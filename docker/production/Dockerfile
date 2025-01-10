# First Stage: Build the App
FROM node:22.11.0 AS builder

WORKDIR /app

COPY package*.json .

# Install dependencies
RUN npm install

COPY . .

# Build the application
RUN npm run build

# Second Stage: Setup the runtime
FROM node:22.11.0 AS runtime

WORKDIR /app

COPY --from=builder /app/build /app
COPY package*.json .

# Define build arguments for secrets
ARG DB_USER
ARG DB_PASSWORD
ARG MAILJET_API_SECRET_KEY
ARG MAILJET_API_KEY
ARG HEALTH

# Set environment variables
ENV FRONTEND_APP_BASE_URL="https://example.flapi.org" \
    API_USER_TOKEN_EXPIRATION="1 days" \
    API_USER_TOKEN_SECRET_LENGTH=128 \
    HASH_DRIVER=argon \
    TZ=UTC \
    PORT=3333 \
    HOST=0.0.0.0 \
    LOG_LEVEL=error  \
    APP_KEY=VyNbUsi5FgpKrhVz-MMWJfe0nH0KnRZC \
    NODE_ENV=production \
    DB_HOST=109.234.165.225 \
    DB_PORT=3306 \
    DB_USER=${DB_USER} \
    DB_PASSWORD=${DB_PASSWORD} \
    DB_DATABASE_NAME=reco5282_customerName-projectName_production \
    DB_DEBUG=false \
    HEALTH=${HEALTH} \
    MAILJET_API_SECRET_KEY=${MAILJET_API_SECRET_KEY} \
    MAILJET_API_KEY=${MAILJET_API_KEY} \
    MAIJET_API_VERSION=3.1 \
    SMTP_HOST=none \
    SMTP_PORT=1025 \
    SMTP_USERNAME=none \
    SMTP_PASSWORD=none \
    MAIL_USERNAME=support@flapi.org

# Install production dependencies only
RUN npm ci --omit="dev" --ignore-scripts

CMD npm run db:migration:staging-prod && \
    npm run db:seed && \
    npm run start
