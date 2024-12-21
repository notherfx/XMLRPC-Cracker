# XML-RPC Password Cracker

Este script en Bash permite realizar ataques de fuerza bruta a un endpoint XML-RPC de WordPress para intentar descubrir la contraseña del usuario `admin`. Usa la lista de contraseñas `rockyou.txt` como fuente de posibles claves.

## Características
- Realiza peticiones XML-RPC al endpoint `wp.getUsersBlogs`.
- Detecta si una contraseña es correcta basándose en la respuesta del servidor.
- Maneja interrupciones con `Ctrl+C` de manera grácil.

## Requisitos previos
- Tener instalado `curl`.
- Contar con la lista de contraseñas `rockyou.txt`. Puedes descargarla desde [SecLists](https://github.com/danielmiessler/SecLists).
- Acceso a un endpoint `xmlrpc.php` de WordPress.

## Uso
1. Clona este repositorio:
   ```bash
   git clone <URL-del-repositorio>
   cd <nombre-del-repositorio>
   ```

2. Asegúrate de que el script tenga permisos de ejecución:
   ```bash
   chmod +x script.sh
   ```

3. Ejecuta el script:
   ```bash
   ./script.sh
   ```
   Nota: Este script busca la lista `rockyou.txt` en el directorio `/usr/share/wordlists/`. Asegúrate de que el archivo esté en esa ubicación.

4. Si conoces un nombre de usuario diferente a `admin`, puedes modificar el script para reemplazar `admin` por el nombre de usuario deseado.

5. Cambia `https://url/xmlrpc.php` por la URL del sitio WordPress que deseas auditar.

## Cómo funciona
1. El script lee cada línea de la lista de contraseñas `rockyou.txt`.
2. Por cada contraseña:
   - Crea un archivo XML (`file.xml`) con el intento de inicio de sesión.
   - Envía el archivo al endpoint `https://url/xmlrpc.php` usando `curl`.
   - Analiza la respuesta para determinar si la contraseña es correcta.
3. Si encuentra la contraseña correcta, la muestra en pantalla y termina la ejecución.
4. Si el usuario presiona `Ctrl+C`, el script termina con un mensaje de salida.

## Advertencia
Este script debe utilizarse únicamente para fines educativos o con el permiso explícito del propietario del sitio web. El uso indebido puede violar leyes locales y provocar consecuencias legales.

## Contribuciones
Si tienes sugerencias para mejorar el script, no dudes en abrir un *pull request* o enviar un *issue*.

## Licencia
Este proyecto está bajo la licencia MIT. Consulta el archivo `LICENSE` para más información.
