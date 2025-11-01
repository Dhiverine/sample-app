# k8s-docker-demo

## Run locally with Docker
```bash
docker compose up --build
# frontend on http://localhost:8082
# backend on http://localhost:3000
```
DB is persisted in named volume `db-data`.

## Build images (optional)
```bash
docker build -t yourrepo/myapp-backend ./backend
docker build -t yourrepo/myapp-frontend ./frontend
```

## Deploy to Kubernetes with Helm
```bash
cd helm/my-app
helm install demo . \
  --set backend.image.repository=yourrepo/myapp-backend \
  --set frontend.image.repository=yourrepo/myapp-frontend \
  --set ingress.enabled=true \
  --set ingress.host=myapp.example.com
```
