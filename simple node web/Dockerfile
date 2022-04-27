# to install the base image
FROM node:alpine

# copy the dependency file
COPY ./ ./
RUN npm install

# start the npm server
CMD ["npm", "start"]