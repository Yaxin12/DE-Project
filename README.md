# 📊 Real-Time YouTube Analytics Pipeline (Data Engineering Zoomcamp 2025 Project)

This project is built as part of the **Data Engineering Zoomcamp 2025**. It implements an end-to-end real-time data pipeline that monitors YouTube activity (views, likes, comments) on a selected video list and streams it through Kafka for processing and analysis.

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
| **Google Cloud Console** | Set up API keys and manage quotas for YouTube API |
| **Confluent Platform** | Kafka management, Control Center, Connectors |

---

## 📌 Features

- ✅ Real-time ingestion of YouTube video stats using Python
- ✅ Kafka ecosystem setup via Docker Compose (Zookeeper, Kafka, Schema Registry, ksqlDB, Control Center)
- ✅ Stream processing using ksqlDB (custom queries and filtering)
- ✅ Modular and extensible design to connect with external systems

---

## 📈 Use Case

I applied this pipeline to **analyze the video list from the [Data Engineering Zoomcamp 2025]**, enabling near real-time insights into audience interaction.

---

## 📂 Folder Structure

├── docker-compose.yml # Setup Kafka ecosystem ├── youtube_fetcher.py # Fetch YouTube video data ├── kafka_producer.py # Push data to Kafka topic ├── ksql/ # ksqlDB queries for stream processing ├── config/ # API keys and secrets └── README.md # Project documentation