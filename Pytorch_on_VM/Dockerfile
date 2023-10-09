# Use the official PyTorch image as the base image
FROM --platform=$BUILDPLATFORM pytorch/pytorch:latest AS builder

# Set the working directory in the container
WORKDIR /code

# Copy the requirements file into the container
COPY requirements.txt /code

# Install any needed packages specified in requirements.txt
RUN apt-get update && apt-get install -y curl build-essential
RUN curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y
RUN --mount=type=cache,target=/root/.cache/pip \
    pip install -r requirements.txt

# Copy the current directory contents into the container
COPY . /code

# Define the entry point of the application
ENTRYPOINT ["python3"]
CMD ["app.py"]
