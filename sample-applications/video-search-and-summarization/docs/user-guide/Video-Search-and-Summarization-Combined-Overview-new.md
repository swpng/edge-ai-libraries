# Combined Search and Summarization

## What Is Combined Mode?

Get the best of both worlds: AI creates smart video summaries, then enables lightning-fast search through those summaries instead of raw video files.

![Video Summary web interface](./images/VideoSearch_Summary_Webpage.png)

## How It Works

**Smart Two-Step Process:**

1. **📝 Summarize First** → AI analyzes videos and creates intelligent summaries
2. **🔍 Search Summaries** → Find content by searching through compact summaries

```
Video → AI Summarization → Text Embeddings → Fast Search → Relevant Results
  ↓            ↓               ↓              ↓           ↓
Upload      Extract Key     Create Index    Query      Video Clips
Videos      Information     for Search      Summary    + Timestamps
```

## Why This Is Better

**Traditional Problems:**
- ❌ Slow search through entire video files
- ❌ Inconsistent and irrelevant results  
- ❌ High storage and compute costs

**Combined Mode Solutions:**
- ✅ **10x Faster**: Search compact summaries, not full videos
- ✅ **More Accurate**: Summaries contain only relevant information
- ✅ **Cost Effective**: Less storage and processing needed
- ✅ **Smarter Results**: Fewer false matches and hallucinations

## Real-World Example

```
Input:  "2-hour security footage from lobby camera"
Step 1: AI Summary → "Person entered at 14:30, delivery at 15:45, 
                     maintenance work 16:20-16:35"
Step 2: Search Query → "maintenance work"
Result: Direct link to 16:20-16:35 video segment
```

## Key Benefits

| Benefit | Description |
|---------|-------------|
| **⚡ Speed** | Search text summaries instead of processing video frames |
| **🎯 Accuracy** | Summaries focus on key events, reducing noise |
| **💰 Efficiency** | Lower storage and compute requirements |
| **🔄 Unified** | Single pipeline handles both summarization and search |
| **📈 Scalable** | Works with thousands of videos and frequent queries |

## Perfect For

- **Large Video Libraries**: News archives, security footage, training content
- **Regular Analysis**: Daily meetings, surveillance review, content moderation  
- **Quick Insights**: When you need fast answers from video content
- **Resource Constraints**: When compute and storage are limited

## Architecture Overview

![System Architecture Diagram](./images/TEAI_VideoSearchSumm.png)

**Microservices Working Together:**
- **Video Ingestion** → Processes and stores videos
- **Summarization Service** → Creates intelligent summaries
- **Embedding Service** → Converts summaries to searchable format
- **Search Backend** → Handles queries and ranking
- **Web Interface** → User-friendly search and results

## Getting Started

### Quick Setup
1. **Deploy** the combined pipeline ([Setup Guide](./get-started.md))
2. **Upload** your video collection
3. **Configure** summary detail level and chunk size
4. **Wait** for AI processing (progress updates provided)
5. **Search** using natural language queries

### Key Configuration

Choose your balance of speed vs. accuracy:

```
Fast Mode:     Basic summaries → Quick processing
Balanced Mode: Good summaries → Moderate processing  
Detailed Mode: Rich summaries → Thorough processing
```

## Use Cases

| Industry | Application |
|----------|-------------|
| **Security** | Search incidents across surveillance archives |
| **Media** | Find scenes in large video libraries |
| **Education** | Locate topics in course recordings |
| **Legal** | Search evidence in recorded proceedings |
| **Corporate** | Find decisions in meeting recordings |

## Benefits Summary

- 🚀 **Fast Search**: Text-based search is 10x faster than video analysis
- 🧠 **Smart Results**: AI summaries capture key information accurately  
- 💾 **Efficient Storage**: Index summaries, not full video embeddings
- 🔒 **Edge Processing**: Keep your data private on Intel® hardware
- 🔗 **Easy Integration**: REST APIs for custom applications

Transform your video archives into a fast, searchable knowledge base.

**Next Steps**: [Get Started](./get-started.md) | [System Requirements](./system-requirements.md)