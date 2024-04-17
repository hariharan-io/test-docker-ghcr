FROM node:20-alpine as base-stage
ENTRYPOINT  ["sh", "-c"]
WORKDIR /app
RUN npm install -g pnpm

FROM base-stage as test-stage
ENV NODE_ENV=test
COPY . .

FROM base-stage as production-stage
ENV NODE_ENV=production
COPY package.json pnpm-lock.yaml ./
RUN pnpm install --frozen-lockfile
COPY . .
CMD ["node", "index.js"]
EXPOSE 3000