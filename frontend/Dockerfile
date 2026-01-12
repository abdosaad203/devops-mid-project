FROM node:18

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .

# مهم جدًا
ARG VITE_API_BASE_URL
ENV VITE_API_BASE_URL=$VITE_API_BASE_URL

RUN npm run build

EXPOSE 4200
CMD ["npm", "run", "preview", "--", "--host", "0.0.0.0", "--port", "4200"]
