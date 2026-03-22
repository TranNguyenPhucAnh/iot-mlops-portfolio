# IoT MLOps Platform

End-to-end IoT MLOps platform: edge data collection, data lake pipelines (bronze–silver–gold), model training & inference, and fully automated AWS infrastructure & Kubernetes deployment.

## High-level Architecture

- Edge device collects sensor data and ships logs/metrics to the cloud.
- AWS backbone provisioned via Terraform (networking, EKS, RDS, observability, CI/CD).
- Workloads deployed to Kubernetes using ArgoCD and GitOps manifests.
- Airflow orchestrates data pipelines and ML workflows (training & inference).
- ML experiment tracking and model registry handled by MLflow.

## Repositories

- **Infrastructure as Code – Terraform**  
  [`iot-mlops-terraform`](https://github.com/TranNguyenPhucAnh/iot-mlops-terraform)  
  Provision AWS networking, EKS cluster, RDS, Grafana/Prometheus, MLflow, Airflow, ArgoCD, and supporting services using Terraform modules.

- **Kubernetes & GitOps Manifests**  
  [`iot-mlops-manifests`](https://github.com/TranNguyenPhucAnh/iot-mlops-manifests)  
  ArgoCD applications and Kubernetes manifests for Airflow, MLflow, Grafana, Jenkins, and application workloads (including image updater automation).

- **Edge Compute Agent**  
  [`iot-mlops-edge-compute`](https://github.com/TranNguyenPhucAnh/iot-mlops-edge-compute)  
  Python-based edge collector with Docker image, logging (Fluent Bit), tracing (OpenTelemetry), and Ansible deployment configs for edge nodes.

- **Data & ML Pipelines (Airflow DAGs)**  
  [`iot-mlops-python-dag`](https://github.com/TranNguyenPhucAnh/iot-mlops-python-dag)  
  Airflow DAGs for IoT data ingestion (bronze/silver), feature engineering, model training, batch/online inference pipelines, and AWS Lambda integration.

## How to Explore

1. Start with [`iot-mlops-terraform`](https://github.com/TranNguyenPhucAnh/iot-mlops-terraform) to see how the AWS & EKS foundation is provisioned.
2. Look at [`iot-mlops-manifests`](https://github.com/TranNguyenPhucAnh/iot-mlops-manifests) to understand the GitOps/Kubernetes deployment model.
3. Review [`iot-mlops-python-dag`](https://github.com/TranNguyenPhucAnh/iot-mlops-python-dag) for data & ML workflows.
4. Check [`iot-mlops-edge-compute`](https://github.com/TranNguyenPhucAnh/iot-mlops-edge-compute) for the edge data collection story.

## Tech Stack Highlights

- AWS: EKS, RDS, IAM, networking, monitoring.
- IaC: Terraform modules.
- Orchestration: Kubernetes, ArgoCD (GitOps).
- Pipelines: Apache Airflow, AWS Lambda.
- ML: MLflow, Python-based feature engineering & training code.
- Observability: Grafana, Prometheus, Fluent Bit, OpenTelemetry.
- CI/CD: Jenkins for building and deploying images & pipelines.
