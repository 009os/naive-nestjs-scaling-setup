# NestJS Load Balancer with Nginx

This is a simple setup to run multiple NestJS containers behind an Nginx load balancer for horizontal scaling locally using Docker.

## 🧱 Folder Structure

```
nest-nginx-loadbalancer/
├── app/                  ← NestJS App here
│   ├── Dockerfile
│   ├── package.json
│   ├── tsconfig.json
│   └── src/
│       ├── main.ts
│       ├── app.module.ts
│       ├── app.controller.ts
│       └── app.service.ts
├── nginx/
│   └── default.conf      ← Nginx config
├── docker-compose.yml    ← All services defined here
└── README.md
```

## ✅ Steps to Run

1. **Navigate to the project directory:**
   ```bash
   cd nest-nginx-loadbalancer
   ```

2. **Build and start everything:**
   ```bash
   docker-compose up --build
   ```

3. **Visit the application:**
   ```
   http://localhost:8080/
   ```

## 🧠 How it works

- **NestJS app** is running in 2 containers (app1, app2)
- **Nginx** sits in front as a load balancer
- Requests hit `localhost:8080` and are distributed between instances
- Every refresh will randomly go to app1 or app2 (round-robin)

## 📝 Notes

- The NestJS controller includes a `console.log("Handled by container")` to see which instance handled the request
- Check the Docker logs to see which container processed each request
- The setup uses round-robin load balancing by default

## 🛠️ Commands

- **Start services:** `docker-compose up --build`
- **Stop services:** `docker-compose down`
- **View logs:** `docker-compose logs -f`
- **View specific service logs:** `docker-compose logs -f app1` or `docker-compose logs -f app2`
