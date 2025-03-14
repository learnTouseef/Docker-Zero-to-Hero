# Get the latest ubuntu base-img for our docker container
FROM ubuntu:latest

# Set the working directory in the image
WORKDIR /app

# Copy the files from the host file system to the image file system --> i.e. copy everything from 'first-docker-file' dir to the '/app' dir which is our work dir. So all the cmds/actions are exe in /app dir
COPY . /app

# Install the necessary packages/ dependencies to run our app
RUN apt-get update && apt-get install -y python3 python3-pip

# Set environment variables
ENV NAME World

# Run command to start the application
CMD ["python3", "app.py"]
