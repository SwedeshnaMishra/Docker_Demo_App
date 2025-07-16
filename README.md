# 🐳 Docker Demo App - User Profile Application

This is a simple demo application showcasing a full-stack setup using Docker. It includes:

- A static frontend (`index.html`) using pure JavaScript and CSS
- A Node.js backend with Express
- MongoDB for data storage

All components are containerized using Docker for seamless development and deployment.

---

## 🐳 Running the App with Docker

### Step 1: Create a Docker network (optional)

```bash
docker network create mongo-network
```
> This step is optional. You can skip it and omit `--net` in the upcoming commands if using the default network.

### Step 2: Start MongoDB container

```bash
docker run -d -p 27017:27017 \
  -e MONGO_INITDB_ROOT_USERNAME=admin \
  -e MONGO_INITDB_ROOT_PASSWORD=password \
  --name mongodb \
  --net mongo-network \
  mongo
```

### Step 3: Start Mongo Express (MongoDB UI)

```bash
docker run -d -p 8081:8081 \
  -e ME_CONFIG_MONGODB_ADMINUSERNAME=admin \
  -e ME_CONFIG_MONGODB_ADMINPASSWORD=password \
  -e ME_CONFIG_MONGODB_SERVER=mongodb \
  --name mongo-express \
  --net mongo-network \
  mongo-express
```

### Step 4: Access Mongo Express in your browser
http://localhost:8081

### Step 5: In Mongo Express
- Create a new database: `user-account`
- Inside it, create a collection: `users`

### Step 6: Start Node.js App Locally

```bash
npm install
node server.js
```

### Step 7: Access the Node.js app
http://localhost:3000

---

## 🐋 Running with Docker Compose

### Step 1: Start MongoDB and Mongo Express

```bash
docker-compose -f docker-compose.yaml up
```
> Mongo Express will be available at: http://localhost:8080

### Step 2: In Mongo Express
- Create database: `my-db`
- Create collection: `users`

### Step 3: Start Node.js App

```bash
npm install
node server.js
```

### Step 4: Access the App
http://localhost:3000

---

## 🛠️ Build Docker Image for the App
To build a Docker image from your Node.js application:

```bash
docker build -t my-app:1.0 .
```
> `.` denotes the location of the Dockerfile (current directory).

---

## For Contributing
If you want to contribute to this project, please follow these steps:
- `Fork` the repository.
- Create a new branch `(git checkout -b feature/your-feature-name)`.
- Make your changes and commit them `(git commit -m 'Add some feature')`.
- Push to the branch `(git push origin feature/your-feature-name)`.
- Open a pull request.

---

## Project Maintainer
**Github:** [Swedeshna Mishra](https://github.com/SwedeshnaMishra)
