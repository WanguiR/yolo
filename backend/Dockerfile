# Use an official lightweight Node.js base image
FROM node:14-alpine

# working directory 
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy application code
COPY . .
CMD ["npm", "start"]
