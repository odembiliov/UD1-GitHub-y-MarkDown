# Como instalar el servidor web Apache en Ubuntu
## Instalar Apache
El primer paso que debemos realizar será abrir el terminal de ubuntu para a continuación empezar con los comandos para la instalación.  
**Importante** -> Actualizar
```
sudo apt update
```
Una vez ha terminado de actualizarse podemos empezar la instalación
```
sudo apt install apache
```
## Ajustar el firewall
Antes de empzar con Apache será necesario modificar los ajustes de firewall para permitir el acceso externo a los puertos web predeterminados
```
sudo ufw app list
```
Habilitaremos el tráfico en el puerto 80 (Apache) y activaremos el cortafuegos y verificaremos que el cambio se haya realizado
```
sudo ufw allow 'Apache'
sudo ufw enable
sudo ufw status
```
##Comprobar su servidor web
En este paso el servidor web ya estara activo.  
Vamos a realizar una verificación con el sistema `systemd` para saber si se encuentra en ejecución el servicio.  
```
sudo systemctl status apache2
```
Si el sistema te indicara que esta incativo, realizar el siguiente comando;
```
sudo systemctl start apache2
```
Una vez comprobamos que el servicio esta en ejecución, para conocer la dirección IP de nuestro servidor introduciremos el siguiente comando y desde nuestro navegador verificaremos que podemos acceder a la página predeterminada de Apache
```
hostname -I
http://_yourServerIP_
```
##Administrar el proceso de Apache
**Detener el servidor**
```
sudo systemctl stop apache2
```
**Iniciar servidor**
```
sudo systemctl start apache2
```
**Reiniciar el servidor**
```
sudo systemctl restart apache2
```
**Recargar sin cerrar las conexiones**
```
sudo systemctl reload apache2
```
**Deshabilitar Apache para que no se inicie automaticamente**
```
sudo systemctl disable apache2
```
**Habilitar el servicio para que se cargue en el inicio**
```
sudo systemctl enable apache2
```