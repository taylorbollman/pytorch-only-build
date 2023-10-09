# Use the official PyTorch image as the base image
FROM --platform=$BUILDPLATFORM pytorch/pytorch:latest AS builder

# Set the working directory in the container
WORKDIR /code

# Update apt-get and install needed tools
RUN apt-get update && apt-get install -y curl build-essential

# Install and set a specific Rust version
RUN curl https://sh.rustup.rs -sSf | sh -s -- -y
RUN /bin/bash -c "source $HOME/.cargo/env && rustup install 1.53.0 && rustup default 1.53.0 && rustup update"

# Update the PATH to include .cargo/bin
ENV PATH="/root/.cargo/bin:${PATH}"

# Copy the requirements file into the container
COPY requirements.txt /code

# Install any needed packages specified in requirements.txt
RUN --mount=type=cache,target=/root/.cache/pip \
    pip install -v -r requirements.txt  # Added the -v flag for verbose logging

# Copy the current directory contents into the container
COPY . /code

# Define the entry point of the application
ENTRYPOINT ["python3"]
CMD ["app.py"]
