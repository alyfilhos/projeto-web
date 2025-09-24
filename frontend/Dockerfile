# Estágio 1: Build da aplicação
FROM node:lts-alpine AS build

WORKDIR /app

# Copia os arquivos de manifesto de pacotes e instala as dependências
COPY package*.json ./
RUN npm install

# Copia o restante do código-fonte
COPY . .

# Comando para build (se necessário para produção, mas útil para verificação)
# Para desenvolvimento com Vite, o servidor de dev é mais comum.
# RUN npm run build

# Estágio 2: Servidor de desenvolvimento
FROM node:lts-alpine

WORKDIR /app

# Copia as dependências instaladas do estágio anterior
COPY --from=build /app/node_modules ./node_modules
COPY --from=build /app ./

# Expõe a porta do Vite
EXPOSE 5173

# Inicia o servidor de desenvolvimento do Vite
CMD ["npm", "run", "dev", "--", "--host", "0.0.0.0"]