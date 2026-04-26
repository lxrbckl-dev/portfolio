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
docker build -t portfolio-app .
docker run --name portfolio-app \   
  -p 8010:8080 \
  -v <host-data-path>:/app/src/data \
  portfolio-app
```

### Server Deployment

The `lxrbckl/portfolio:jbarger-app` image is built and pushed to Docker Hub automatically on every commit to `main` by the [`dockerhub-build-push`](.github/workflows/dockerhub-build-push.yml) GitHub Actions workflow.

```bash
# Pull the latest image
docker pull lxrbckl/portfolio:jbarger-app

# Run it detached, with auto-restart, on host port 8047
docker run -d \
  --name jbarger-app \
  -p 8047:8080 \
  --restart unless-stopped \
  lxrbckl/portfolio:jbarger-app
```

Once the container is up, the site is reachable at `http://<host>:8047`.

To update an already-running container:

```bash
docker pull lxrbckl/portfolio:jbarger-app
docker stop jbarger-app && docker rm jbarger-app
```

---

[`dillionverma/portfolio`](https://github.com/dillionverma/portfolio) [`Docker Hub`](https://hub.docker.com/r/lxrbckl/portfolio)
