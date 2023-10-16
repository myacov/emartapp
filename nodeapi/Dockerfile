FROM node:14 AS nodeapi-build
WORKDIR /usr/src/app
COPY ./ ./nodeapi/
RUN cd nodeapi && npm install

FROM node:14
WORKDIR /usr/src/app/
COPY --from=nodeapi-build /usr/src/app/nodeapi/ ./
RUN ls              #List the contents of the current directory (debug purposes)
EXPOSE 5000         #Inform Docker that the container listens on port 5000 at runtime
CMD ["/bin/sh", "-c", "cd /usr/src/app/ && npm start"]          #This navigates to and starts the application

