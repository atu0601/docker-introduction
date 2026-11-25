FROM node:18-alpine

RUN addgroup -S appgroup && adduser -S appuser -G appgroup

RUN npm install -g serve

WORKDIR /app

RUN chown appuser:appgroup /app

USER appuser

COPY package.json package-lock.json ./

RUN npm ci

COPY . ./

RUN npm run build

EXPOSE 3000

CMD ["serve", "-s", "dist", "-l", "3000"]