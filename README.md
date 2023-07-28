# Batchalign Docker

## Step 1: Download Docker Desktop
Follow [these instructions](https://www.docker.com/products/docker-desktop/) to first acquire a copy of Docker Desktop.

## Step 2: Download Manifest
On a command prompt/terminal, execute:

```bash
curl -O https://raw.githubusercontent.com/TalkBank/batchalign-docker/master/docker-compose.yml
```

## Step 3: Run Services
On the *same* command prompt/terminal as the line before, execute:

```bash
docker compose up -d
```

## Step 4: Wait
Wait a little as the service provisions. 


## Step 5: Use
Open your web browser and navigate to

```bash
http://localhost
```

You should see a web interface for Batchalign running ony our local machine.
