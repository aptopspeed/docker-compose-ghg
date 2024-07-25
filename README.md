# docker-compose-ghg

# Docker Compose Setup for Project Demo Emissions

This repository contains a Docker Compose configuration to run both the frontend and backend of our application. Follow these instructions to get started.

## Prerequisites

- Docker installed on your machine
- Docker Compose installed on your machine

## Getting Started

1. Clone this repository to your local machine:
   ```
   git clone https://github.com/aptopspeed/docker-compose-ghg.git
   cd docker-compose-ghg
   ```

2. Make sure you have a `docker-compose.yml` file in the root of your project. It should define both your frontend and backend services.

3. Open a terminal and navigate to the root directory of your project where the `docker-compose.yml` file is located.

4. Run the following command to start your application:
   ```
   docker-compose up -d
   ```
   The `-d` flag runs the containers in detached mode, allowing them to run in the background.

5. Docker will pull the necessary images (if not already present) and start the containers for your frontend and backend services.

6. Once the process is complete, your application should be up and running. You can access it through the specified ports in your `docker-compose.yml` file.

## Stopping the Application

To stop the application and remove the containers, use:
```
docker-compose down
```

## Viewing Logs

To view the logs of your running containers:
```
docker-compose logs
```

Add the `-f` flag to follow the log output in real-time:
```
docker-compose logs -f
```

## Rebuilding Changes

If you make changes to your application code, you may need to rebuild the Docker images. Use:
```
docker-compose up -d --build
```

## Troubleshooting

If you encounter any issues, try the following:

1. Ensure all required ports are free and not used by other applications.
2. Check the Docker logs for any error messages.
3. Verify that your `docker-compose.yml` file is correctly configured.

For more detailed information, refer to the official [Docker Compose documentation](https://docs.docker.com/compose/).