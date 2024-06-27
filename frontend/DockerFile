# Use an official Node runtime as a parent image
FROM node:18

# Set the working directory
WORKDIR /usr/src/app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code
COPY . .

# Copy the environment file (if needed)
COPY .env .env

# Expose the port used by the application (if necessary)
EXPOSE 5173

# Command to run the application in development mode
CMD ["npm", "run", "dev"]
