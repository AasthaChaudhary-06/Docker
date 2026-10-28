# HTML Website with Docker

A static HTML website served by Nginx in a Docker container.

## Project files

- `index.html` — website content and styling
- `Dockerfile` — builds the image and serves the site with Nginx
- `.dockerignore` — excludes unnecessary files from the Docker build context

## Requirements

Install and start Docker Desktop:
https://www.docker.com/products/docker-desktop/

## Build the Docker image

Run these commands in the folder containing the `Dockerfile`:

```bash
docker build -t my-html-website .
```

## Run the website

```bash
docker run -d --name my-html-website-container -p 8080:80 my-html-website
```

Open http://localhost:8080 in your browser.

## Check status and logs

```bash
docker ps
docker logs my-html-website-container
```

## Stop and remove the container

```bash
docker stop my-html-website-container
docker rm my-html-website-container
```

## Rebuild after editing index.html

```bash
docker stop my-html-website-container
docker rm my-html-website-container
docker build -t my-html-website .
docker run -d --name my-html-website-container -p 8080:80 my-html-website
```

If the container does not exist, skip the first two commands and run the build and run commands.

## Upload the project to GitHub

Create a new empty repository on GitHub. Then, from the project folder, run:

```bash
git init
git add index.html Dockerfile .dockerignore README.md
git commit -m "Add HTML website with Docker"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/YOUR-REPOSITORY.git
git push -u origin main
```

Replace the example URL with your own repository URL.

## Important

A Dockerfile describes how to build an image and configure a container. Commands such as `docker build` and `docker run` are run in Terminal; the Dockerfile does not automatically execute those commands on your Mac.
