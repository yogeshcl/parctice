# Base stage for building dependencies
FROM node:18-alpine AS deps
WORKDIR /app
COPY package*.json ./
RUN npm install --only=production

# Base image for running the application
FROM node:18-alpine
WORKDIR /app

# Copy only production dependencies and source files
COPY --from=deps /app/node_modules ./node_modules
COPY appointment-service.js ./

# Set environment variables
ENV NODE_ENV=production
ENV PORT=3000

# Expose the application port
EXPOSE ${PORT}

# Run the application
CMD ["node", "appointment-service.js"]
