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

## 5. Servicios a probar:
    - Elasticsearch: Almacenará los logs de los contenedores, registrando cualquier traza que pudieran llegar a soltar los servicios dockerizados, incluido el propio elastic.

    - Fluentbit: Es el servicio que enviará los logs a Elasticsearch

    - Nginx: A parte de servir la web del site de pruebas, hará de proxy inverso.

    - Grafana: Es un servicio web que permite hacer gráficos y paneles con la información del sistema

    - Prometheus: Se encarga de la monitorización de servicios, dado que es un entorno local, no necesitaremos enviar alertas por correo.

    - Portainer: Es una interfaz web que permite ver los contenedores y gestionarlos de forma básica.

    - CAdvisor: Exporta métricas de los contenedores que pueden ser ingestadas por Grafana y prometheus

## 5. Establecemos el orden de arranque de los servicios

## 6. Comprobaciones extra (auditoría)

## 7. ¡Alerta, malas prácticas!