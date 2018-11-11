FROM homeassistant/amd64-homeassistant-base

ENV LANG C.UTF-8

COPY package.json .

RUN apk add --no-cache jq nodejs nodejs-npm \
	&& npm config set unsafe-perm true \
	&& pwd \
    && npm install -g \
	&& npm config set unsafe-perm false

COPY template.yml /templates/
COPY run.sh /
RUN chmod a+x /run.sh

# We need to percist state, so using data
ENV CONFIG_DIR=/data

CMD [ "/run.sh" ]