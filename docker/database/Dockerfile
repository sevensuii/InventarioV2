FROM postgres:latest

# Agregar archivo SQL para inicializar la base de datos
#COPY schema.sql /docker-entrypoint-initdb.d/

# Establecer la contraseña de la base de datos
ENV POSTGRES_PASSWORD=${POSTGRES_PASSWORD}

# Establecer la base de datos predeterminada a utilizar
ENV POSTGRES_DB=inventario

# Exponer el puerto 5432
EXPOSE 5432