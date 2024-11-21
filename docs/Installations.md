---
title: Code
nav_order: 2
---

# Installations

### **Clone the Repository**
Follow these steps to get a local copy of the project:
1. Clone the repository: `git clone https://github.com/your_username/opendrive-framework.git`
2. Navigate to the project root: `cd OpenDrive`
3. Install the dependencies: `pip install -r requirements.txt`

### **Fork the Repository**
Follow these steps to create your own copy of the project repository:

1. Fork the repository on GitHub: `https://github.com/OpenDriveDevelopment/OpenDrive`
2. Clone your fork: `git clone https://github.com/YOUR_USERNAME/OpenDrive.git`
3. Navigate to the project root: `cd OpenDrive`
4. Add the original repository as the upstream remote: `git remote add upstream https://github.com/OpenDriveDevelopment/OpenDrive.git`
5. Fetch updates from the original repository: `git fetch upstream`
6. Merge changes into your local copy: `git merge upstream/main`

### **Install Docker Compose**
Follow these steps to install Docker Compose on your system:

#### **Linux**
1. Download Docker Compose:  
   `curl -L "https://github.com/docker/compose/releases/download/$(curl -s https://api.github.com/repos/docker/compose/releases/latest | jq -r .tag_name)/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose`
   
2. Set permissions:  
   `sudo chmod +x /usr/local/bin/docker-compose`

3. Verify:  
   `docker-compose --version`

#### **Windows**
1. Install Docker Desktop from [Docker's website](https://www.docker.com/products/docker-desktop).
2. Docker Compose is bundled with Docker Desktop. Verify with:  
   `docker-compose --version`

#### **macOS**
1. Install Docker Desktop from [Docker's website](https://www.docker.com/products/docker-desktop).
2. Docker Compose is included in Docker Desktop. Verify with:  
   `docker-compose --version`


### Running Kafka Locally

First, make sure you have docker-compose installed. Then:

1. Download this docker-compose file to a preferred location.
2. From its directory, run `docker-compose up -d`.  
   It sets up everything automatically, running it in the background!

You can connect your Kafka clients via `localhost:9092`.  
It has a helpful UI at [http://localhost:9021](http://localhost:9021)  
which allows you to easily inspect and manage topics.

When finished, run `docker-compose down` from the download location to stop it.

