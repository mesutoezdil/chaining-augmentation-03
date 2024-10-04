# Chaining Augmentation 03

## Overview

This project demonstrates a way to create and use embeddings for text search. It takes an input text, generates a vector embedding for it using the Prediction Guard API, and searches through precomputed vectorized chunks to find the most relevant match based on cosine similarity.

## Features

- Embeds text using the `Prediction Guard` API.
- Computes cosine similarity between vector embeddings.
- Finds the most similar chunk of text from precomputed vectorized data.

## Getting Started

### Prerequisites

- Go (version 1.22.6 or later)
- A `Prediction Guard` API Key
- A properly structured `chunks.json` file

### Project Structure

```
chaining-augmentation-03/
│
├── main.go                  # Main source code of the project
├── chunks.json              # Precomputed vectorized chunks (mock data or actual data)
├── README.md                # Project documentation (this file)
├── go.mod                   # Go module file
└── go.sum                   # Dependency management file
```

## Setting Up the Project

### 1. Clone the Repository

Clone the repository to your local machine:
```sh
git clone https://github.com/mesutoezdil/chaining-augmentation-03.git
cd chaining-augmentation-03
```

### 2. Set Up the Environment

- Ensure Go is installed by running:
  ```sh
  go version
  ```

- Set the `Prediction Guard` API Key as an environment variable:
  ```sh
  export PGKEY="YOUR_API_KEY"
  ```

### 3. Create the `chunks.json` File

Create a file named `chunks.json` in the `../example2/` directory. This file contains vectorized data chunks that the program will use for searching. Here is an example structure:

```json
[
    {
        "id": 1,
        "chunk": "This is a sample chunk of text.",
        "vector": [0.1, 0.2, 0.3, 0.4],
        "metadata": "sample metadata"
    },
    {
        "id": 2,
        "chunk": "Another example of a chunk of text.",
        "vector": [0.5, 0.6, 0.7, 0.8],
        "metadata": "example metadata"
    }
]
```

Ensure that the path matches the one in your code, or update the code to point to the correct file path.

### 4. Run the Project

- Initialize the Go modules if not already done:
  ```sh
  go mod init chaining-augmentation-03
  go mod tidy
  ```

- Run the program:
  ```sh
  go run main.go
  ```

This will:
1. Load the vectorized chunks from `chunks.json`.
2. Generate an embedding vector for the input message.
3. Find and print the most relevant chunk based on cosine similarity.

## How It Works

1. **Embedding the Input Message**:  
   The program takes an input string (e.g., "What do I need in order to respond to reviewers?") and uses the Prediction Guard API to generate its vector embedding.

2. **Comparing Vectors**:  
   It then compares the vector embedding of the input message to the precomputed vector embeddings in `chunks.json` using cosine similarity.

3. **Finding the Best Match**:  
   The chunk of text from `chunks.json` with the highest cosine similarity to the input message is returned as the most relevant chunk.

## Customization

- **Change Input Message**:  
  Modify the `message` variable in `main.go` to test different queries.
  
- **Adjust Chunks Data**:  
  Add or modify chunks in `chunks.json` to enhance the search capabilities.
