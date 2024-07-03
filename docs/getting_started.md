
# Getting Started

Welcome to the AI Marketplace! This section will guide you through the initial steps to get started with uploading your AI models.

## Prerequisites
Before you begin, ensure you have the following:
- Python 3.9 or higher installed on your local machine.
- Basic knowledge of FastAPI and Docker.
- Your AI model ready to be served via an API.

## Overview
The process of uploading your model involves the following steps:
1. Defining the input and output types.
2. Creating a FastAPI application to serve your model.
3. Packaging your application with Docker.
4. Uploading your model to the AI Marketplace.

## Setting Up Your Environment
1. **Install Python:**
   Ensure Python 3.9 or higher is installed on your machine. You can download it from [python.org](https://www.python.org/downloads/).

2. **Install FastAPI:**
   FastAPI is the web framework we will use to serve your model.

   ```sh
   pip install fastapi
   ```

3. **Install Uvicorn:**
   Uvicorn is an ASGI server that runs FastAPI applications.

   ```sh
   pip install uvicorn
   ```

4. **Install Docker:**
   Docker is used to package your application into a container. You can download and install Docker from [docker.com](https://www.docker.com/get-started).

## Creating Your Project Structure
Create a new directory for your project and navigate into it:

```sh
mkdir your_model
cd your_model
```

Inside this directory, you will create the following files:
- `Dockerfile`
- `main.py`
- `requirements.txt`

If your model requires additional files or functions, ensure they are included in the same directory. For example, if you have a file named `utils.py` with helper functions, include it here.

## Example Project Structure
```
your_model/
├── Dockerfile
├── main.py
├── requirements.txt
└── utils.py
```

We will go into detail about each of these files in the following sections.

---

Proceed to the next section: [Defining Input and Output Types](input_output_types.md)