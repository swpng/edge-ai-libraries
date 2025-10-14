# Video Search Architecture

## Simple Architecture Overview

Video Search uses a microservices architecture that processes videos locally on Intel® hardware, creating searchable indexes for fast natural language queries.

![System Architecture Diagram](./images/TEAI_VideoSearch.png)

## Core Components

### 🎬 **Video Processing**
```
Video Upload → Feature Extraction → Vector Storage → Search Ready
```

- **Video Ingestion**: Processes common video formats and stores in MinIO
- **Embedding Service**: Converts videos to searchable representations using CLIP
- **Vector Database (VDMS)**: Stores embeddings for fast similarity search

### 🔍 **Search Pipeline**
```
User Query → Query Embedding → Vector Search → Ranked Results
```

- **Search Backend**: Handles queries using LangChain framework
- **Embedding Inference**: Creates query embeddings using OpenVINO models
- **Web UI**: User-friendly interface for search and results

## Data Flow

### 📤 **Video Ingestion Process**
![Technical Architecture Diagram of video ingestion](./images/TEAI_VideoSearch_Arch-ingest.png)

1. **Upload Videos** → Store in MinIO object storage
2. **Extract Features** → Create embeddings from visual and audio content
3. **Index Content** → Store embeddings in VDMS vector database
4. **Ready for Search** → Videos now searchable via natural language

### 🔎 **Search Query Process**
![Technical Architecture Diagram of video query](./images/TEAI_VideoSearch_Arch-query.png)

1. **User Query** → "Find people entering the building"
2. **Create Embedding** → Convert query to vector representation
3. **Search Database** → Find matching video segments
4. **Return Results** → Relevant clips with timestamps

### 📊 **Complete Request Flow**
![Data flow figure](./images/VideoSearch-request.png)

## Key Features

### 🏠 **Edge Deployment**
- **Local Processing**: All AI runs on Intel® hardware
- **Data Privacy**: Videos never leave your infrastructure
- **Low Latency**: No cloud roundtrips required

### 🔧 **Modular Design**
- **Swappable Components**: Change models, databases, or interfaces
- **Standard APIs**: OpenAI-compatible endpoints
- **Scalable**: Add more processing power as needed

### 🤖 **Background Processing**
- **Continuous Monitoring**: Set up to 8 background queries
- **Auto-Detection**: Get notified when events match your queries
- **Agentic Reasoning**: Handle complex, multi-step analysis

## Microservices Breakdown

| Service | Purpose | Technology |
|---------|---------|------------|
| **Web UI** | User interface for search | React + REST APIs |
| **Search Backend** | Query processing and orchestration | LangChain + Python |
| **Video Ingestion** | Process and store videos | OpenVINO + MinIO |
| **Embedding Service** | Convert content to vectors | CLIP + OpenVINO |
| **Vector Database** | Store and search embeddings | VDMS |
| **Object Storage** | Store original videos | MinIO (S3-compatible) |

## Deployment Options

### 🐳 **Single Node (Docker Compose)**
Perfect for development and small deployments:
```
All services on one machine
Simple setup with docker-compose up
Good for testing and proof-of-concepts
```

### ☸️ **Multi-Node (Kubernetes)**
For production and scale:
```
Services distributed across multiple nodes
Better performance and reliability
Supports large video collections
```

## Customization Points

### 🔄 **Easy to Replace**
- **Models**: Use different embedding or VLM models
- **Storage**: Switch from VDMS to other vector databases
- **Inference**: Replace OpenVINO with other model servers
- **UI**: Build custom interfaces using REST APIs

### ⚙️ **Configuration Options**
- **Video Quality**: Adjust processing vs. accuracy tradeoffs
- **Search Parameters**: Tune result ranking and filtering  
- **Background Queries**: Set up automatic event detection
- **Hardware**: Optimize for CPU, GPU, or NPU

## Benefits

- ⚡ **Fast Setup**: Deploy with docker-compose in minutes
- 🔒 **Secure**: All processing happens on your hardware
- 🎯 **Accurate**: AI models optimized for Intel® hardware
- 📈 **Scalable**: From single videos to enterprise collections
- 🔧 **Flexible**: Customize components for your specific needs

Perfect for security footage analysis, media archives, training content, and any scenario requiring intelligent video search.

**Next Steps**: [Get Started](./get-started.md) | [System Requirements](./system-requirements.md)