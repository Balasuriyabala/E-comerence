FROM node:20 AS build 

WORKDIR /app 

COPY package*.json ./ 

# Deterministic install
RUN npm ci
# Copy application source explicitly
COPY src ./src
COPY public ./public

#RUN npm install 
#COPY . . 
#RUN npm run build 

# Stage 2: Minimal Node.js runtime to serve static files 
FROM node:20-alpine 

WORKDIR /app 

# Install serve (tiny package) 

RUN npm install -g serve 

# Copy only the build output

COPY --from=build /app/build.

EXPOSE 3000

# Serve the React app 
CMD ["serve", "-s", "build", "-l", "3000"]
