
## for building
FROM node:latest

ENV DB_HOST=nwdb \
    DB_PORT=3306 \
    DB_USER=root \
    DB_PASSWORD=changeit \
    APP_DIR=/app \
    APP_PORT=3000


WORKDIR ${APP_DIR}

# add files
ADD main.js .
ADD package.json .

# add directories
ADD public public
ADD views views
ADD config config

RUN npm install

## run
EXPOSE ${APP_PORT}

HEALTHCHECK --interval=30s --timeout=30s --retries=3 \
    CMD curl -f -s http://localhost:${APP_PORT}/health || exit 1


ENTRYPOINT [ "node", "main.js" ]

CMD [ "" ]
