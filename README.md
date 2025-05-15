# UNAI-MENESES-PT2
# Instalación y Configuración de ownCloud mediante IsardVDI

## Descripción del proyecto

Este proyecto consiste en la instalación y configuración de **ownCloud** utilizando **IsardVDI**. Se ha detallado el proceso de instalación en un entorno controlado, así como la configuración de los usuarios, roles, permisos y administración de archivos dentro de la plataforma.

El objetivo principal es proporcionar una guía paso a paso para la instalación, configuración y gestión de ownCloud. Esto permite una gestión eficiente de los archivos y la asignación de permisos de forma sencilla y segura.

## Dificultades encontradas

Durante la instalación de ownCloud, surgieron algunos contratiempos que fue necesario resolver:

- **Problemas de conexión con la base de datos MySQL/MariaDB**: Al principio, ownCloud no conseguía conectar con la base de datos debido a un error en el nombre del host. Se solucionó modificando la configuración y asegurándose de que el servicio estuviera activo.
  
- **Permisos de escritura en el directorio de datos**: El instalador de ownCloud detectó que no tenía permisos para escribir en el directorio de almacenamiento. Esto se resolvió ajustando los permisos con `chown` y `chmod`.

- **Advertencias sobre módulos PHP faltantes**: Durante la instalación, el sistema notificó que faltaban algunas extensiones PHP necesarias (como `php-gd` y `php-mbstring`). Fue necesario instalarlas manualmente con el gestor de paquetes.

Estos problemas fueron útiles para afianzar el conocimiento sobre la configuración del servidor web y la infraestructura de ownCloud.

## Enlaces a los otros archivos

A continuación se muestran los enlaces a los archivos más detallados para la instalación y configuración:

- [Manual de Instalación de ownCloud con IsardVDI (INSTALLATION.md)](INSTALLATION.md): Este documento explica todos los pasos para instalar y configurar **ownCloud** mediante **IsardVDI**, incluyendo capturas de pantalla para cada paso.
  
- [Manual de Configuración de ownCloud (CONFIGURATION.md)](CONFIGURATION.md): Aquí se detallan los pasos necesarios para configurar usuarios, roles, permisos y la administración de archivos dentro de ownCloud.

---

**Autor:** Unai Meneses Pulido
