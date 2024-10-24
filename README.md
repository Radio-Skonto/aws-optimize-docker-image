Source -> https://aws.plainenglish.io/docker-pros-are-shrinking-images-by-99-the-hidden-techniques-you-cant-afford-to-miss-a70ee26b4cbf

1) Use && to chain commands and clean up in the same layer
```
RUN apt-get update && apt-get install -y python3-pip python3-dev && \
    pip3 install numpy pandas && \
    apt-get clean && rm -rf /var/lib/apt/lists/*
```
2) Use Docker Buildkit
```
DOCKER_BUILDKIT=1 docker build -t myapp .
```
3) Run Containers as Non-Root Users
```
RUN adduser --disabled-password --gecos "" appuser
USER appuser
```
4) scan your Docker images for known vulnerabilities.(Consider using tools like Trivy to regularly scan your images for vulnerabilities.
```
docker scan your-image:tag
```
5) Use .dockerignore file: Docker ignore similar to .gitignore. It lets you exclude specific files and directories from your final image.
```
# Exclude virtual environment
venv/
# Exclude cache, logs, and temporary files
__pycache__/
*.log
*.tmp
*.pyc
*.pyo
*.pyd
.pytest_cache
.git
.gitignore
README.md
# Exclude model training checkpoints and tensorboard logs
checkpoints/
runs/
```
6) 
