# Usa la imagen base oficial de SQL Server
FROM mcr.microsoft.com/mssql/server:2019-latest

# Establece la variable de entorno para la contraseña del usuario SA
ENV SA_PASSWORD=h4ckm3.2024
ENV ACCEPT_EULA=Y

# Expon el puerto 1433 para permitir conexiones
EXPOSE 1433

# Establece el comando para iniciar SQL Server
CMD [ "/opt/mssql/bin/sqlservr" ]
##docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=h4ckm3.2024' -p 1433:1433 --name sql_server_container -d mcr.microsoft.com/mssql/server:2019-latest
