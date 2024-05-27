# LLM Application with Pathway Vector Index

## Overview

This project demonstrates how to build a Large Language Model (LLM) application using Pathway's vector index on a Windows environment. The application leverages vector indexing to efficiently retrieve similar documents based on semantic similarity and integrates with LLM toolkits to provide powerful language processing capabilities.

## Features

- Efficient vector indexing for fast similarity searches and nearest neighbor queries.
- Integration with Pathway's vector index to avoid the need for a separate vector database.
- RESTful API for easy querying and data retrieval.
- Compatibility with popular LLM toolkits like Langchain and Llama-index.
- Scalable and high-performance solution for large datasets.
- Flexible data ingestion from various formats, including text and images.

## Prerequisites

- Docker installed on your Windows machine.
- OpenAI API key for generating embeddings and LLM responses.
- Python environment with necessary dependencies.

## Setup and Installation

1. **Install Docker:**
   - Download Docker Desktop for Windows from [Docker's official website](https://www.docker.com/products/docker-desktop).
   
2. **Create Dockerfile:**
   - In your project directory, create a file named `Dockerfile` with the following content:
     ```Dockerfile
     FROM pathwaycom/pathway:latest
     WORKDIR /app
     COPY requirements.txt ./
     RUN pip install --no-cache-dir -r requirements.txt
     COPY . .
     CMD ["python", "./your-script.py"]
     ```
   - Replace `your-script.py` with the name of your Python script file.

3. **Build Docker Image:**
   - Open a terminal or command prompt, navigate to your project directory, and run:
     ```bash
     docker build -t my-pathway-app .
     ```

4. **Run Docker Container:**
   - To start the container, run:
     ```bash
     docker run -it --rm --name my-pathway-app my-pathway-app
     ```
   - For environment variables and port mapping, use:
     ```bash
     docker run -p 8080:8080 --env-file .env my-pathway-app
     ```

## Running the Application

1. **Set Environment Variables:**
   - Configure necessary environment variables:
     ```python
     os.environ['OPENAI_API_KEY'] = '<your_openai_api_key>'
     os.environ['PATHWAY_DATA_DIR'] = '/content/data/pathway-docs/'
     os.environ['PATHWAY_REST_CONNECTOR_HOST'] = '0.0.0.0'
     os.environ['PATHWAY_REST_CONNECTOR_PORT'] = '8080'
     ```

2. **Run the Script:**
   - The script `your-script.py` contains the logic for setting up the vector index and handling queries. Ensure this script is in your project directory and includes necessary imports and function definitions.

3. **Test the Application:**
   - Use Postman or any HTTP client to test the RESTful API. Example curl command:
     ```bash
     curl -X POST -H "Content-Type: application/json" -d '{"user": "user", "query": "How to build vector index in Pathway?"}' http://0.0.0.0:8080/ | jq
     ```

## Code Structure

- `app.py`: Main script to run the application.
- `requirements.txt`: List of dependencies.
- `Dockerfile`: Docker configuration file for building the image.

## Resources

- [Pathway Developers](https://pathway.com/developers)
- [Vector Index Glossary](https://pathway.com/glossary/vector-index)
- [Pathway API Docs - Indexing](https://pathway.com/docs/api/indexing)
- [Pathway Docker Hub](https://hub.docker.com/r/pathwaycom/pathway)

## Contact

For any issues or questions, feel free to reach out to me via [LinkedIn](https://linkedin.com/in/vinayak-gavariya) or email.

Happy coding! 🚀
