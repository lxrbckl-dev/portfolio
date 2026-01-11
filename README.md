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
```bash
docker run -d \
  --name portfolio \
  -p 8046:8080 \
  --restart unless-stopped \
  lxrbckl/portfolio:sawyer-showalter-business
```

---

[`dillionverma/portfolio`](https://github.com/dillionverma/portfolio) [`Docker Hub`](https://hub.docker.com/r/lxrbckl/portfolio)
