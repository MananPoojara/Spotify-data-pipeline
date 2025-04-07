# 🎧 Spotify Data Pipeline using AWS

This project demonstrates a serverless **ETL data pipeline** built with **AWS services** to extract music data from the Spotify API, transform it using AWS Lambda, and analyze it with **Amazon Athena**.

<br/>

## 📊 Architecture

![Spotify Data Pipeline](./Capture.PNG)

---

## 🧰 Tech Stack

- **AWS Lambda** – For serverless data extraction and transformation.
- **Amazon S3** – Storage for raw and transformed data.
- **Amazon CloudWatch** – Scheduled trigger for daily extraction.
- **AWS Glue** – Crawlers and Data Catalog for schema inference.
- **Amazon Athena** – SQL-based querying and analytics.
- **Spotify API** – Data source.
- **Python** – For scripting the pipeline logic.

---

## ⚙️ Workflow Breakdown

### 🔍 Extract

- **Trigger**: Amazon CloudWatch runs daily.
- **AWS Lambda** (Extraction):
  - Calls the Spotify API using a Python script.
  - Fetches data (e.g., top tracks, artists, playlists).
  - Stores raw JSON data into **Amazon S3** (raw data bucket).

### 🔄 Transform

- An **S3 trigger** invokes another **AWS Lambda** function when new raw data is uploaded.
- The transformation Lambda:
  - Cleans and formats the raw data.
  - Saves transformed data into a separate **Amazon S3** bucket.

### 🚀 Load

- **AWS Glue Crawler** scans the transformed data and infers the schema.
- **AWS Glue Data Catalog** stores the metadata for Athena.
- **Amazon Athena** can now run SQL queries over the data for analytics.

---

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/yourusername/spotify-data-pipeline.git
cd spotify-data-pipeline
