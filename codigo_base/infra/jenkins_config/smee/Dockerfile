# Contenedor liviano que ejecuta smee-client: reenvía los eventos del
# webhook de GitHub (recibidos en un canal público de smee.io) hacia el
# endpoint /github-webhook/ de Jenkins, sin necesidad de exponer Jenkins
# a Internet.
FROM node:20-alpine

RUN npm install -g smee-client

# TODO: la URL del canal de Smee (creada por usted en https://smee.io) y
# la URL de destino dentro de la red de Docker (el servicio "jenkins" en
# el puerto 8080) se reciben como variables de entorno desde
# docker-compose.yml (SMEE_URL y SMEE_TARGET). No las escriba aquí.

ENTRYPOINT ["sh", "-c", "smee -u \"$SMEE_URL\" -t \"$SMEE_TARGET\""]
