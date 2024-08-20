# Use the official Python image from the Docker Hub
FROM python:3.10

# Set the working directory
WORKDIR /app

# Copy the application files to the container
COPY . /app

# Ensure the config.yml directory exists in the container
RUN mkdir -p /usr/local/lib/python3.10/site-packages/titanic_model/

# Copy the config.yml to the required path in the container
COPY titanic_model/config.yml /usr/local/lib/python3.10/site-packages/titanic_model/config.yml

# Ensure the trained_models directory exists in the container
RUN mkdir -p /usr/local/lib/python3.10/site-packages/titanic_model/trained_models/

# Copy the trained model to the required path in the container
COPY titanic_model/trained_models/titanic__model_output_v0.0.1.pkl /usr/local/lib/python3.10/site-packages/titanic_model/trained_models/titanic__model_output_v0.0.1.pkl

# Upgrade PIP
RUN pip install --upgrade pip

# Copy the .whl file to the container
COPY titanic_model_api/titanic_model-0.0.1-py3-none-any.whl /app/titanic_model-0.0.1-py3-none-any.whl

# Install the model from the .whl file
RUN pip install /app/titanic_model-0.0.1-py3-none-any.whl

# Copy the requirements file to the container
COPY titanic_model_api/requirements.txt /app/requirements.txt

# Install the dependencies
RUN pip install -r /app/requirements.txt


# Expose the port the app runs on
EXPOSE 8000

# Start the FASTAPI application
CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8000"]
