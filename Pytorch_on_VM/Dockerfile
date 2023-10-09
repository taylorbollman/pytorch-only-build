# Use the official PyTorch image as the base image
FROM pytorch/pytorch:latest

# Set the working directory in the container
WORKDIR /code

# Update apt-get and install needed tools
RUN apt-get update && apt-get install -y build-essential

# Copy the requirements file into the container
COPY requirements.txt /code

# Install any needed packages specified in requirements.txt
RUN pip install --no-cache-dir -r requirements.txt

# Copy the current directory contents into the container
COPY . /code

# Define the entry point of the application
ENTRYPOINT python3 app.py; tail -f /dev/null
