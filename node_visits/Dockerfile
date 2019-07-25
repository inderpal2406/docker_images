# Specify base image
FROM node:alpine

# Set up work directory
WORKDIR '/usr/app'

# Copy package.json
COPY ./package.json ./

# Install dependencies
RUN npm install

# Copy rest of the code
COPY . .

# Set the default command
CMD ["npm", "start"]
