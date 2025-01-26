# Docker Project

## 📌 Assignments
-------------------

### 🏗 Assignment 4: Dockerfile for Apache2
--------------------------------------------

#### **Objective**
Create a Dockerfile with the following specifications:
- Use **Ubuntu** as the base image.
- Install **Apache2**.
- Ensure **Apache2 starts automatically** when the container runs.

#### **Dockerfile (Assignment 4)**
```dockerfile
# Use Ubuntu as the base image
FROM ubuntu:latest

# Install Apache2
RUN apt update && apt install -y apache2

# Start Apache2 service automatically
CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]

Or

ENTRYPOINT apachectl -D FOREGROUND

# Expose port 80 for web access
EXPOSE 80
```

### 🌐 Assignment 5: Custom HTML Page in Apache2 Container
------------------------------------------------------------

#### **Objective**
- Create a **sample HTML file**.
- Modify the **Dockerfile** from Assignment 4.
- Replace the default **Apache homepage** with this HTML file.

#### **Steps**
1. **Create a sample HTML file** (`index.html`):
```html
<!DOCTYPE html>
<html>
<head>
    <title>Welcome to Dockerized Apache!</title>
</head>
<body>
    <h1>Hello, Docker!</h1>
    <p>This page is served from a Docker container running Apache2.</p>
</body>
</html>
```

2. **Modify the Dockerfile to copy `index.html`**:
```dockerfile
# Use Ubuntu as the base image
FROM ubuntu:latest

# Install Apache2
RUN apt update && apt install -y apache2

# Copy custom index.html to the Apache root directory
COPY index.html /var/www/html/index.html

# Start Apache2 service automatically
CMD ["apachectl", "-D", "FOREGROUND"]

# Expose port 80 for web access
EXPOSE 80
```

#### **Build & Run the Container**
```sh
# Build the Docker image
docker build -t myimg .

# Run the container, mapping port 80
docker run -d -p 80:80 --name assign5 myimg
```

#### **Verify**
- Open **http://localhost** in your browser.
- You should see the **custom HTML page** with "Hello, Docker!" message.
- You can also use your custom html like i have done here.

---

## 📂 Repository Structure
```
📦 docker-project
├── 📂 Assignment-4
│   ├── Dockerfile
├── 📂 Assignment-5
│   ├── Dockerfile
│   ├── index.html
└── README.md
```

## 🚀 How to Use
1. Clone this repository:
   ```sh
   git clone https://github.com/satrujitpani/docker-project.git
   ```
2. Navigate to the project folder:
   ```sh
   cd docker-project/Assignment-5
   ```
3. Build & Run the Docker container:
   ```sh
   docker build -t myimg .
   docker run -d -p 80:80 myimg
   ```
4. Open your browser and visit **http://localhost** to see the custom Apache page.

---

### 🏆 **Credits**
**Author**: [Satrujit Pani](https://github.com/satrujitpani)

📌 _Feel free to contribute by submitting pull requests!_ 🚀
