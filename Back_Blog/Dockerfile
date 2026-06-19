FROM node:20-alpine
RUN npm install -g pnpm
WORKDIR /app

COPY pnpm-lock.yaml pnpm-workspace.yaml package.json ./
COPY Back_Blog/package.json ./Back_Blog/
RUN pnpm install --frozen-lockfile

COPY Back_Blog/ ./Back_Blog/

EXPOSE 3000
CMD ["node", "Back_Blog/app.js"]
