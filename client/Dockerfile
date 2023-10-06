# Use an official Node.js runtime as a parent image
FROM node:14

# Set the working directory 
WORKDIR /usr/src/app

COPY package*.json ./

# Install dependencies
RUN npm install

# Copy application code
COPY . .
EXPOSE 8001:80
CMD ["npm", "start"]
