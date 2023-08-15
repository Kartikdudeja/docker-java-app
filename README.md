# Multi-Tier Dockerized Java Application

This repository contains a multi-tier Dockerized Java application that showcases the deployment of a multi-tier architecture using Docker containers. The application consists of multiple interconnected components, each running in its own Docker container, to demonstrate the separation of concerns and scalability in a distributed system.

## Prerequisites

Before you start, ensure that you have the following prerequisites installed on your system:

- Docker: [Install Docker](https://docs.docker.com/get-docker/)

## Architecture

The multi-tier Java application consists of the following components:

1. **Frontend**: A web-based frontend that provides a user interface for interacting with the application. It communicates with the backend services.
2. **Backend**: A backend service responsible for processing user requests and interacting with the database.
3. **Database**: A database service that stores and retrieves data for the application.

The communication flow is as follows: User interacts with the frontend, which in turn communicates with the backend, which finally interacts with the database.

## Getting Started

1. Clone this repository:

   ```bash
   git clone https://github.com/Kartikdudeja/docker-java-app.git
   ```

2. Navigate to the project directory:

   ```bash
   cd docker-java-app
   ```

3. Build the Docker images for each component:

   ```bash
   docker-compose build
   ```

4. Run the Docker containers:

   ```bash
   docker-compose up -d
   ```

   This starts the database container, memcache container and mq container, then the app container linked to the database, and finally the web container linked to the app.

5. Access the application:

   Open your web browser and navigate to `http://localhost:8080` to interact with the frontend of the multi-tier application.

## Project Structure

The project's directory structure is organized as follows:

```
docker-java-app/
├── web/
│   ├── Dockerfile
│   └── vproapp.conf
├── app/
│   ├── Dockerfile
│   ├── application.properties
│   └── target/
|        └── vprofile-v2.war
├── db/
│   ├── Dockerfile
│   └── db_backup.sql
├── docker-compose.yml
└── README.md
```

- `web/`, `app/`, `db/`: These directories contain the Dockerfiles, configuration file and source code for the frontend, backend, and database components respectively.

## Contributions

Contributions are appreciated! If you encounter any issues or have suggestions for improvements, please submit a pull request or open an issue.

## Acknowledgements

I want to express my gratitude to the open-source community for providing the tools and libraries that made this multi-tier web app possible.
