# Step 1: Build the React app
FROM node:18 AS builder

# Set working directory
WORKDIR /app

# Install dependencies
COPY package.json package-lock.json ./
RUN npm install

# Copy all files
COPY . .
# Build the app
RUN npm run build

# Step 2: Serve the app with an Nginx server
FROM nginx:alpine

# Copy built React app to Nginx's web directory
COPY --from=builder /app/build /usr/share/nginx/html

# Expose port 80
EXPOSE 80

# Start Nginx server
CMD ["nginx", "-g", "daemon off;"]