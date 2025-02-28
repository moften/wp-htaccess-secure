# README - Archivo .htaccess para WordPress
# m10sec@proton.me

Este archivo `.htaccess` está diseñado para mejorar la seguridad y el rendimiento de un sitio web basado en WordPress.

## Características

1. **Reescritura de URLs**
   - Permite el uso de enlaces permanentes amigables en WordPress.

2. **Seguridad Adicional**
   - Protección contra ataques XSS, Clickjacking y MIME sniffing.
   - Habilitación de Strict Transport Security (HSTS).
   - Aplicación de una política de seguridad de contenido (CSP).

3. **Protección de Archivos Sensibles**
   - Bloqueo de acceso a `wp-config.php` y `xmlrpc.php`.
   - Restricción de acceso a archivos de configuración y copias de seguridad.

4. **Restricciones en Métodos HTTP**
   - Solo permite métodos `GET`, `POST`, `HEAD` y `OPTIONS`.

5. **Defensa contra Bots y Crawlers Maliciosos**
   - Bloqueo de agentes de usuario sospechosos.

6. **Restricción de Ejecución de PHP en Cargas**
   - Impide la ejecución de archivos PHP dentro de la carpeta `uploads`.

## Instalación
1. Copia el contenido de este archivo en el `.htaccess` de la raíz de tu instalación de WordPress.
2. Asegúrate de que el archivo tenga permisos adecuados (`644` o más seguros según tu configuración de servidor).

## Notas
- Asegúrate de probar el sitio después de aplicar estos cambios para evitar problemas de compatibilidad.
- Modifica las reglas según sea necesario para adaptarlas a tus necesidades específicas.
- Asegurate adaptar tu CSP para evitar errores
