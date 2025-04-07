# knowledge-graphs-with-llms

Build Knowledge Graphs Using 6 different LLMs on the Neo4j Aura platform.

## Detailed Setup of Neo4j Aura

To begin constructing knowledge graphs, you'll need a Neo4j Aura account and a running database instance. Follow these detailed steps:

1.  **Create a Neo4j Aura Account**:
    *   Navigate to the [Neo4j Aura](https://neo4j.com/cloud/aura/) website.
    *   Sign up for a new account or log in if you already have one. Neo4j Aura offers a free tier suitable for development and experimentation.

2.  **Create a New Database Instance**:
    *   Once logged in, you'll be directed to the Neo4j Aura console.
    *   Click on the option to create a new database instance. You'll be prompted to choose a plan (e.g., free, professional). Select the plan that best fits your needs.
    *   Specify a name for your database instance. This name will help you identify the instance in the future.
    *   Choose a region for your database. Selecting a region close to your location can reduce latency.
    *   Set a password for the `neo4j` user. This password is crucial for securing your database.

3.  **Note Connection Details**:
    *   After the database instance is created, you'll need to gather the connection details. These details are essential for connecting to your Neo4j database from your application.
    *   The connection details include:
        *   **NEO4J\_URI**: This is the URI (Uniform Resource Identifier) for your database. It typically follows the format `neo4j+s://<your-instance-id>.databases.neo4j.io`. The `neo4j+s` scheme indicates a secure connection.
        *   **NEO4J\_USERNAME**: The default username is usually `neo4j`.
        *   **NEO4J\_PASSWORD**: This is the password you set during the database instance creation.

4.  **Update the .env File**:
    *   In your project directory, locate the `.env` file. This file stores environment-specific configuration settings.
    *   Open the `.env` file and add or update the following lines with your Neo4j Aura connection details:

        ```
        NEO4J_URI="neo4j+s://<your-instance-id>.databases.neo4j.io"
        NEO4J_USERNAME="neo4j"
        NEO4J_PASSWORD="<your-neo4j-password>"
        ```

    *   Replace `<your-instance-id>` with your actual instance ID and `<your-neo4j-password>` with the password you created.
    *   Save the `.env` file. This will allow your application to connect to your Neo4j Aura instance securely.

## The Role of LangChain in Knowledge Graph Construction

LangChain is instrumental in the construction of knowledge graphs with LLMs because it provides a structured and efficient way to interact with these models and manage the data flow. Here's a detailed breakdown:

*   **Orchestration of LLM Interactions**: LangChain acts as an orchestrator, managing the calls to different LLMs. It abstracts away the complexities of interacting with various LLM APIs, allowing you to focus on the logic of your application.
*   **Knowledge Extraction from Unstructured Data**: LLMs are capable of understanding and extracting information from unstructured text. LangChain provides tools to feed text data to LLMs and retrieve structured knowledge.
*   **Structuring Knowledge into Graph Format**: The extracted knowledge needs to be structured in a way that can be represented as a graph. LangChain helps in defining entities, relationships, and properties, and converting the extracted information into a graph-compatible format.
*   **Pushing Data to Neo4j**: Once the knowledge is structured, it needs to be stored in a graph database like Neo4j. LangChain provides connectors to Neo4j, making it easy to push the structured data into the database.
*   **Simplified Integration**: LangChain offers a unified interface for working with different LLMs and graph databases, simplifying the integration process and reducing the amount of boilerplate code you need to write.

In summary, LangChain streamlines the entire process of building knowledge graphs, from extracting information from unstructured data to storing it in a structured graph database.

## Detailed Usage of Different LLMs

This repository showcases the use of multiple LLMs, each requiring specific setup and API keys. Here's a detailed guide on how to use each LLM:

### Accessing Groq and Gemini APIs

*   **Groq**:
    *   **Obtain an API Key**: Visit the [Groq platform](https://console.groq.com/users/api_keys) and create an account or log in.
    *   Generate an API key from your account dashboard.
    *   **Set the API Key**: In your `.env` file, add the following line, replacing `<your-groq-api-key>` with the API key you generated:

        ```
        GROQ_API_KEY="<your-groq-api-key>"
        ```

    *   **Use Groq Models**: In your code, specify the Groq model you want to use and ensure that the `GROQ_API_KEY` environment variable is accessible.
*   **Gemini**:
    *   **Obtain an API Key**: Go to the [Google AI Studio](https://makersuite.google.com/app/apikey) and create a project.
    *   Generate an API key for your project.
    *   **Set the API Key**: In your `.env` file, add the following line, replacing `<your-gemini-api-key>` with your API key:

        ```
        GOOGLE_API_KEY="<your-gemini-api-key>"
        ```

    *   **Use Gemini Models**: In your code, specify the Gemini model you want to use and ensure that the `GOOGLE_API_KEY` environment variable is accessible.

### Building Ollama and Downloading Models Locally

Ollama allows you to run LLMs locally, providing more control and privacy. Here’s how to set it up:

1.  **Install Ollama**:
    *   Visit the [Ollama's website](https://ollama.ai/) and download the Ollama CLI for your operating system.
    *   Follow the installation instructions provided on the website.

2.  **Download Models Locally**:
    *   Open your terminal and use the Ollama CLI to download the models you want to use. For example, to download the `llama2` model, run:

        ```
        ollama pull llama2
        ```

    *   Ollama will download the model and set it up for local use.

3.  **Configure the .env File**:
    *   To use the local Ollama setup, you might need to configure your application to point to the Ollama server. This typically involves setting the base URL for the Ollama API.
    *   In your `.env` file, add the following line, replacing `<ollama-server-url>` with the URL of your Ollama server (usually `http://localhost:11434`):

        ```
        OLLAMA_BASE_URL="<ollama-server-url>"
        ```

4.  **Use Ollama Models**:
    *   In your code, specify the Ollama model you want to use and ensure that the `OLLAMA_BASE_URL` environment variable is accessible.

## Summary

This repository provides a comprehensive guide to building knowledge graphs using various LLMs and Neo4j Aura. By following the detailed steps outlined in this document, you can set up your environment, configure your LLMs, and start constructing your own knowledge graphs.
