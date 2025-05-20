# Use Node.js official base image
FROM node:20-alpine

# Set working directory inside container
WORKDIR /app

# Copy package files and install dependencies
COPY package*.json ./
RUN npm install

# Copy project files into container
COPY . .

# Build the Vite project
RUN npm run build

# Expose the app's port (adjust if different)
EXPOSE 5173

# Command to start the server
CMD ["node", "server.js"]
