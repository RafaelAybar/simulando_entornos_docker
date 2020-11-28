# Simulando entornos "productivos" en nuestro local con Docker

## 1. Mapeando en nuestro /etc/hosts los dominios (o no)
Si no tenemos comprado ningún dominio, pues lo mapeamos a nuestro local, pero como el dominio local coincida con preproducción o con producción, vamos a tener un problema grave.

Por ello propongo que el dominio sea test.servicio.nombredesarrollador.com, quedando nuestro /etc/hosts así:

    127.0.0.1 test.grafana.rafa.com

    127.0.0.1 test.rafa.com

    127.0.0.1 test.prometheus.rafa.com

    127.0.0.1 test.portainer.rafa.com

## 2. Generamos una CA
¿Para qué queremos crear una CA? Pues podríamos comprobar a generar certificados de cliente para otras aplicaciones que pudiéramos estar desarrollando, por ejemplo, para comprobar que sólo los que tengan nuestros certificados acceden a nuestros servicios

## 3. Firmamos los certificados

## 4. Directorios para persistir los datos
- nginx_conf: Contiene todos los virtualhost de nginx.
- portainer_data: Contiene la configuración de los usuarios de portainer.
- certs: Contiene todos .cert, .key usados por nginx
- env_files: Contiene todos los ajustes parametrizables de cada servicio. Ejemplos con grafana:


## 5. Servicios a probar:
- Elasticsearch: Almacenará los logs de los contenedores, registrando cualquier traza que pudieran llegar a soltar los servicios dockerizados, incluido el propio elastic.

- Fluent-bit: Es el servicio que enviará los logs a Elasticsearch. [Plantilla de fluentbit](docs/fluet-bit.md)

- Nginx: A parte de servir la web del site de pruebas, hará de proxy inverso.

- Grafana: Es un servicio web que permite hacer gráficos y paneles con la información del sistema. Puedes ver aquí una    configuración básica. [Variables de entorno de Grafana](docs/grafana.md)

- Prometheus: Se encarga de la monitorización de servicios, dado que es un entorno local, no necesitaremos enviar alertas por correo. [Plantilla de Prometheus](docs/prometheus.md)

- Portainer: Es una interfaz web que permite ver los contenedores y gestionarlos de forma básica.

- CAdvisor: Exporta métricas de los contenedores que pueden ser ingestadas por Grafana y prometheus

- Kibana: Permitirá establecer configuraciones avanzadas en Elasticsearch

## 5. Establecemos el orden de arranque de los servicios

## 6. Comprobaciones extra (auditoría)
- Análisis de SSL/TSL con [testssl.sh](https://github.com/drwetter/testssl.sh)
    (pendiente de documentar)

- Auditorías de imágenes de Docker con [trivy](https://github.com/aquasecurity/trivy)
    (pendiente de documentar)

## 7. ¡Alerta, malas prácticas!
  - No reposites los ficheros .env o que contengan credenciales
  - Ten cuidado con el orden de arranque de servicios
  - Usa contraseñas seguras, puedes generarlas con [passwordgenerator](https://passwordsgenerator.net/)
  - Guarda las contraseñas en un lugar seguro, como por ejemplo [keepassxc](https://keepassxc.org/project/)