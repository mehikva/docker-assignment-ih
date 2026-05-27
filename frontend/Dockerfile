# ---- Build Stage ----
FROM node:18-alpine AS build

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .

# Build the React app into static files
RUN npm run build

# ---- Production Stage ----
# Use nginx to serve the static files
FROM nginx:alpine

# Copy the built React app into nginx's web root
COPY --from=build /app/build /usr/share/nginx/html

# Expose port 80 (nginx default)
EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
