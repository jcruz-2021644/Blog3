FROM node:20-alpine AS build
RUN npm install -g pnpm
WORKDIR /app
ARG VITE_API_URL=/blog/v1
ENV VITE_API_URL=$VITE_API_URL

COPY pnpm-lock.yaml pnpm-workspace.yaml package.json ./
COPY Front_Blog/package.json ./Front_Blog/
RUN pnpm install --frozen-lockfile

COPY Front_Blog/ ./Front_Blog/
RUN pnpm --filter frontend build

FROM nginx:1.27-alpine
COPY --from=build /app/Front_Blog/dist /usr/share/nginx/html
COPY Front_Blog/nginx.conf /etc/nginx/conf.d/default.conf
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
