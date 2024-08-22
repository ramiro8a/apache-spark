# Usar la imagen base de Bitnami Spark
FROM bitnami/spark:latest
USER root
# Establecer el directorio de trabajo
WORKDIR /opt

# Actualizar el sistema e instalar las dependencias necesarias
RUN apt-get clean && apt-get update --fix-missing && apt-get install -y wget bzip2 curl

# Descargar e instalar Anaconda
RUN wget https://repo.anaconda.com/archive/Anaconda3-2023.03-Linux-x86_64.sh -O anaconda.sh \
    && bash anaconda.sh -b -p /opt/anaconda \
    && rm anaconda.sh \
    && /opt/anaconda/bin/conda clean --all --yes

# Limpiar la caché de APT
RUN apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Configurar las variables de entorno para Anaconda
ENV PATH /opt/anaconda/bin:$PATH

# Crear el directorio de trabajo para los notebooks
RUN mkdir /opt/notebooks

# Exponer los puertos necesarios
EXPOSE 8080 7077 8888

# Configurar el comando para iniciar Spark Master y Jupyter Notebook
CMD ["/bin/bash", "-c", "start-spark-master.sh & jupyter notebook --ip=0.0.0.0 --no-browser --allow-root --notebook-dir=/opt/notebooks"]
