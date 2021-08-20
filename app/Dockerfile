# use node official image for this dockerfile
FROM node

# location destination inside the container
WORKDIR /usr/src/app

# in real time project, there will be ENV node_env=dev or prod

COPY ["package.json", "package-lock.json*", "./"]

COPY . .

# RUN is the keyword to run all the commands
RUN npm install -g npm@7.20.6

RUN node seeds/seed.js

# to launch the app

EXPOSE 3000
CMD ["node", "seeds/seed.js"]
CMD ["node", "app.js"]
# it is like node app.js or npm start 
