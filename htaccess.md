# BEGIN WordPress
<IfModule mod_rewrite.c>
RewriteEngine On
RewriteBase /
RewriteRule ^index\.php$ - [L]
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . /index.php [L]
</IfModule>
# END WordPress

# Seguridad adicional
<IfModule mod_headers.c>
    Header set X-XSS-Protection "1; mode=block"
    Header set X-Content-Type-Options "nosniff"
    Header set X-Frame-Options "SAMEORIGIN"
    Header always set Strict-Transport-Security "max-age=31536000; includeSubDomains; preload"
    Header set Referrer-Policy "no-referrer-when-downgrade"
    Header set Content-Security-Policy "default-src 'self'; script-src 'self' 'unsafe-inline' 'unsafe-eval'; style-src 'self' 'unsafe-inline'; img-src 'self' data:; font-src 'self' data:;"
</IfModule>

# Protección de archivos sensibles
<Files wp-config.php>
    order allow,deny
    deny from all
</Files>

<Files xmlrpc.php>
    order allow,deny
    deny from all
</Files>

# Deshabilitar listado de directorios
Options -Indexes

# Bloquear acceso a archivos de configuración y copias de seguridad
<FilesMatch "\.(bak|conf|sql|swp|old|log|htpasswd|ini|sh|inc|phps|cgi|out|env)$">
    Order allow,deny
    Deny from all
</FilesMatch>

# Limitar métodos HTTP permitidos
<IfModule mod_rewrite.c>
    RewriteCond %{REQUEST_METHOD} !^(GET|POST|HEAD|OPTIONS)$
    RewriteRule .* - [R=405,L]
</IfModule>

# Protección contra bots maliciosos y spam
<IfModule mod_rewrite.c>
    RewriteCond %{HTTP_USER_AGENT} ^.*(bot|crawl|slurp|spider).*$ [NC]
    RewriteRule .* - [F,L]
</IfModule>

# Bloquear ejecución de archivos PHP en uploads
<Directory "wp-content/uploads">
    <FilesMatch "\.php$">
        Order allow,deny
        Deny from all
    </FilesMatch>
</Directory>
