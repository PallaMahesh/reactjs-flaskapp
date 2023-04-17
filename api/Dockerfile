# api/Dockerfile

# Use an official Python Alpine base image
FROM python:3.9-alpine

# Set the working directory in the container
WORKDIR /app

# Copy the backend files into the container
COPY . .

# Install dependencies using Alpine package manager
RUN apk add --no-cache gcc musl-dev \
    && apk add --no-cache python3-dev \
    && apk add --no-cache postgresql-dev \
    && apk add --no-cache linux-headers \
    && apk add --no-cache py3-psutil \
    && pip install --upgrade pip \
    && pip install --no-cache-dir -r requirements.txt \
    && apk del gcc musl-dev python3-dev postgresql-dev

# Expose the backend server port
EXPOSE 5000

CMD ["gunicorn", "app:app", "-b", "0.0.0.0:5000"]