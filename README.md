# AI Experts Assignment (JS/TS)

A TypeScript project demonstrating proper bug finding, testing, and minimal fixes with docker support.

## How to run tests locally

### 1. Install dependencies:

       ```bash
       npm install
       ```

### 2. Run tests:

    ```bash
    npm test
    ```

## How to build and run tests with Docker

Replace ai-assignment with any image name you want. eg: test-suite or any other name you want to name your image

### 1. Build the Docker image:

    ```bash
      docker build -t ai-assignment .
    ```
      
### 2. Run tests in Docker:
    ```bash
      docker run ai-assignment
    ```

