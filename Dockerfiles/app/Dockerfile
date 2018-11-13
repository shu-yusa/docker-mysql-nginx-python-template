# Use an official Python runtime as a parent image
FROM python:3.7

# Set the working directory to /app
WORKDIR /app

# Copy requirements.txt individually to ensure the cached is used if there's no change in dependent packages
COPY requirements.txt /app

RUN apt-get update && apt-get -y upgrade

# Install any needed packages specified in requirements.txt
RUN pip install --trusted-host pypi.python.org -r requirements.txt

# Copy the current directory contents into the container at the working directory, /app
COPY . /app
RUN echo "alias ls='ls -hp'" >> /root/.bashrc
RUN echo "alias ll='ls -l'" >> /root/.bashrc
RUN echo "alias la='ls -la'" >> /root/.bashrc

# Run app.py when the container launches
# CMD ["waitress-serve", "--port=8000", "--expose-tracebacks", "app:app"]
CMD ["gunicorn", "app:app", "--bind", "unix:/tmp/sockets/gunicorn.sock"]
