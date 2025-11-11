# SXE_tarea11

### Crea un repositorio en GitHub documentando la instalación de un entorno de desarrollo Odoo 18 completo usando Docker, VS Code/Pycharm (u otro IDE que prefieras) y PgAdmin. Ten en cuenta que Odoo está programado en Python.  

En nuestro archivo .yml insertamos los servicios para lo pedido.

yaml 
```
services:
  web:
    image: odoo:17.0
    depends_on:
      - mydb
    ports:
      - "8069:8069"
    environment:
      - HOST=mydb
      - USER=odoo
      - PASSWORD=myodoo
  mydb:
    image: postgres:15
    environment:
      - POSTGRES_DB=postgres
      - POSTGRES_PASSWORD=myodoo
      - POSTGRES_USER=odoo
  pgadmin:
    image: dpage/pgadmin4:latest
    container_name: pgadmin_container
    environment:
      PGADMIN_DEFAULT_EMAIL: piero@gmail.com
      PGADMIN_DEFAULT_PASSWORD: sxe_user_password_db
    ports:
      - "8081:80"
    depends_on:
      - mydb
    restart: unless-stopped
```

