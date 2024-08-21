# Use the official Python image from the Docker Hub
FROM python:3.10

# Set the working directory inside the container
WORKDIR /app

# Copy application files to the container
COPY Titanic_Project/titanic_model_api/ /app

# Copy config file
COPY Titanic_Project/titanic_model/config.yml /usr/local/lib/python3.10/site-packages/titanic_model/config.yml

# COPY Titanic_Project/titanic_model/trained_models/titanic__model_output_v0.0.1.pkl Titanic_Project/titanic_model_api/
# Copy the trained model file
COPY Titanic_Project/titanic_model/trained_models/titanic__model_output_v0.0.1.pkl /usr/local/lib/python3.10/site-packages/titanic_model/trained_models/titanic__model_output_v0.0.1.pkl

# Copy the trained model file
# COPY Titanic_Project/titanic_model/trained_models/titanic__model_output_v0.0.1.pkl /usr/local/lib/python3.10/site-packages/titanic_model/trained_models/titanic__model_output_v0.0.1.pkl

# Upgrade PIP
RUN pip install --upgrade pip

# Install the model from the .whl file
RUN pip install Titanic_Project/titanic_model_api/titanic_model-0.0.1-py3-none-any.whl

# Install the dependencies
RUN pip install -r /app/requirements.txt

# Expose the port the app runs on
EXPOSE 8000

# Start the FASTAPI application
CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8000"]
