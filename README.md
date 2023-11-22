# README - Docker Hub Webhook API

## Overview

This API listens for webhooks from Docker Hub, indicating that a new Docker image has been pushed. Upon receiving a webhook notification, it pulls the new image and runs a specified script to handle the image, such as starting a container based on the image.

## Prerequisites

- Go (Golang) installed on your system.
- Docker installed and configured.
- Basic understanding of Docker Hub and webhooks.
- Ngrok for testing webhook locally.

## Setting Up and Running the API

### Step 1: Clone Repository

Clone the repository containing the API code to your local machine:

```bash
git clone https://github.com/ESPEDUZA/api-dockerhub.git
cd api-docker-hub
```

### Step 2: Ensure Script is Executable

Navigate to the directory containing script.sh and make it executable:

```bash
chmod +x script.sh
```

### Step 3: Run the API
In the directory containing your Go file (main.go), start the API:

```bash
go run main.go
```

The API will start and listen on http://localhost:8080.

### Step 4: Set Up Ngrok
Ngrok is used to expose your local server to the internet, allowing Docker Hub to trigger the webhook.

Download and Install Ngrok:

Download Ngrok from [Ngrok's website](https://ngrok.com/download) and follow the instructions to install it.

Start Ngrok:

Run Ngrok to expose your local server (assuming your API runs on port 8080):

```bash
ngrok http 8080
```
Ngrok will provide a public URL (e.g., http://12345abc.ngrok.io).

### Step 5: Configure Docker Hub Webhook

Go to your Docker Hub repository.
Navigate to the 'Webhooks' section.
Add a new webhook with the Ngrok URL: Use the URL provided by Ngrok followed by /webhook (e.g., http://12345abc.ngrok.io/webhook).
Testing
Push a new image to your Docker Hub repository or use the Docker Hub UI to test the webhook. The API should receive the webhook, and the script should execute as defined.

Notes
Ngrok URLs are temporary and will change every time you restart Ngrok.






