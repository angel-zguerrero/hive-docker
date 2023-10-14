FROM --platform=linux/x86_64 node:16
RUN mkdir -p /db
RUN npm install run-rs -g
EXPOSE 27017 27018 27019
 
CMD ["sh", "-c", "run-rs --keep --portStart 27017 --dbpath /db --host ${HOST_NAME}"]