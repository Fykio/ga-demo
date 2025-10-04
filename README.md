# GitHub Actions CI Demo

A simple Python app built with Flask demonstrating continuous integration using GitHub Actions

## Prerequisites

- Python `3.x` installed on your machine
- Docker installed on your machine
- Git installed on your machine
- GitHub account
- DockerHub account (for pushing the image built in the `ga.yml` workflow)

## Getting Started

1. Clone this repository to your local machine.
   ```text
   git clone https://github.com/Fykio/ga-demo.git
   ```
2. Navigate into the repository directory
   ```text
   cd ga-demo
   ```

## How to run

### As Python App within `venv`

1. Create a virtual environment
   ```text
   python -m venv venv
   ```
2. Activate the virtual environment
   - On Linux/macOS:
     ```text
     source venv/bin/activate
     ```
   - On Windows:
     ```text
     venv\Scripts\activate
     ```
3. Install the required dependencies:
   ```text
   pip install -r requirements.txt
   ```
4. Run the application:
   ```text
   python app.py
   ```
   The app will start and run on `http://localhost:7878/`. Open your browser and navigate to this URL to see the app in action.

### As Container using Docker

1. Build the Docker image using the Dockerfile:
   ```text
   docker build -t ga-demo .
   ```
2. Run the container:
   ```text
   docker run -d -p 7878:7878 ga-demo
   ```
   The app will be accessible at http://localhost:7878/.

## Workflow

This repository includes a CI workflow defined in `.github/workflows/ga.yml`. It triggers on every push to the `main` branch and performs the following _steps_:

1. Checks out the code.
2. Sets up Python on the _runner_.
3. Installs the required app dependencies on the _runner_.
4. Builds the docker image of the app.
5. Execute vulnerability scanning of the image using _Trivy_.
6. Login into Docker Hub with the provided `username` in Repository Variables and the password (Docker Hub PAT) in Repository Secrets.
7. Push the image to Docker Hub.

## Dependencies

- Listed in `requirements.txt`

## License

This repository is free to use.
