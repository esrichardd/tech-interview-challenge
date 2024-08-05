# Tech Interview Challenge

Este proyecto contiene una serie de servicios que se ejecutan en contenedores Docker, coordinados por un archivo `docker-compose.yml`. A continuación se explica cómo clonar e inicializar el proyecto.

## Tecnologías Utilizadas
- Go 1.22.2: Lenguaje de programación para el backend.
- NestJS: Framework de Node.js para construir aplicaciones del lado del servidor.
- MySQL: Sistema de gestión de bases de datos relacional.
- Redis: Base de datos en memoria utilizada como caché.
- Kafka: Plataforma de mensajería distribuida.
- Docker Compose: Herramienta para definir y ejecutar aplicaciones Docker con múltiples contenedores.

## Clonar el Repositorio

Para comenzar, primero debes clonar el repositorio principal y sus submódulos. Ejecuta los siguientes comandos en tu terminal:

```bash
# Clonar el repositorio principal
git clone --recurse-submodules https://github.com/esrichardd/tech-interview-challenge.git

# Navegar al directorio del proyecto
cd tech-interview-challenge
```

## Inicializar el Proyecto

Una vez clonado el repositorio, puedes iniciar el proyecto utilizando Docker Compose. Asegúrate de tener Docker y Docker Compose instalados en tu máquina.

### Configuración de Entorno

Antes de iniciar los contenedores, es posible que desees configurar variables de entorno específicas para tu entorno local. Crea un archivo `.env` en el directorio raíz del proyecto con el siguiente contenido:

```
MYSQL_ROOT_PASSWORD=root
MYSQL_DATABASE=tech-interview-db
MYSQL_USER=user
MYSQL_PASSWORD=user_password
MYSQL_TCP_PORT=3307
MYSQL_HOST=tech-interview-mysql
REDIS_HOST=tech-interview-redis
REDIS_PORT=6379
TECH_INTERVIEW_CORE_PORT=3002
TECH_INTERVIEW_CORE_NODE_ENV=development
TECH_INTERVIEW_SCRAPPERS_PORT=3003
TECH_INTERVIEW_KAFKA_ADVERTISED_LISTENERS=INSIDE://tech-interview-kafka:9093,OUTSIDE://localhost:9092
TECH_INTERVIEW_KAFKA_LISTENER_SECURITY_PROTOCOL_MAP=INSIDE:PLAINTEXT,OUTSIDE:PLAINTEXT
TECH_INTERVIEW_KAFKA_LISTENER_NAMES=INSIDE,OUTSIDE
TECH_INTERVIEW_KAFKA_LISTENER_NAME=INSIDE
TECH_INTERVIEW_KAFKA_LISTENERS=INSIDE://0.0.0.0:9093,OUTSIDE://0.0.0.0:9092
TECH_INTERVIEW_KAFKA_INTER_BROKER_LISTENER_NAME=INSIDE
TECH_INTERVIEW_KAFKA_ZOOKEEPER_CONNECT=tech-interview-zookeeper:2181
```

Ajusta las variables de entorno según las necesidades de tu configuración local.

### Iniciar Contenedores

Para iniciar todos los contenedores definidos en el archivo `docker-compose.yml`, ejecuta:

```bash
docker-compose up
```

Esto descargará las imágenes necesarias (si no están presentes en tu sistema) y levantará los contenedores especificados.

### Verificar Estado

Para verificar que todos los contenedores están corriendo correctamente, puedes usar:

```bash
docker-compose ps
```

## Submódulos

El proyecto incluye dos submódulos:

- `tech-interview-scrappers`: Contiene el código para los scrappers.
- `tech-interview-core`: Contiene el núcleo de la aplicación y la lógica de negocio.

Estos submódulos se clonan automáticamente al usar `--recurse-submodules`, pero si necesitas actualizarlos manualmente, puedes usar:

```bash
git submodule update --init --recursive
```

## Documentación Adicional

Para más información sobre cómo configurar y usar los servicios dentro de los submódulos, consulta la documentación específica en sus respectivos repositorios.

## Contacto

Para cualquier pregunta o problema, puedes contactarme en espinozar1994@gmail.com