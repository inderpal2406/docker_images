# Specifying a base image
FROM alpine

# Specify a working directory
WORKDIR /usr/app

# Install dependencies
COPY ./package.json .
RUN apk add npm
RUN npm install
COPY . .

# Default command
CMD ["npm", "start"]
