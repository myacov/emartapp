FROM node:14 AS web-build
WORKDIR /usr/src/app
COPY ./ ./client

#install the npm packages, and run the production build
RUN cd client && npm install && npm run build --prod



# Start a new build stage using the official nginx image as the base
FROM nginx:latest

# Copy the built output from the 'web-build' stage to replace the default nginx contents
COPY --from=web-build /usr/src/app/client/dist/client/ /usr/share/nginx/html
# Copy our custom nginx configuration into the default nginx configuration location
COPY nginx.conf /etc/nginx/conf.d/default.conf

# Inform Docker that the container listens on the specified network port at runtime
EXPOSE 4200
