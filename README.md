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
  --restart unless-stopped \
  lxrbckl/portfolio:latest
```