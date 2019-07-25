# Use an official python runtime as a parent
FROM python:2.7-slim

# Set the working dir to /app
WORKDIR /app

# Copy the contents of current directory to the /app directory in the container
COPY . /app

# Install any needed packages specified in requirements.txt (This requirements.txt has already been copied to the container with above COPY)
RUN pip install --trusted-host pypi.python.org -r requirements.txt

# Make port 80 available to the world outside this container
EXPOSE 80

# To define environment variables inside the container
ENV NAME World

# Run app.py when the container launches
CMD ["python", "app.py"]
