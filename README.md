# Simulando entornos "productivos" en nuestro local con Docker

## 1. Mapeando en nuestro /etc/hosts los dominios (o no)
Si no tenemos comprado ningún dominio, pues lo mapeamos a nuestro local, pero como el dominio local coincida con preproducción o con producción, vamos a tener un problema grave.

Por ello propongo que el dominio sea test.servicio.cliente.com, quedando nuestro /etc/hosts así:

    127.0.0.1 test.grafana.rafa.com

    127.0.0.1 test.rafa.com

    127.0.0.1 test.prometheus.rafa.com

    127.0.0.1 test.portainer.rafa.com

## 2. Generamos una CA

## 3. Firmamos los certificados

## 4. Directorios para persistir los datos

## 5. Establecemos el orden de arranque de los servicios

## 6. Comprobaciones extra (auditoría)

## 7. ¡Alerta, malas prácticas!