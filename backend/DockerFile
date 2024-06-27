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

# Copy the environment file
COPY .env .env

# Expose the port the app runs on
EXPOSE 4115

# Command to run the application
CMD ["npm", "start"]
