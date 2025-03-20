
# Stage 1: Build the React application
FROM node:17 AS build

# Set the working directory inside the container
WORKDIR /app

# Copy package.json and package-lock.json files
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code
COPY . .

# Build the application
RUN npm run build

# Stage 2: Use a smaller Node.js image to serve the app
FROM node:alpine

# Install serve globally
RUN npm install -g serve

# Set the working directory
WORKDIR /app

# Copy only the built files from the previous stage
COPY --from=build /app/build .

# Expose port 3000
EXPOSE 3000

# Run the application using 'serve'
CMD ["serve", "-s", ".", "-l", "3000"]
