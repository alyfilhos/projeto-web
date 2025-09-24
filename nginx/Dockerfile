# Utiliza a imagem base do Nginx com Alpine Linux
FROM nginx:alpine

# Remove a configuração padrão do Nginx
RUN rm /etc/nginx/conf.d/default.conf

# Copia o arquivo de configuração customizado para o contêiner
COPY nginx.conf /etc/nginx/conf.d