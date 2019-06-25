FROM node:latest

# define my environment variable
ENV APP_PORT=5000 APP_DIR=/fortune

# create WORKDIR and cd inside
WORKDIR ${APP_DIR}

# copy files to APP_DIR
ADD main.js .
ADD package.json .
# directories must have a target name
ADD public public
ADD views views

# install libraries from package.json
RUN npm install


## docker run
EXPOSE ${APP_PORT}

HEALTHCHECK --interval=60s --timeout=5s --retries=3 \
    CMD curl -f -s http://localhost:${APP_PORT}/health || exit 1

# how should the image be executed (fixed for the image)
ENTRYPOINT [ "node", "main.js" ]

# CMD["3000"] // as an option to ENTRYPOINT
