# Combined Search and Summarization Architecture

## Simple Architecture Overview

The combined mode brings together video summarization and search into a unified pipeline that processes videos once and enables both intelligent summaries and fast search capabilities.

![System Architecture Diagram](./images/TEAI_VideoSearchSumm.png)

## How Combined Mode Works

```
Video Upload → AI Processing → Dual Output → Unified Search
     ↓             ↓             ↓           ↓
  Store in     Generate        Store        Search Both
  MinIO       Summary +       Summary +    Summary &
             Embeddings      Embeddings    Video Content
```

## Core Processing Flow

### 📤 **Single Upload, Dual Benefits**
![Technical Architecture Diagram](./images/TEAI_VideoSearchSumm_Arch.png)

1. **Upload Once** → Video stored in MinIO object storage
2. **Process Together** → AI creates both summaries and search embeddings
3. **Search Everything** → Query summaries and video content simultaneously
4. **Unified Results** → Get comprehensive results from both sources

## Key Components

### 🎯 **Central Orchestrator**
- **Pipeline Manager**: Coordinates both summarization and search processes
- **Unified UI**: Single interface for upload, configuration, and search
- **Async Processing**: Handles both workflows simultaneously

### 🤖 **Shared AI Services**
| Service | Summary Role | Search Role |
|---------|-------------|-------------|
| **Video Ingestion** | Extract frames for captioning | Create embeddings from content |
| **VLM Service** | Generate frame captions | Provide visual understanding |
| **LLM Service** | Create final summaries | Process search queries |
| **Audio Transcription** | Add speech to summaries | Enable audio-based search |
| **Embedding Service** | Convert summaries to vectors | Create searchable representations |

### 💾 **Unified Storage**
- **Object Store (MinIO)**: Videos, frames, summaries, and metadata
- **Vector Database (VDMS)**: Search embeddings from both content and summaries

## Data Flow Process

### Step-by-Step Combined Processing

1. **📹 Video Upload & Configuration**
   - Upload video through unified interface
   - Configure both summary and search features
   - Set processing parameters for both pipelines

2. **🔧 Parallel Processing**
   - **Video Analysis**: Extract frames, audio, and metadata
   - **Summary Generation**: Create captions → combine into summary
   - **Search Indexing**: Generate embeddings → store in vector database
   - **Background Tasks**: Both processes run simultaneously

3. **💾 Unified Storage**
   - Store video summaries as searchable text
   - Index both summary and video content embeddings
   - Maintain relationships between summaries and original content

4. **🔍 Enhanced Search**
   - Search across video content embeddings
   - Search through summary text embeddings
   - Combine results for comprehensive answers

## Benefits of Combined Mode

### ⚡ **Efficiency**
- **Process Once**: Single upload serves both use cases
- **Shared Resources**: AI services handle both workflows
- **Unified Storage**: Single database for all content

### 🎯 **Better Results**
- **Comprehensive Search**: Find content in both summaries and raw video
- **Context-Aware**: Summaries provide better search context
- **Faster Discovery**: Search summaries first, then dive into video details

### 💰 **Cost Effective**
- **Resource Sharing**: Same hardware serves both functions
- **Reduced Storage**: Efficient indexing strategy
- **Single Pipeline**: Lower operational complexity

## Configuration Options

### 🎛️ **Unified Settings**

Choose features that benefit both search and summary:

```
Basic Mode:     Summary + basic search capabilities
Enhanced Mode:  + Object detection for richer context
Advanced Mode:  + Audio transcription for complete coverage
Custom Mode:    Mix features based on specific needs
```

### ⚙️ **Key Configuration**
- **Chunk Duration**: Affects both summary quality and search granularity
- **Frame Extraction**: Impacts visual understanding for both workflows
- **Object Detection**: Enhances both summaries and search accuracy
- **Audio Processing**: Adds speech insights to both outputs

## Microservices Architecture

### 🔄 **Shared Services**
```
┌─────────────────────────────────────────────────────────────┐
│                    Combined Pipeline                        │
├─────────────────────┬───────────────────────────────────────┤
│    Summary Path     │           Search Path                 │
├─────────────────────┼───────────────────────────────────────┤
│ Video → VLM →       │ Video → Embedding →                   │
│ LLM → Summary       │ Vector DB → Search                    │
└─────────────────────┴───────────────────────────────────────┘
```

| Service | Combined Function |
|---------|-------------------|
| **Pipeline Manager** | Orchestrates both summary and search workflows |
| **Video Ingestion** | Processes video for both summarization and indexing |
| **VLM Service** | Generates captions for summaries and search understanding |
| **LLM Service** | Creates summaries and processes search queries |
| **Embedding Service** | Creates vectors for both content and summaries |
| **Vector Database** | Stores all embeddings for unified search |

## Use Cases

| Scenario | Combined Benefit |
|----------|------------------|
| **Media Archives** | Summarize content + search for specific scenes |
| **Security Systems** | Daily summaries + instant incident search |
| **Training Content** | Course summaries + search for specific topics |
| **Meeting Records** | Action item summaries + search past decisions |

## Deployment

### 🐳 **Single Deployment**
- Same Docker Compose setup serves both functions
- Unified configuration and management
- Shared resource allocation

### ☸️ **Scalable Architecture**  
- Kubernetes deployment with shared services
- Independent scaling of summary vs. search workloads
- Load balancing across combined functionality

## Key Benefits

- 🚀 **One-Stop Solution**: Upload once, get both summaries and search
- ⚡ **Fast Results**: Search summaries for quick answers, drill down for details
- 🧠 **Smart Integration**: Summaries improve search accuracy and relevance
- 💾 **Efficient Storage**: Shared embeddings reduce storage requirements
- 🔒 **Edge Processing**: All capabilities run locally on Intel® hardware

Perfect for organizations that need both content understanding (summaries) and content discovery (search) from their video collections.

**Next Steps**: [Get Started](./get-started.md) | [System Requirements](./system-requirements.md)