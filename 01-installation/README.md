#

##

### Step 1: Install Docker

If you haven’t installed Docker yet, follow these steps to install it:

1. **For Ubuntu / Debian-based systems:**

   ```bash
   sudo apt update
   sudo apt install -y docker.io
   ```

2. **For macOS:**
   - Download Docker Desktop for Mac from [Docker's website](https://www.docker.com/products/docker-desktop).
   - Open the downloaded file and follow the installation instructions.

3. **For Windows:**
   - Download Docker Desktop for Windows from [Docker's website](https://www.docker.com/products/docker-desktop).
   - Follow the installation instructions.

4. **Verify Docker Installation:**

   ```bash
   docker --version
   ```

### Step 2: Pull Redis Image from Docker Hub

Docker Hub hosts a variety of Redis images. To get the latest Redis image, use the following command:

```bash
docker pull redis
```

This command downloads the latest Redis image available on Docker Hub.

### Step 3: Run Redis Container

Now, you can run the Redis container. This command will start Redis in a detached mode (running in the background):

```bash
docker run -d --name my-redis -p 6379:6379 redis
```

- `-d` runs the container in detached mode.
- `--name my-redis` gives the container a name, making it easier to manage.
- `-p 6379:6379` maps Redis's default port (6379) to the host system, so you can access Redis on `localhost:6379`.

### Step 4: Verify Redis Installation

To confirm that Redis is running, use the following command:

```bash
docker ps
```

You should see `my-redis` running in the list of active containers.

### Step 5: Access Redis CLI

You can access the Redis CLI to interact with the Redis instance:

```bash
docker exec -it my-redis redis-cli
```

This command opens a Redis CLI within the running Redis container. You can now run Redis commands, for example:

```bash
ping
```

You should receive a `PONG` response, indicating that Redis is running.

### Step 6: Configure Persistence (Optional)

Redis stores data in-memory but can persist data to disk. To enable persistence, mount a volume when running the container:

```bash
docker run -d --name my-redis -p 6379:6379 -v /my/local/redisdata:/data redis redis-server --appendonly yes
```

- `-v /my/local/redisdata:/data` mounts the host directory `/my/local/redisdata` to the container’s `/data` directory.
- `--appendonly yes` enables Redis persistence.

### Step 7: Test Redis from a Client Application (Optional)

To connect to Redis from an application, use `localhost` and port `6379` in your configuration.

```bash
redis://localhost:6379
```

### Step 8: Stop and Remove the Redis Container

If you need to stop or remove the Redis container, use these commands:

- **Stop the Redis container:**

  ```bash
  docker stop my-redis
  ```

- **Remove the Redis container:**

  ```bash
  docker rm my-redis
  ```

### Recap

1. Install Docker.
2. Pull the Redis image from Docker Hub.
3. Run the Redis container.
4. Access the Redis CLI to interact with Redis.
5. Optionally, enable persistence by mounting a local volume.
6. Stop and remove the Redis container when finished.

Now you have a Redis instance up and running with Docker!

### Links

 **Install Redis**: [https://redis.io/docs/latest/operate/oss_and_stack/install/install-redis/](https://redis.io/docs/latest/operate/oss_and_stack/install/install-redis/)
