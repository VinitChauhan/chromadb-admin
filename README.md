# Chromadb Admin

Admin UI for the Chroma embedding database, built with Next.js

![screely-1696786774071](https://github.com/flanker/chromadb-admin/assets/109811/6d4369d4-d10c-49f7-8342-89849f271dbe)

## Links：

* GitHub Repo: [https://github.com/flanker/chromadb-admin](https://github.com/flanker/chromadb-admin)
* Chroma Official Website [https://docs.trychroma.com](https://docs.trychroma.com)

## Authentication Support

<img width="743" alt="image" src="https://github.com/flanker/chromadb-admin/assets/109811/c15cab9a-db80-4e2f-b732-a3bd5ef557da">

## Run Locally

First, start the development server:

```bash
npm run dev
# or
yarn dev
# or
pnpm dev
# or
bun dev
```

THen, open [http://localhost:3001](http://localhost:3001) in your browser to see the app.

## Run with Docker

Run

```bash
docker run -p 3001:3001 fengzhichao/chromadb-admin
```

and visit https://localhost:3001⁠ in the browser.

*NOTE*: Use `http://host.docker.internal:8000` for the connection string if you want to connect to a ChromaDB instance running locally.

## Build and Run with Docker locally

Build the Docker image:

```bash
docker build -t chromadb-admin .
```

Run the Docker container:

```bash
docker run -p 3001:3001 chromadb-admin
```

##Trouble shooting

1. Verify ChromaDB is Running
First, make sure your local ChromaDB server is actually running:

bash# If using Docker
docker ps | grep chroma

# If running directly
curl http://localhost:8000/api/v2/heartbeat

You should get a response like {"nanosecond heartbeat": ...}

2. Check ChromaDB Admin Configuration
In ChromaDB Admin, go to the Setup page and verify:

ChromaDB URL: Should be http://localhost:8000 (or your actual ChromaDB port)
If using Docker: Try http://host.docker.internal:8000 instead

3. Common Connection Issues
CORS Issues: ChromaDB might not be configured to accept requests from the admin interface. Start ChromaDB with CORS enabled:
bash

# If running ChromaDB directly
chroma run --host 0.0.0.0 --port 8000 --path ./chroma_data

# If using Docker
docker run -p 8000:8000 chromadb/chroma:latest

4. Test ChromaDB API Directly
Verify your ChromaDB API is working:

bash# Test the collections endpoint directly
curl http://localhost:8000/api/v2/collections

# Should return something like: {"collections": []}


## Note

This is NOT an official Chroma project.

This project is licensed under the terms of the MIT license.
