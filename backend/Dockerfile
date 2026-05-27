# Use official Node.js LTS image as the base
FROM node:18-alpine

# Set the working directory inside the container
WORKDIR /app

# Copy package files first (for layer caching — avoids re-installing if code changes)
COPY package*.json ./

# Install dependencies
RUN npm install --production

# Copy the rest of the source code
COPY . .

# Expose the port the backend runs on
EXPOSE 3001

# Start the server
CMD ["node", "server.js"]
