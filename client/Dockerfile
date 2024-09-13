# Stage 1: Build the React app using Vite
FROM node:16 AS build

# Set working directory
WORKDIR /app

# Copy package files and install dependencies
COPY package*.json ./
RUN npm install

# Copy the rest of the application code
COPY . .

# Build the React app using Vite
RUN npm run build

# Check contents of /app to verify the build directory
RUN ls -la /app/dist

# Stage 2: Serve the React app with Nginx
FROM nginx:alpine

# Copy the build files from the first stage
COPY --from=build /app/dist /usr/share/nginx/html

# Expose port 80
EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
