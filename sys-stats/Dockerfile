# sys-stats/Dockerfile

# Use an official Node.js base image
FROM node:16-alpine as build

# Set the working directory in the container
WORKDIR /app

# Copy the package.json and package-lock.json files into the container
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the frontend application code to the container
COPY . /app

# Build the frontend app
RUN npm run build

# Use a smaller nginx base image for serving the static files
FROM nginx:1.19-alpine

# Copy the built frontend app from the previous stage to the Nginx default HTML directory
COPY --from=build /app/build /usr/share/nginx/html

# Copy the Nginx configuration file to the container
COPY ./nginx/nginx.conf /etc/nginx/nginx.conf

# Expose the port that Nginx will run on
EXPOSE 80

# Start Nginx
CMD ["nginx", "-g", "daemon off;"]