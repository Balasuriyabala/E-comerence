# ---------- Stage 1: Build ----------
FROM node:20-alpine AS build

WORKDIR /app

# Copy only dependency files first
COPY package*.json ./

# Deterministic & secure install
RUN npm ci

# Copy application source
COPY . .

# Build React app
RUN npm run build


# ---------- Stage 2: Runtime ----------
FROM node:20-alpine

WORKDIR /app

# Install serve safely
RUN npm install -g serve@14

# Copy only build output
COPY --from=build /app/build ./build

EXPOSE 3000

CMD ["serve", "-s", "build", "-l", "3000"]
