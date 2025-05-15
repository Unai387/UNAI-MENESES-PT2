# Configuración e Instalación de Plataformas Cloud

En este documento explicamos cómo instalar diferentes plataformas cloud en nuestro servidor.

## Requisitos previos

- Servidor web Apache
- Ubuntu 24.04
- Permisos de administrador

## Proceso general

Para instalar una plataforma cloud debemos seguir estos pasos:

1. Descargar el código fuente
2. Mover el archivo al directorio raíz del servidor web
3. Descomprimir el contenido en `/var/www/html`
4. Acceder a `http://localhost` y seguir el asistente de instalación

Para más detalles, consulta el [manual de instalación de aplicaciones web](installacio-aplicacions-web.md).

## Plataformas disponibles

### Nextcloud

- **Web oficial**: http://www.nextcloud.com
- **Archivo de instalación**: https://download.nextcloud.com/server/releases/latest.zip

### OwnCloud

- **Web oficial**: http://www.owncloud.org
- **Archivo de instalación**: https://download.owncloud.com/server/stable/owncloud-complete-20240724.zip

## Configuración de PHP 7.4 en Ubuntu 24.04

OwnCloud requiere PHP 7.4. Sigue estos comandos para instalarlo:

### 1. Preparación del sistema

```bash
# Instalar prerrequisitos
sudo apt install software-properties-common -y

# Añadir repositorio de PHP
LC_ALL=C.UTF-8 sudo add-apt-repository ppa:ondrej/php -y

# Actualizar repositorios
sudo apt update
```

### 2. Instalación de PHP y módulos

```bash
# Instalar PHP 7.4 base
sudo apt install php7.4 -y

# Integrar con Apache
sudo apt install -y php libapache2-mod-php7.4

# Instalar extensiones necesarias
sudo apt install -y php7.4-fpm php7.4-common php7.4-mbstring php7.4-xmlrpc php7.4-soap php7.4-gd php7.4-xml php7.4-intl php7.4-mysql php7.4-cli php7.4-ldap php7.4-zip php7.4-curl
```

### 3. Configuración final

```bash
# Seleccionar versión de PHP
sudo update-alternatives --config php

# Activar módulos de Apache
sudo a2enmod proxy_fcgi setenvif
sudo a2enconf php7.4-fpm

# Reiniciar Apache
sudo service apache2 restart
```