# Build stage
FROM node:18-alpine as builder
WORKDIR /app
COPY package*.json ./
RUN npm install --only=production
COPY . .

# Runtime Stage
FROM node:18-alpine
ENV NODE_ENV=production
ENV PORT=3100
WORKDIR /app
COPY --from=builder /app .
EXPOSE ${PORT}
CMD ["node", "appointment-service.js"]