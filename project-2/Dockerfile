# Use Node.js base image
FROM node:20-alpine

# Set working directory
WORKDIR /app

# Copy dependencies
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy app source
COPY . .

# Expose Vite default port
EXPOSE 5173

# Start Vite dev server
CMD ["npm", "run", "dev"]
