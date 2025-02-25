# DockerImageGdalJupyter
Imagen de Docker con Gdal y Jupyter Notebook
##crear contenedor espacial

#descargar la imagen con gdal
docker pull ghcr.io/osgeo/gdal:ubuntu-full-latest
#crear el contenedor con el volumen de la carpeta
docker run -it --rm -v "C:/Users/rvargco/OneDrive - Emtelco/Archivos pc/Proyectos_espaciales:/mnt/proyectos" ghcr.io/osgeo/gdal:ubuntu-full-latest
#instalar pip y sudo dentro del contenedor
apt-get update 
apt-get -y install python3-pip --fix-missing
apt-get update && apt-get install -y sudo
apt-get install nano


##instalar paquetes faltantes
pip install geopandas rioxarray pystac-client pandas numpy --break-system-packages
pip install jupyter --break-system-packages


#para uniciar el contenedor
docker run -it --rm -v "C:/Users/rvargco/OneDrive - Emtelco/Archivos pc/Proyectos_espaciales:/mnt/proyectos" -p 8888:8888 ghcr.io/osgeo/gdal:ubuntu-full-latest


##para usar el contenedor
docker run -it --rm -v "C:/Users/rvargco/OneDrive - Emtelco/Archivos pc/Proyectos_espaciales:/mnt/proyectos" -p 8888:8888 gdal-with-jupyter:latest

jupyter notebook --ip=0.0.0.0 --no-browser --allow-root
