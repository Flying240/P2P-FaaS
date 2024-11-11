# P2PFaaS: A Decentralized Framework for Function-as-a-Service (FaaS) in Edge and Fog Computing

## Table of Contents

- [Overview](#overview)
- [Motivation](#motivation)
- [Features](#features)
- [Architecture](#architecture)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
  - [Running the Framework](#running-the-framework)
- [Usage](#usage)
  - [API Endpoints](#api-endpoints)
  - [Examples](#examples)
- [Configuration](#configuration)
- [Benchmarks](#benchmarks)
- [Contributing](#contributing)
- [License](#license)
- [References](#references)

---

## Overview

*P2PFaaS* (Peer-to-Peer Function-as-a-Service) is a fully decentralized framework designed for scheduling and load balancing in Edge and Fog Computing environments. It leverages Docker containers to implement cooperative scheduling algorithms, with a focus on Function-as-a-Service (FaaS) models. The framework supports both x86 and ARM architectures, making it suitable for diverse hardware setups, including Raspberry Pi devices.

## Motivation

Edge and Fog Computing paradigms are essential for reducing latency and improving service availability in distributed environments, particularly for applications like smart cities. Traditional cloud-based orchestrators like Kubernetes do not offer custom scheduling flexibility, especially in resource-constrained edge nodes. *P2PFaaS* fills this gap by enabling peer-to-peer scheduling and load balancing without relying on a central orchestrator.

## Features

- *Decentralized Scheduling:* Fully peer-to-peer (P2P) without a central orchestrator.
- *Modular Design:* Built with Docker containers for portability.
- *Scalable Architecture:* Supports both x86 and ARM-based devices.
- *Custom Scheduling Algorithms:* Allows integration with Reinforcement Learning (RL) for dynamic scheduling decisions.
- *Low Latency Operations:* Uses WebSockets for reduced communication delays.
- *Extensive Logging and Monitoring:* Provides detailed logs for performance analysis.
  
## Architecture

The P2PFaaS framework consists of three main services:

1. *Scheduler Service*: Handles task scheduling and can forward requests to other nodes.
2. *Learner Service*: Implements RL models to optimize scheduling decisions.
3. *Discovery Service*: Manages peer discovery and network topology using a gossip protocol.

![P2PFaaS Architecture](https://your-image-url.com/architecture.png)

## Getting Started

### Prerequisites

- Docker (version 20.x or higher)
- Go (version 1.18 or higher)
- Python (version 3.8 or higher)
- Git

### Installation

1. *Clone the Repository:*

    bash
    git clone https://github.com/yourusername/P2PFaaS.git
    cd P2PFaaS
    

2. *Build Docker Containers:*

    bash
    docker-compose build
    

3. *Start the Services:*

    bash
    docker-compose up
    

### Running the Framework

- The Scheduler Service is accessible at http://localhost:18080
- The Learner Service runs on port 19020
- The Discovery Service is available at http://localhost:19000

To verify the services are running:

bash
curl http://localhost:18080/health


## Usage

### API Endpoints

- *Function Execution:*
  http
  POST /function/<fn>
  
  - Replace <fn> with the function name.
  
- *Training the RL Model:*
  http
  POST /train
  

- *Node Discovery:*
  http
  GET /nodes
  

### Examples

*Deploying a Face Recognition Function:*

1. Deploy the function container:

    bash
    docker run -d -p 8080:8080 --name face-recognition esimov/pigo-openfaas
    

2. Execute the function:

    bash
    curl -X POST http://localhost:18080/function/face-recognition -d '{"image": "base64_image_data"}'
    

## Configuration

The framework supports both static and dynamic configurations. Configuration files are located in the /config directory.

- *Static Configuration*: Update config.json for boot-time settings.
- *Dynamic Configuration*: Use the /configuration API for runtime changes.

## Benchmarks

The P2PFaaS framework has been tested on both virtual machines and physical devices (e.g., Raspberry Pi 4). Example benchmarks can be found in the [experiments repository](https://gitlab.com/p2p-faas/experiments).

### Sample Benchmark Results

| Algorithm          | Latency (ms) | Throughput (req/s) |
|--------------------|--------------|---------------------|
| Random Scheduling  | 20          | 1500               |
| RL-based Scheduling| 12          | 2000               |

## Contributing

We welcome contributions to enhance the P2PFaaS framework. Please follow the [contribution guidelines](CONTRIBUTING.md).

1. Fork the repository.
2. Create a new branch.
3. Make your changes and test thoroughly.
4. Submit a pull request.

## References

- [Reinforcement Learning: An Introduction](https://mitpress.mit.edu/9780262039246/)
- [OpenFaaS Documentation](https://docs.openfaas.com/)
- [Docker Documentation](https://docs.docker.com/)
