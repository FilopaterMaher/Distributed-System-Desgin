# Google Drive System Design Diagram

## Diagram Overview
This diagram shows a partial system design for Google Drive, focusing on core storage and caching components. The visible elements suggest a high-level architecture.

## Identified Components

### 1. Actor
- Represents end users interacting with Google Drive
- Could be web, mobile, or desktop clients

### 2. Server
- Central server handling client requests
- Likely includes API endpoints for file operations

### 3. ObjectStore
- Primary persistent storage for files and binary data
- Probably distributed across multiple servers/data centers
- May use technologies like Colossus (Google's distributed file system)

### 4. CACHE
- Performance optimization layer
- Stores frequently accessed files and metadata
- Reduces load on ObjectStore

### 5. Garbage Collection
- System for cleaning up deleted files
- May implement soft-delete before permanent removal
- Handles storage reclamation

### 6. Cache MetaData
- Stores information about cached items
- Tracks cache validity, expiration, and relationships
- Helps manage cache consistency

