
# Packaging with Docker

In this section, you will learn how to package your FastAPI application with Docker. We will provide detailed instructions and examples to ensure your model is ready for deployment.

## Creating a Dockerfile
A Dockerfile is a script that contains a series of commands to create a Docker image. Here’s an example Dockerfile for your FastAPI application:

```dockerfile
FROM python:3.9-slim

# Set working directory
WORKDIR /app

# Copy the requirements file and install dependencies
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy the rest of the application code
COPY . .

# Expose the port
EXPOSE 8000

# Run the FastAPI app with Uvicorn
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]
```

## Creating the Requirements File
List all the dependencies required for your application in `requirements.txt`.

**Example:**
```text
fastapi
uvicorn
pydantic
```
Include any additional libraries your model might require.

## Testing Your Model Locally
Before deploying your model, it’s crucial to test it locally to ensure everything is working correctly. Follow these steps to build and run your Docker container locally:

1. **Navigate to your project directory:**
   ```sh
   cd your_model
   ```

2. **Build the Docker image:**
   ```sh
   docker build -t your_model_image .
   ```

3. **Run the Docker container:**
   ```sh
   docker run -p 8000:8000 your_model_image
   ```

4. **Test your API:**
   Open your browser or use a tool like `curl` or Postman to test your API endpoints. For example, navigate to `http://localhost:8000/docs` to view the automatically generated API documentation provided by FastAPI.

## Example Project Structure
Ensure your project directory includes all necessary files:
```
your_model/
├── Dockerfile
├── main.py
├── requirements.txt
└── utils.py  # Any additional files your model requires
```

## Deploying Your Model
Once you have tested your model locally and ensured everything is working, you can proceed to deploy it to the AI Marketplace. Follow these steps:

1. **Zip your project files:**
   ```sh
   zip -r your_model.zip .
   ```

2. **Upload the zip file:**
   Log in to your AI Marketplace account, navigate to the model upload section, and upload your zip file.

3. **Provide model details:**
   Fill in the required details about your model, including input and output types.

4. **Deploy your model:**
   Once uploaded, your model will be automatically launched on the site through Docker.

## Additional Tips
- **Keep your Docker image lightweight:** Use a slim base image and avoid unnecessary packages to keep your Docker image small and efficient.
- **Use environment variables:** For configuration settings, consider using environment variables to make your application more flexible and secure.

---

Proceed to the next section: [Uploading Your Model](uploading_your_model.md)