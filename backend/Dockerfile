# official Node.js runtime as a parent image
FROM node:14

# working directory 
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy application code
COPY . .
CMD ["npm", "start"]
