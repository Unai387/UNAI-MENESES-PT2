# Manual de Instalación y Configuración de Aplicaciones Web

## Introducción

Este manual describe el proceso completo para instalar y configurar un entorno de servidor web con Apache2 y MySQL, así como la instalación de una aplicación web en dicho entorno. El directorio raíz por defecto de Apache2 es `/var/www/html`, donde deberemos colocar los archivos de nuestra aplicación para acceder a ella mediante `http://localhost`.

## Requisitos Previos

- Acceso a terminal con permisos de administrador
- Conexión a internet para descargar paquetes
- Conocimientos básicos de línea de comandos

## 1. Preparación del Entorno

### 1.1. Actualización del Sistema

Antes de comenzar, actualizamos los repositorios y el sistema:

```bash
sudo apt update
sudo apt upgrade
```

### 1.2. Instalación de Componentes Principales

#### Instalación del Servidor Web Apache2

```bash
sudo apt install -y apache2
```

#### Instalación del Servidor de Base de Datos MySQL

```bash
sudo apt install -y mysql-server
```

#### Instalación de PHP y Módulos Necesarios

```bash
sudo apt install -y php libapache2-mod-php
sudo apt install -y php-fpm php-common php-mbstring php-xmlrpc php-soap php-gd php-xml php-intl php-mysql php-cli php-ldap php-zip php-curl
```

### 1.3. Reinicio del Servidor Apache2

```bash
sudo systemctl restart apache2
```

## 2. Configuración de MySQL

### 2.1. Acceso a la Consola MySQL

```bash
sudo mysql
```

### 2.2. Creación de Base de Datos

Ejecutamos dentro de la consola MySQL:

```sql
CREATE DATABASE bbdd;
```

### 2.3. Creación de Usuario y Asignación de Permisos

```sql
CREATE USER 'usuario'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
GRANT ALL ON bbdd.* to 'usuario'@'localhost';
exit
```

### 2.4. Verificación de la Conexión

Para comprobar que podemos conectar con el usuario creado:

```bash
mysql -u usuario -p
```

## 3. Instalación de la Aplicación Web

### 3.1. Copiado y Descompresión de Archivos

```bash
sudo cp ~/Descargas/app-web.zip /var/www/html
cd /var/www/html
sudo unzip app-web.zip
sudo cp -R app-web/. /var/www/html
sudo rm -rf app-web/
```

### 3.2. Eliminación del Archivo de Bienvenida de Apache2

```bash
sudo rm -rf /var/www/html/index.html
```

### 3.3. Configuración de Permisos

```bash
cd /var/www/html
sudo chmod -R 775 .
sudo chown -R usuario:www-data .
```

## 4. Acceso y Configuración Final

1. Abra su navegador web
2. Ingrese la URL: `http://localhost`
3. Siga el asistente de instalación de la aplicación web
4. Configure con los siguientes datos:
   - **Usuario de BD**: usuario
   - **Contraseña de BD**: password
   - **Nombre de BD**: bbdd
   - **Servidor**: localhost

## Solución de Problemas Comunes

- **Error 403**: Verifique los permisos de los archivos y carpetas
- **Error de conexión a MySQL**: Confirme que el servicio esté activo con `sudo systemctl status mysql`
- **Página en blanco**: Revise los logs de Apache2 en `/var/log/apache2/error.log`

## Recomendaciones de Seguridad

- Cambie las contraseñas predeterminadas
- Limite el acceso remoto solo a IPs necesarias
- Mantenga actualizado regularmente el sistema y aplicaciones
- Considere implementar un firewall como `ufw`
