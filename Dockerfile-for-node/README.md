# Node.js Docker Setup

This project uses Docker to containerize a Node.js application for consistent development and deployment.

## Dockerfile

```dockerfile
# Build Stage
FROM node:22-alpine AS builder

WORKDIR /app

COPY package*.json ./

RUN npm ci

COPY . .

RUN npm run build


# Production Stage
FROM node:22-alpine

ENV NODE_ENV=production

WORKDIR /app

COPY package*.json ./

RUN npm ci --only=production

COPY --from=builder /app/dist ./dist

EXPOSE 3000

USER node

CMD ["node", "dist/index.js"]
```

---

## Build Docker Image

```bash
docker build -t node-app .
```

---

## Run Container

```bash
docker run -p 3000:3000 node-app
```

The application will run on:

```text
http://localhost:3000
```

---

## Notes

- Uses multi-stage builds for smaller image size
- Runs the container in production mode
- Uses a non-root user for better security
- Assumes the build output is inside the `dist` folder
