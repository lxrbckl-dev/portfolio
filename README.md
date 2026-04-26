# portfolio
> A forked portfolio website, containerized to work on a local server with pipelines.
>
> **`TypeScript`** **`Docker`** **`CSS`** `next-js` `tailwind` `radix-ui` `github-actions`

---

### Local Development
```bash
pnpm install
pnpm dev
# makes changes in ./src/data/data.tsx
```

### Local Deployment
```bash
docker build -t project-jordyn .
docker run --name project-jordyn \
  -p 8010:8080 \
  -v <host-data-path>:/app/src/data \
  project-jordyn
```

### Server Deployment

The `lxrbckl/project-jordyn` image is built and pushed to Docker Hub automatically on every commit to `main` by the [`dockerhub-build-push`](.github/workflows/dockerhub-build-push.yml) GitHub Actions workflow.

```bash
# Pull the latest image
docker pull lxrbckl/project-jordyn

# Run it detached, with auto-restart, on host port 8047
docker run -d \
  --name project-jordyn \
  -p 8047:8080 \
  --restart unless-stopped \
  lxrbckl/project-jordyn
```

Once the container is up, the site is reachable at `http://<host>:8047`.

To update an already-running container:

```bash
docker pull lxrbckl/project-jordyn
docker stop project-jordyn && docker rm project-jordyn
```

---

[`dillionverma/portfolio`](https://github.com/dillionverma/portfolio) [`Docker Hub`](https://hub.docker.com/r/lxrbckl/project-jordyn)
