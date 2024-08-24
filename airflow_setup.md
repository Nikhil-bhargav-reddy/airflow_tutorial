
# Setting Up Apache Airflow Locally Using Docker

This guide will help you set up Apache Airflow using Docker on your local machine. Follow these steps to get up and running.

## Prerequisites

- **Docker Desktop**: Make sure Docker Desktop is installed on your machine. You can download it [here](https://www.docker.com/products/docker-desktop).
- **Docker Compose**: Check that Docker Compose is installed by running:

  ```bash
  docker-compose --version
  ```

## Setup Instructions

### 1. Prepare Your Environment

1. **Create a Directory for Airflow**

   Create a new directory where you will store your Airflow configurations and data. For example:

   ```bash
   mkdir -p ~/airflow
   cd ~/airflow
   ```

2. **Download the Docker Compose File**

   Download the `docker-compose.yaml` file for Airflow. This file contains the configuration for the Airflow services:

   ```bash
   curl -LfO 'https://airflow.apache.org/docs/apache-airflow/2.10.0/docker-compose.yaml'
   ```

   You can replace `2.10.0` with the desired Airflow version. If you do not specify a version, Docker will pull the latest image.

### 2. Configure Directories

1. **Create Required Folders**

   Create the necessary directories for Airflow:

   ```bash
   mkdir dags logs plugins
   ```

   - `dags`: Place your Airflow DAGs (Directed Acyclic Graphs) here.
   - `logs`: Airflow logs will be stored here.
   - `plugins`: Place any Airflow plugins here.

### 3. Initialize Airflow

1. **Initialize the Airflow Database**

   Run the following command to initialize the Airflow database:

   ```bash
   docker-compose up airflow init
   ```

   This step may take a few minutes. You can ignore any warnings that appear.

2. **Start Airflow**

   Once initialization is complete, start the Airflow services:

   ```bash
   docker-compose up
   ```

### 4. Verify the Setup

1. **Check Running Containers**

   Verify that the containers are up and running by executing:

   ```bash
   docker ps
   ```

   Ensure that the containers are healthy and running.

2. **Access Airflow Web Interface**

   Open your web browser and navigate to [http://localhost:8080](http://localhost:8080). You should see the Airflow web interface.

   - **Default Credentials**: 
     - **Username**: `airflow`
     - **Password**: `airflow`

   You can change the default credentials and other configurations in the `docker-compose.yaml` file.

### 5. Deploy Your DAGs

Place your DAG files in the `dags` folder. By default, Airflow will check for new DAGs every 30 seconds. This interval can be adjusted in the `docker-compose.yaml` file if needed.

## Additional Configuration

- **Configuration File**: The `docker-compose.yaml` file includes configurations for refresh frequency, retries, server URL, and DAG namespaces. Review this file to customize your setup according to your needs.

## Troubleshooting

- **Logs**: If you encounter issues, check the logs for detailed error messages:

  ```bash
  docker-compose logs
  ```

- **Port Conflicts**: Ensure that port `8080` is not being used by another application on your machine.

## Resources

- [Apache Airflow Documentation](https://airflow.apache.org/docs/apache-airflow/stable/)
- [Docker Documentation](https://docs.docker.com/)
- [Docker Compose Documentation](https://docs.docker.com/compose/)

Feel free to open issues or contribute to this documentation if you find any errors or have suggestions for improvements.
```
