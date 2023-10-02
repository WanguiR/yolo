# Use an official Node.js runtime as a parent image
FROM node:14

# Set the working directory 
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy application code
COPY . .
EXPOSE 3000
CMD ["npm", "start"]
