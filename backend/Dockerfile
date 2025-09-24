# Estágio 1: Build da aplicação
FROM node:lts-alpine AS build

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .

RUN npm run build

# Estágio 2: Imagem de produção/desenvolvimento otimizada
FROM node:lts-alpine

WORKDIR /app

# Instala apenas as dependências de produção
COPY package*.json ./
RUN npm install --only=production

# Copia os artefatos do build do estágio anterior
COPY --from=build /app/dist ./dist

# Expõe a porta da aplicação
EXPOSE 3000

# Comando para iniciar a aplicação em modo de desenvolvimento (com watch)
CMD ["npm", "run", "start:dev"]