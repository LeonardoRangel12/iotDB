# iotDB
Este proyecto fue creado para hacer una infraestructura completa de IoT para maquinas virtuales.
Si quieren hacer cambios, pueden crear su propio repositorio con un fork y de ahí hacer sus cambios (esta es una plantilla)
## Como instalar
<strong>ESTAR EN USUARIO ROOT AL EMPEZAR</strong>
```BASH
sudo su
```
Primero se tiene que utilizar un sistema operativo basado en Debian (Ubuntu o similares).
### Instalar dependencias
```bash
sudo apt update
sudo apt install docker docker-compose git -y
```
### Configurar equipo
Se tiene que abrir el firewall para permitir acceso externo al servidor MQTT
```bash
sudo ufw allow 1883
sudo ufw enable
```
Si se quiere utilizar AWS o similares, se tiene que abrir el puerto de la máquina virtual al internet a través de los security groups.
Se tiene que abrir

| Puerto| Descripción |
|----------|----------|
| 1883    | MQTT  |
| 3000    | Interfaz Web de Grafana  |
| 8086    | Interfaz Web de InfluxDB   |
| 9090    | Interfaz Web de Prometheus   |

### Clonar repositorio
Todo lo necesario viene dentro de Docker
```bash
git clone https://github.com/LeonardoRangel12/iotDB.git
```


### Ejecutar repositorio
Antes de ejecutar el Docker debemos cambiar los permisos para que puedan utilizar las carpetas:
```
cd iotDB
chmod -R 777 data/*
Ejecutamos el docker.
```bash
docker-compose up -d
```

## Acceder a los datos
### Credenciales
<strong>InfluxDB:<br></strong>
Usuario: hola<br>
Contraseña: holamundo<br>
<strong>Grafana:<br></strong>
Usuario: admin<br>
Contraseña: admin<br><br>
MQTT y Prometheus no utilizan contraseña<br>
### Obtener IP
#### Localmente
Se tiene que obtener la IP para acceder
```bash
ip addr show
```
#### AWS
Esta se puede ver en las instancias de EC2
