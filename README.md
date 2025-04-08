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
This project demonstrates how to build a real-time analytics pipeline to monitor engagement metrics—such as views, likes, comments, and favorites—on YouTube videos from the Data Engineering Zoomcamp 2025 playlist using Apache Kafka and ksqlDB.

We first create a stream to capture raw video data:
```bash
CREATE STREAM youtube_videos (video_id VARCHAR KEY,title VARCHAR,likes INTEGER,comments INTEGER,views INTEGER,favorites INTEGER,thumbnail VARCHAR) WITH (KAFKA_TOPIC = 'youtube_videos',PARTITIONS = 1,VALUE_FORMAT = 'JSON');
```
```bash
SELECT * from youtube_videos;
```
We can now view the ingested information in real-time:
<img src="https://github.com/Yaxin12/Real-Time-YouTube-Analytics-Pipeline-Data-Engineering-Zoomcamp-2025-Project-/blob/main/image/2.png" width="600"/>

Next, we create a ksqlDB table that tracks the change in likes, comments, views, and favorites over time for each video:
```bash
CREATE TABLE youtube_analytics_changes WITH(KAFKA_TOPIC='youtube_analytics_changes') AS SELECT video_id, latest_by_offset(title) as title, latest_by_offset(comments,2)[1] as comments_prev, latest_by_offset(comments,2)[2] as comments_curr, latest_by_offset(likes,2)[1] as likes_prev, latest_by_offset(likes,2)[2] as likes_curr, latest_by_offset(views,2)[1] as views_prev, latest_by_offset(views,2)[2] as views_curr, latest_by_offset(favorites,2)[1] as favorites_prev, latest_by_offset(favorites,2)[2] as favorites_curr FROM youtube_videos GROUP BY video_id EMIT CHANGES;
```
This enables continuous monitoring of how engagement metrics evolve:

<img src="https://github.com/Yaxin12/Real-Time-YouTube-Analytics-Pipeline-Data-Engineering-Zoomcamp-2025-Project-/blob/main/image/4.png" width="600"/>

As an example, we tracked the video [Data Engineering Zoomcamp 2025 Office Hours (Kestra)](https://www.youtube.com/watch?v=aBQulSpOgfY&t=574s). At first, the video had 67 likes. The information was also reflected in the Kafka stream and shown in the Confluent Platform.


> ⚠️ **Note**: For testing purposes, I temporarily hit the "unlike" button—strictly for science, I swear! 😅 I promise I'll hit "like" again, because this course absolutely deserves it. It's genuinely great and totally worth a thumbs-up! 👍


<table> <tr> <td><img src="https://github.com/Yaxin12/Real-Time-YouTube-Analytics-Pipeline-Data-Engineering-Zoomcamp-2025-Project-/blob/main/image/5.png" width="100%"/></td> <td><img src="https://github.com/Yaxin12/Real-Time-YouTube-Analytics-Pipeline-Data-Engineering-Zoomcamp-2025-Project-/blob/main/image/6.png" width="100%"/></td> </tr> </table>
Then, I clicked the like button again✅—and as expected, the like count updated in real-time:

<table> <tr> <td><img src="https://github.com/Yaxin12/Real-Time-YouTube-Analytics-Pipeline-Data-Engineering-Zoomcamp-2025-Project-/blob/main/image/7.png" width="100%"/></td> <td><img src="https://github.com/Yaxin12/Real-Time-YouTube-Analytics-Pipeline-Data-Engineering-Zoomcamp-2025-Project-/blob/main/image/8.png" width="100%"/></td> </tr> </table>

---

## 📂 Folder Structure
```bash
├── docker-compose.yml        # Setup Kafka ecosystem
├── YoutubeAnalytics.py       # Fetch YouTube video data
├── config/                   # API keys and secrets
└── README.md                 # Project documentation
```

## 🔮 Future Work
While this pipeline successfully demonstrates real-time monitoring of YouTube video engagement, there are several opportunities to improve its usability, scalability, and interactivity:

🔌 1. Integrate with External Systems via Kafka Connect
Currently, the data stays within the Kafka ecosystem, which limits its accessibility for broader analytics or dashboarding. In future iterations, I plan to integrate Kafka Connect to stream data into external systems such as:

 - PostgreSQL or BigQuery for advanced analytics and storage

 - Elasticsearch for full-text search and visualizations via Kibana

 - Data warehouses or BI tools for business-facing reporting

 - This will make the pipeline more extensible and easier to integrate into enterprise environments.

📲 2. Real-Time Notifications with Telegram
To enhance interactivity and responsiveness, I plan to implement real-time alerts via Telegram. This will allow users to receive instant updates on key metrics (e.g., sudden spikes in views or likes, trending videos, or unusual comment activity) directly on their mobile devices.

 This feature will be particularly useful for:

 - Content creators monitoring their own videos

 - Marketing teams tracking campaign performance

 - Educators or students following engagement on course-related playlists