# Use a specific Node.js version
FROM node:14.17.0

# Set working directory
WORKDIR /app

# Copy package files separately to leverage Docker cache
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the source code
COPY . .

# Expose the port React runs on
EXPOSE 3000

# Start the application
CMD ["npm", "start"]
