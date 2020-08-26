FROM node:6-alpine

ENV HOME=/home/app

WORKDIR ${HOME}

#RUN echo -e 'https://repository.walmart.com/content/repositories/alpine-v38/community\nhttps://repository.walmart.com/content/repositories/alpine-v38/main' > /etc/apk/repositories && rm -rf /var/cache/apk/* && rm -rf /tmp/*  && apk --update add --no-cache apk-tools tini
#RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/g' /etc/apk/repositories && rm -rf /var/cache/apk/* && rm -rf /tmp/*  && apk --update add --no-cache apk-tools tini
RUN rm -rf /var/cache/apk/* && rm -rf /tmp/*  && apk --update add --no-cache apk-tools tini
ADD package.json ${HOME}/
ADD config/production.json ${HOME}/config/production.json
#RUN echo 'registry=https://registry.npm.taobao.org/' > ${HOME}/.npmrc

RUN npm install --production
ENTRYPOINT [ "/sbin/tini", "--" ]

EXPOSE 9001
VOLUME ${HOME}/config
CMD ["npm", "run", "start"]