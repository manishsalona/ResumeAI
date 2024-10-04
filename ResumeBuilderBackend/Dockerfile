# Use Node.js base image
FROM node:18.10.0

# Set working directory inside the container
WORKDIR /app

# Copy package files and install npm dependencies
COPY package*.json ./
RUN npm install --force

# Install dependencies for Puppeteer
RUN apt-get update && \
    apt-get install -y \
    ca-certificates \
    fonts-liberation \
    libappindicator3-1 \
    libasound2 \
    libatk-bridge2.0-0 \
    libatk1.0-0 \
    libc6 \
    libcairo2 \
    libcups2 \
    libdbus-1-3 \
    libexpat1 \
    libfontconfig1 \
    libgbm1 \
    libgcc1 \
    libglib2.0-0 \
    libgtk-3-0 \
    libnspr4 \
    libnss3 \
    libpango-1.0-0 \
    libpangocairo-1.0-0 \
    libstdc++6 \
    libx11-6 \
    libx11-xcb1 \
    libxcb1 \
    libxcomposite1 \
    libxcursor1 \
    libxdamage1 \
    libxext6 \
    libxfixes3 \
    libxi6 \
    libxrandr2 \
    libxrender1 \
    libxss1 \
    libxtst6 \
    lsb-release \
    wget \
    xdg-utils \
    --no-install-recommends && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

# Copy the rest of the application code
COPY . .

# Install TypeScript globally
RUN npm install -g typescript

# Compile TypeScript code (if necessary)
RUN npx tsc

# Set environment variables
#ENV JWT_SECRET_KEY="MYREALLYSECRETKEY"
#ENV MONGO_URL="mongodb://resumeai-mongodb-1:27017/myDatabase"
#ENV OPENAI_KEY="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"
#ENV GMAIL_USER="salonamanish@gmail.com"
#ENV GMAIL_PASS="mrinali#1993"
#ENV FRONT_END="http://localhost:80"

# Expose the port your app runs on
EXPOSE 4292

# Start the application
CMD ["npm", "start"]
