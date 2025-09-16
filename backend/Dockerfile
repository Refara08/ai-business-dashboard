FROM node:18-alpine AS builder
WORKDIR /app
COPY package*.json ./
COPY backend/package.json ./backend/
RUN npm install --workspace=backend
COPY . .
RUN npm run build --workspace=backend

FROM node:18-alpine AS runner
WORKDIR /app/backend
COPY --from=builder /app/node_modules /app/node_modules
COPY --from=builder /app/backend/dist ./dist
COPY --from=builder /app/backend/package.json ./
EXPOSE 4000
CMD ["npm", "run", "start:prod"]
