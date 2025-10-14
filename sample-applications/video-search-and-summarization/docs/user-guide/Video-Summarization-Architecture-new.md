# Video Summarization Architecture

## Simple Architecture Overview

Video Summarization transforms long videos into concise, intelligent summaries using AI models that run locally on Intel® hardware.

![System Architecture Diagram](./images/TEAI_VideoSumm.png)

## Core Processing Flow

```
Video Upload → Video Processing → AI Analysis → Summary Generation → Results
     ↓              ↓               ↓              ↓            ↓
  Store in       Chunk &         Caption        Combine       Text Summary
  MinIO         Extract          Frames         Captions      + Timestamps
```

## Key Components

### 📹 **Video Processing Pipeline**
![Technical Architecture Diagram](./images/TEAI_VideoSumm_Arch.png)

- **Video Ingestion**: Processes videos, creates chunks, extracts key frames
- **Audio Transcription**: Converts speech to text using Whisper models
- **Object Detection**: Identifies people, objects, and activities (optional)

### 🤖 **AI Analysis Services**
- **VLM Service**: Creates captions for video frames using Vision Language Models
- **LLM Service**: Combines captions into coherent summaries
- **Pipeline Manager**: Orchestrates the entire summarization process

### 💾 **Storage & Interface**
- **Object Storage (MinIO)**: Stores videos, frames, and generated content
- **Web UI**: User-friendly interface for configuration and results

## Data Flow Process

![Data flow diagram](./images/VideoSummary-request.jpg)

### Step-by-Step Process

1. **📤 Upload & Configure**
   - Upload video through web interface
   - Choose summarization features (object detection, audio transcription)
   - Set chunk duration and frame extraction settings

2. **🔧 Video Processing**
   - Split video into manageable chunks
   - Extract representative frames from each chunk
   - Separate audio track for transcription

3. **👁️ AI Analysis**
   - **Vision Analysis**: VLM creates captions for each frame
   - **Audio Analysis**: Whisper transcribes speech content
   - **Object Detection**: Identifies key elements (if enabled)

4. **📝 Summary Creation**
   - LLM combines all captions into coherent summary
   - Adds timestamps and key event markers
   - Incorporates audio transcription insights

5. **📊 Results Delivery**
   - Present structured summary with timestamps
   - Show processing progress in real-time
   - Store results for future reference

## Configuration Options

### 🎛️ **Pipeline Modes**

Choose your balance of speed vs. detail:

```
Basic Mode:     Fast processing → Good summaries
Enhanced Mode:  + Object detection → Better context  
Advanced Mode:  + Audio transcription → Rich insights
Custom Mode:    Mix and match features → Tailored results
```

### ⚙️ **Key Settings**
- **Chunk Duration**: How long each video segment should be (30s - 5min)
- **Frame Extraction**: How many frames to analyze per chunk
- **Object Detection**: Enable/disable visual element identification
- **Audio Processing**: Include/exclude speech transcription

## Microservices Breakdown

| Service | Purpose | Technology |
|---------|---------|------------|
| **Web UI** | User interface and configuration | React + REST APIs |
| **Pipeline Manager** | Orchestrates entire process | Python + Message Queue |
| **Video Ingestion** | Process and chunk videos | DLStreamer + OpenVINO |
| **VLM Service** | Generate frame captions | Vision Language Models |
| **LLM Service** | Create final summaries | Large Language Models |
| **Audio Transcription** | Convert speech to text | Whisper + OpenVINO |
| **Object Storage** | Store videos and results | MinIO (S3-compatible) |

## Customization Points

### 🔄 **Easy to Replace**
- **Models**: Use different VLM, LLM, or Whisper models
- **Capabilities**: Add custom analysis features
- **Storage**: Switch to different object stores
- **Interface**: Build custom UIs using REST APIs

### 📈 **Scalability Options**
- **Single Node**: Docker Compose for development
- **Multi-Node**: Kubernetes for production scale
- **Hardware**: Optimize for CPU, GPU, or NPU

## Benefits

- ⏰ **Time Savings**: Hours of video → Minutes of reading
- 🔒 **Data Privacy**: All processing on your hardware
- 🎯 **Smart Analysis**: Multi-modal understanding (vision + audio + text)
- ⚡ **Real-Time Updates**: See progress as processing happens
- 🔧 **Flexible**: Configure features based on your needs
- 📊 **Structured Output**: Timestamped summaries with key insights

## Use Cases

| Scenario | Configuration | Output |
|----------|---------------|---------|
| **Meeting Records** | Audio transcription + basic video | Action items + key decisions |
| **Security Footage** | Object detection + basic processing | Event timeline + incidents |
| **Training Videos** | Enhanced mode with all features | Learning objectives + key concepts |
| **Media Content** | Custom based on content type | Episode summaries + highlights |

Perfect for meetings, security footage, training content, and any scenario where you need to quickly understand long-form video content.

**Next Steps**: [Get Started](./get-started.md) | [System Requirements](./system-requirements.md)