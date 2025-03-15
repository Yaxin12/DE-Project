# DE-Project
This is my project of DE.
## Goal
Build an end-to-end data pipeline

## Problem statement
- [ ] Selecting a dataset of interest
- [ ] Creating a pipeline for processing this dataset and putting it to a datalake
- [ ] Creating a pipeline for moving the data from the lake to a data warehouse
- [ ] Transforming the data in the data warehouse: prepare it for the dashboard
- [ ] Building a dashboard to visualize the data

## Data Pipeline
* **Batch:**   run things periodically (hourly/daily)

## Technologies
I plan to use those tools:
* **Cloud:**  GCP
* **Infrastructure as code (IaC):**  Terraform
* **Workflow orchestration:**  Airflow
* **Data Warehouse:**  BigQuery
* **Batch processing:** Spark

## Dashboard

## Evaluation Criteria

- [ ] Problem description

- [ ]  Cloud
    * 2 points: The project is developed in the cloud
    * 4 points: The project is developed in the cloud and IaC tools are used

- [ ] Data ingestion
    * Batch / Workflow orchestration
        * 2 points: Partial workflow orchestration: some steps are orchestrated, some run manually
        * 4 points: End-to-end pipeline: multiple steps in the DAG, uploading data to data lake

- [ ] Data warehouse
    * 2 points: Tables are created in DWH, but not optimized
    * 4 points: Tables are partitioned and clustered in a way that makes sense for the upstream queries (with explanation)

- [ ] Transformations (dbt, spark, etc)
    * 2 points: Simple SQL transformation (no dbt or similar tools)
    * 4 points: Tranformations are defined with dbt, Spark or similar technologies

- [ ] Dashboard 
    * 2 points: A dashboard with 1 tile
    * 4 points: A dashboard with 2 tiles

- [ ] Reproducibility
    * 2 points: Some instructions are there, but they are not complete
    * 4 points: Instructions are clear, it's easy to run the code, and the code works

## Helpful Links
* [Unit Tests + CI for Airflow](https://www.astronomer.io/events/recaps/testing-airflow-to-bulletproof-your-code/)
* [CI/CD for Airflow (with Gitlab & GCP state file)](https://engineering.ripple.com/building-ci-cd-with-airflow-gitlab-and-terraform-in-gcp)
* [CD for Terraform](https://towardsdatascience.com/git-actions-terraform-for-data-engineers-scientists-gcp-aws-azure-448dc7c60fcc)
* [Spark + Airflow](https://medium.com/doubtnut/github-actions-airflow-for-automating-your-spark-pipeline-c9dff32686b)


Go! Make some cool stuff!!!