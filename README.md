# Batchalign Docker

## Initial Setup
Follow these instructions to get started. 

### Step 1: Download Docker Desktop
Follow [these instructions](https://www.docker.com/products/docker-desktop/) to first acquire a copy of Docker Desktop. Once downloaded, open the app. See to it that the lower-left hand corner of the app is green: this means that Docker is ready.

### Step 2: Download Manifest
On a command prompt/terminal, execute:

```bash
curl -O https://raw.githubusercontent.com/TalkBank/batchalign-docker/master/docker-compose.yml
```

### Step 3: Run Services
On the *same* command prompt/terminal as the line before, execute:

```bash
docker compose up -d
```

### Step 4: Wait
Wait a little as the service provisions. You should be returned control of your terminal once that is the case.


### Step 5: Use
Open your web browser of choice and navigate to

```bash
http://localhost:4173
```

You should see a web interface for Batchalign; follow the instructions provided to tag your files.

## Seeing Logs 
To debug or get progress on runs, you may want to see the batchalign logs. In the same *directory* as where you first ran Batchalign following the instructions above, but not necessarily needed to be the same terminal, you can run:

```bash
docker compose logs backend
```

## Updating and/or Fixing
If you would like to update your copy of batchalign, follow these instructions.

### Step 1: Download (A New!) Manifest
On a command prompt/terminal, execute:

```bash
curl -O https://raw.githubusercontent.com/TalkBank/batchalign-docker/master/docker-compose.yml
```

### Step 2: Stop and Remove Old Version
On the *same* command prompt/terminal as the line before, execute:

```bash
docker compose stop
docker compose rm -f
```

### Step 3: Pull New Data
On the *same* command prompt/terminal as the line before, execute:

```bash
docker compose pull
```

### Step 4: Run Services
On the *same* command prompt/terminal as the line before, execute:

```bash
docker compose up -d
```

### Step 5: Wait
Wait a little as the service provisions. You can head back to Batchaligning!
