# Use the official Python image from the Docker Hub
FROM python:3.10

# Set the working directory
WORKDIR /app

# Copy application files to the container
COPY . /app

# Copy config file
COPY Titanic_Project/titanic_model/config.yml /usr/local/lib/python3.10/site-packages/titanic_model/config.yml

# Copy the trained model file
COPY Titanic_Project/titanic_model/trained_models/titanic__model_output_v0.0.1.pkl /usr/local/lib/python3.10/site-packages/titanic_model/trained_models/titanic__model_output_v0.0.1.pkl

# Upgrade PIP
RUN pip install --upgrade pip

# Install the model from the .whl file
RUN pip install Titanic_Project/dist/titanic_model-0.0.1-py3-none-any.whl

# Install the dependencies
RUN pip install -r Titanic_Project/requirements/requirements.txt

# Expose the port the app runs on
EXPOSE 8000

# Start the FASTAPI application
CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8000"]
