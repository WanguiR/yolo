# Use an official lightweight Node.js base image
FROM node:14-alpine

# Set the working directory 
WORKDIR /usr/src/app

COPY package*.json ./

# Install dependencies
RUN npm install

# Copy application code
COPY . .
EXPOSE 8888:80
CMD ["npm", "start"]
