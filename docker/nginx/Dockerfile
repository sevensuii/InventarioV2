FROM nginx:1.19

ARG UID
EXPOSE $UID

RUN adduser -u ${UID} --disabled-password --gecos '' inventario

COPY default.conf /etc/nginx/conf.d/