# 📊 Real-Time YouTube Analytics Pipeline (Data Engineering Zoomcamp 2025 Project)

<div align="center">

  <a href="https://www.youtube.com/watch?v=X8cEEwi8DTM&list=PL3MmuxUbc_hJZdpLpRHp7dg6EOx828q6y" title="Video Title">
    <img src="https://i.ytimg.com/vi/X8cEEwi8DTM/hqdefault.jpg?sqp=-oaymwEXCOADEI4CSFryq4qpAwkIARUAAIhCGAE=&rs=AOn4CLCHMXvedNHuTfWxeUXhRUVacYUG3g" alt="IMAGE ALT TEXT" />
  </a>

</div>


This project implements an end-to-end real-time data pipeline that monitors YouTube video activity—such as views, likes, and comments—for [Data Engineering Zoomcamp 2025](https://www.youtube.com/watch?v=X8cEEwi8DTM&list=PL3MmuxUbc_hJZdpLpRHp7dg6EOx828q6y) playlist. The data is streamed using Apache Kafka, enabling real-time processing and analytics.

> ⚠️ **Note**: Telegram bot integration is currently not functional and will be addressed in future work.

---

## 🚀 Project Overview

This pipeline fetches video analytics from the YouTube API, streams it into Kafka topics, processes it with ksqlDB, and enables extensible integrations with external systems. The goal is to demonstrate real-time analytics capability using industry-grade tools and infrastructure.

---

## 🛠 Technologies & Tools Used

| Tool/Tech | Purpose |
|-----------|---------|
| **Python** | Fetch data from YouTube API and push to Kafka |
| **YouTube Data API v3** | Access video statistics and metadata |
| **Docker + Docker Compose** | Containerize the full Kafka ecosystem |
| **Apache Kafka** | Real-time messaging and data streaming |
| **Kafka Connect** | External system integration (e.g., Telegram, future DB) |
| **ksqlDB** | Real-time stream processing using SQL-like syntax |
| **Google Cloud Platform** | Set up API keys and manage quotas for YouTube API |
| **Confluent Platform** | Kafka management, Control Center, Connectors |

---

## 📌 Features

- ✅ Real-time ingestion of YouTube video stats using Python
- ✅ Kafka ecosystem setup via Docker Compose (Zookeeper, Kafka, Schema Registry, ksqlDB, Control Center)
- ✅ Stream processing using ksqlDB (custom queries and filtering)
- ✅ Modular and extensible design to connect with external systems

---

## 📈 Use Case

```bash
CREATE STREAM youtube_videos (
  video_id VARCHAR KEY,
  title VARCHAR,
  likes INTEGER,
  comments INTEGER,
  views INTEGER,
  favorites INTEGER,
  thumbnail VARCHAR
) WITH (
  KAFKA_TOPIC = 'youtube_videos',
  PARTITIONS = 1,
  VALUE_FORMAT = 'JSON'
);

SELECT * from youtube_videos;
```
Creat a stream, and let's take a look.
[Information of Playlist](https://github.com/Yaxin12/Real-Time-YouTube-Analytics-Pipeline-Data-Engineering-Zoomcamp-2025-Project-/blob/main/image/2.png)
---

## 📂 Folder Structure
```bash
├── docker-compose.yml        # Setup Kafka ecosystem
├── YoutubeAnalytics.py       # Fetch YouTube video data
├── config/                   # API keys and secrets
└── README.md                 # Project documentation
```

## 🔮 Future Work
❌ Telegram Integration: Although initial steps were implemented (Telegram Bot setup), real-time alerts for significant YouTube events are not functional yet due to integration issues. This remains a priority for future development.

🔌 Integration with databases such as PostgreSQL or BigQuery

📊 Visualization dashboards using tools like Grafana or Looker Studio
