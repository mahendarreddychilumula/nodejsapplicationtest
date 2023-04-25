# Use an official Node.js runtime as a parent image
FROM node:14-alpine

# Set the working directory in the container
WORKDIR /usr/src/app

# Copy the package.json and package-lock.json files to the container
COPY package*.json ./
EXPOSE 3000
# Install dependencies
RUN npm install

# Copy the rest of the application code to the container
COPY . .

# Start the Node.js application
CMD ["npm", "start"]
