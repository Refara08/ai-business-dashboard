FROM node:18-alpine AS builder
WORKDIR /app
COPY package*.json ./
COPY frontend/package.json ./frontend/
RUN npm install --workspace=frontend
COPY . .
RUN npm run build --workspace=frontend

FROM node:18-alpine AS runner
WORKDIR /app/frontend
COPY --from=builder /app/node_modules /app/node_modules
COPY --from=builder /app/frontend/.next ./.next
COPY --from=builder /app/frontend/package.json ./ 
COPY --from=builder /app/frontend/public ./public
EXPOSE 3000
CMD ["npm", "run", "start"]
