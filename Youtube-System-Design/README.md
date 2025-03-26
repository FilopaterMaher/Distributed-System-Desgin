# YouTube System Design Diagram

## Diagram Overview
This diagram outlines key components of YouTube's video streaming architecture, focusing on video processing, storage, and delivery.

## Identified Components

### 1. Actor
- Represents end users watching videos or content creators uploading content
- Could be web browsers, mobile apps, or embedded players

### 2. Server
- Application servers handling HTTP requests
- Manages API endpoints for:
  - Video uploads
  - Stream requests
  - User interactions (likes, comments)
  - Recommendations

### 3. ObjectStore (raw)
- Stores original uploaded videos before processing
- Characteristics:
  - High durability storage
  - Handles large binary files
  - Likely uses distributed file system (e.g., Google Colossus)

### 4. Queue
- Message queue for asynchronous processing
- Handles:
  - Video encoding jobs
  - Thumbnail generation
  - Metadata extraction
  - Notification events
- Possible technologies: Pub/Sub, Kafka, RabbitMQ

### 5. CDN (Content Delivery Network)
- Global edge cache for video streams
- Key functions:
  - Distributes encoded video chunks worldwide
  - Reduces latency through edge locations
  - Handles adaptive bitrate switching
- Likely uses Google's global CDN infrastructure

### 6. NoSQL Database
- Stores:
  - Video metadata (title, description, tags)
  - User data (profiles, preferences)
  - Engagement metrics (views, likes)
- Possible choices: Bigtable, Spanner, or Firestore

### 7. Metadata
- Management system for:
  - Video information
  - User relationships
  - Search indexes
  - Recommendations data
- May include both relational and graph data

### 8. Cache
- Performance optimization layer for:
  - Frequently accessed videos
  - User sessions
  - Recommendations
  - Trending content
- Likely multi-level caching (memory, SSD)

### 9. Encoding
- Video processing subsystem:
  - Transcodes raw uploads into multiple formats
  - Generates adaptive bitrate versions
  - Creates thumbnails and previews
  - May use machine learning for enhancements

### 10. ObjectStore (Encoded)
- Stores processed video files:
  - Multiple resolutions (144p to 8K)
  - Different codecs (VP9, AV1, H.264)
  - Audio tracks and subtitles
- Optimized for sequential reads
