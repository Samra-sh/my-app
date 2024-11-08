# Use Node.js LTS as the base image for building
FROM node:16 as build

# Set working directory
WORKDIR /app

# Copy package.json and install dependencies
COPY package*.json ./
RUN npm install

# Copy the rest of the application code and build
COPY . .
RUN npm run build

# Use a lightweight web server for the frontend
FROM nginx:alpine
COPY --from=build /app/build /usr/share/nginx/html

# Expose the frontend port
EXPOSE 80

# Start Nginx
CMD ["nginx", "-g", "daemon off;"]
