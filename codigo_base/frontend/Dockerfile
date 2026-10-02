# Stage 1: build
FROM node:20.11.1-alpine AS builder
WORKDIR /build
COPY package*.json ./
RUN npm install
ARG VITE_API_URL
ENV VITE_API_URL=$VITE_API_URL
COPY . .
RUN npm run build

# Stage 2: nginx runtime
FROM nginx:1.27-alpine AS runtime
COPY --from=builder /build/dist /usr/share/nginx/html
COPY nginx.conf /etc/nginx/conf.d/default.conf
EXPOSE 3000
