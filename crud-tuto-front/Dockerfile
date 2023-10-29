### STAGE 1: BUILD ###
# Use Node.js 16.x
FROM node:16-alpine AS builder

WORKDIR /app
COPY package*.json ./
RUN npm install --force
COPY . .
RUN npm run build --prod

### STAGE 2: RUN ###
FROM nginx:latest AS ngi

# Copy the compiled Angular application from the "builder" stage to the default Nginx public folder
COPY --from=builder /app/dist /usr/share/nginx/html

# Expose port 80 for the web server
EXPOSE 80
