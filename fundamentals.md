# Container and Microservices Notes

## Key Concepts

### Containers
Containers are small independent processes which do not require a VM.

### Microservices
A microservice is a small service that does one task.

### API
API is the common language through which various microservices in different languages can talk.

## Benefits of Microservices
- Resilience
- Flexible Scaling
- Easy deployment

![alt text](image.png)

## Define Microservice
![alt text](image-1.png)

## Disadvantages [TODO add more]
- Latency issues
- Complexity
- Distribution causes more calls

## CONTAINER
![alt text](image-2.png)

## VM vs CONTAINER

### VM
![](image-3.png)

### Container
![](image-4.png)

## Container Flow
![alt text](image-5.png)

## Horizontal vs Vertical Scaling
Horizontal is more elastic - it scales when you need:
- 1 pod becomes 2 pods or multiple (like 2 houses)

Vertical scaling is when you need more room so you add a floor to that house (add more CPU and memory to same container).

Lambdas will horizontally scale and are managed by AWS.

## DOCKER and KUBERNETES
![alt text](image-6.png)

![alt text](image-7.png)

![alt text](image-8.png)

## GOOD READ
https://www.bmc.com/blogs/kubernetes-vs-docker-swarm/

## 1.1 Docker: Unveiling the Container Management Software
Docker serves two primary purposes:
- **Container Management Software**: Docker acts as the central hub for managing your containerized environment. It allows you to:
  - Manage Docker images: These are blueprints that define the structure and contents of your containers.
  - Manage Docker volumes: These are persistent storage directories that containerized applications can leverage to store data independent of the container itself.
  - Manage Docker containers: These are the running instances of your applications built from Docker images.

## 1.2 The Docker Engine: The Runtime Platform
The Docker engine is a software program that runs on various operating systems (Linux, Windows Server) and provides the underlying runtime environment for your Docker containers. It essentially acts as the platform upon which your containers execute.

## 1.3 Demystifying Docker Images: Blueprints for Containers
- **What is a Docker Image?** An image is a self-contained template that defines the instructions for building a Docker container. It encapsulates everything required to run an application, including:
  - The application code itself
  - The operating system libraries and dependencies the application needs
  - Configuration files

- **Layering Docker Images**: Images are constructed in a layered fashion. Each layer represents a specific instruction or step in the build process. This layered approach makes image creation efficient as subsequent containers based on the same image can reuse existing layers, reducing storage requirements.
  - Base Layer: The foundation of an image typically consists of a base operating system (e.g., Ubuntu, Debian).

- **Benefits of Docker Images**:
  - Portability: Since images contain everything a container needs, they are portable across different computing environments (physical machines, virtual machines, cloud platforms) as long as Docker is installed. This simplifies application deployment and streamlines development workflows.
  - Repeatability: Images ensure consistent application environments. Developers can be confident that their applications will run reliably regardless of the underlying system configurations.

## 1.4 Unveiling the Power of Docker Containers
- **What is a Docker Container?** A container is a running instance of a Docker image. It's a lightweight, self-contained unit that encapsulates an application and all its dependencies. This ensures that the application runs consistently across different environments.

- **Key Advantages of Containers**:
  - Fast Startup Times: Containers share the underlying operating system kernel with the host machine, eliminating the need to boot a separate OS for each container. This translates to significantly faster startup times compared to traditional virtual machines.
  - Resource Efficiency: Containers share the host system's resources, leading to efficient resource utilization compared to virtual machines, which allocate dedicated resources even when idle.
  - Isolation: Containers are isolated from each other and the host system, enhancing security and preventing conflicts between applications.

- **Real-World Example**: Consider a scenario where you have a containerized WordPress application. Multiple developers can work on this project simultaneously even if their development environments differ. The container itself includes all the necessary components (code, libraries, dependencies) to run WordPress, eliminating discrepancies caused by variations in individual development setups.

# Lab Manual: Running "Hello World" in Docker
## docker --version
1. Check if the hello-world image is now present locally:
# docker images
2. There should not be any container images on your computer yet.
3. Type and execute the following command:
## docker run hello-world
Explanation:
○ docker run: This command creates and starts a new container.
○ hello-world: This is the name of the Docker image that Docker will attempt to
run. It is a small test image designed to validate that Docker is working properly.

Step 4: List Docker Images
1. Check if the hello-world image is now present locally:
docker images
Explanation:
○ This command lists all Docker images available locally on your machine,
including the one just pulled.
Expected Output:
REPOSITORY TAG IMAGE ID CREATED SIZE
hello-world latest d1165f221234 2 months ago 13kB
Step 5: Inspect the Container
1. Check the list of containers (including stopped ones):
docker ps -a
Explanation:
○ docker ps -a: Displays all containers, whether running or stopped.
Expected Output:
CONTAINER ID IMAGE COMMAND CREATED STATUS PORTS NAMES
123abc45defg hello-world "/hello" 1 minute ago Exited (0) About a minute ago quirky_panini
Key Details:
● CONTAINER ID: Unique ID for the container.
● STATUS: Indicates that the container has exited since the hello-world container stops
automatically after displaying its message.
Step 6: Clean Up
1. Remove the hello-world container:
docker rm <CONTAINER ID>
Replace <CONTAINER ID> with the actual container ID from the docker ps -a output.
3. Remove the hello-world image:
docker rmi hello-world
Explanation:
○ docker rm: Deletes containers.
○ docker rmi: Deletes images from the local system
