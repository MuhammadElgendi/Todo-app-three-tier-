# FROM node:14-alpine

# WORKDIR /app

# # add '/app/node_modules/.bin' to $PATH
# ENV PATH /app/node_modules/.bin:$PATH
# # install application dependencies
# COPY package*.json ./
# RUN npm install
# # RUN npm install react-scripts -g

# # copy app files
# COPY . .

# EXPOSE 3000
# # CMD ["npm", "run ","build"]
# RUN npm run build
# # Stage 2: Serve the application with Nginx
# FROM nginx:alpine
# COPY --from=build /app/ /usr/share/nginx/html
# EXPOSE 80
# CMD ["nginx", "-g", "daemon off;"]




# Stage 1: Build the application
FROM node:14-alpine as build

WORKDIR /app

# Add '/app/node_modules/.bin' to $PATH
ENV PATH /app/node_modules/.bin:$PATH

# Install application dependencies
COPY package*.json ./
RUN npm install

# Copy app files
COPY . .

# Build the application
RUN npm run build

# Stage 2: Serve the application with Nginx
FROM nginx:alpine

# Copy built files from the 'build' stage
COPY --from=build /app /usr/share/nginx/html

# Expose port 80
EXPOSE 80

# Start Nginx server
CMD ["nginx", "-g", "daemon off;"]
