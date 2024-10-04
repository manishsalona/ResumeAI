# Stage 1: Base image to build and develop the Angular application
FROM node:18.10.0 AS build

# Set the working directory
WORKDIR /app

# Copy package.json and package-lock.json to install dependencies
COPY package*.json ./

# Install npm dependencies with legacy-peer-deps flag
RUN npm install --force

# Install Angular CLI globally
RUN npm install -g @angular/cli@14.0.0

# Copy the rest of the project files
COPY . .

# Build the Angular app for production
RUN ng build --configuration production

# Stage 2: Serve the application using Nginx
FROM nginx:alpine

# Copy the production build files from the previous stage to Nginx
# Copy the production build files from the previous stage
COPY --from=build /app/dist/resumebuilder/ /usr/share/nginx/html

# Expose port 80
EXPOSE 80

# Start Nginx
CMD ["nginx", "-g", "daemon off;"]
