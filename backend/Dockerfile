# Development Dockerfile for Medusa
FROM node:20-alpine

# Set working directory
WORKDIR /backend

# Copy package manager files (use Yarn, not npm)
COPY package.json yarn.lock ./

# Enable Corepack and use Yarn 4 (matches package.json: "packageManager": "yarn@4.4.0")
RUN corepack enable \
  && corepack prepare yarn@4.4.0 --activate \
  && yarn --version \
  && yarn install --immutable

# Copy source code
COPY . .

# Ensure start script is executable
RUN chmod +x start.sh

# Expose the port Medusa runs on
EXPOSE 9000

# Start with migrations and then the development server
CMD ["./start.sh"]