# Instalación y Configuración de Plataformas Cloud

Este documento explica cómo instalar diferentes plataformas cloud en un servidor web.

## Proceso de instalación

Para instalar una plataforma cloud seguiremos estos pasos:

1. Descargar el código fuente
2. Mover el archivo al directorio raíz del servidor web
3. Descomprimir el contenido en `/var/www/html`
4. Acceder a `http://localhost` y seguir el asistente de instalación

Para más información, consulta la [guía de instalación de aplicaciones web](installacio-aplicacions-web.md).

## Enlaces a las plataformas cloud

* ***OwnCloud***: http://www.owncloud.org
* ***Nextcloud***: http://www.nextcloud.com

## Descargas

### Nextcloud Server
https://download.nextcloud.com/server/releases/latest.zip

### OwnCloud Server
https://download.owncloud.com/server/stable/owncloud-complete-20240724.zip

## Instalación de PHP 7.4 en Ubuntu 24.04

Para instalar OwnCloud necesitaremos PHP 7.4. Sigue estos pasos para instalarlo:

Actualiza las listas de paquetes e instala los prerrequisitos:

```bash
sudo apt install software-properties-common -y
```

Añade el repositorio de PHP:

```bash
LC_ALL=C.UTF-8 sudo add-apt-repository ppa:ondrej/php -y
```

Actualiza los repositorios:

```bash
sudo apt update
```

Instala PHP 7.4:

```bash
sudo apt install php7.4 -y
```

Integra PHP con Apache:

```bash
sudo apt install -y php libapache2-mod-php7.4
```

Instala las extensiones necesarias:

```bash
sudo apt install -y php7.4-fpm php7.4-common php7.4-mbstring php7.4-xmlrpc php7.4-soap php7.4-gd php7.4-xml php7.4-intl php7.4-mysql php7.4-cli php7.4-ldap php7.4-zip php7.4-curl
```

Configura la versión de PHP:

```bash
sudo update-alternatives --config php
```

Activa los módulos de Apache:

```bash
sudo a2enmod proxy_fcgi setenvif
```

```bash
sudo a2enconf php7.4-fpm
```

Reinicia el servidor Apache:

```bash
sudo service apache2 restart
```