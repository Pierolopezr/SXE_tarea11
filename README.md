# SXE_tarea11

#### Crea un repositorio en GitHub documentando la instalación de un entorno de desarrollo Odoo 18 completo usando Docker, VS Code/Pycharm (u otro IDE que prefieras) y PgAdmin. Ten en cuenta que Odoo está programado en Python.  


En nuestro archivo .yml insertamos los servicios para lo pedido en `Intellij` con los pluggins (En este caso python, añadidos).

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

Posteriormente con el comando `docker-compose up`, arrancamos el docker, por lo que accederemos al navegador con sus puertos respectivos (`8081 y 8069`)

## Odoo  
Tal como nos indican en la actividad, seleccionaremos el apartado de **Load demonstration data** para  cargar datos de demostración. Posteriormente rellenaremos los datos tal como lo dejamos en nuestro archivo `.yml` para crear la base de datos.  

<img width="950" height="600" alt="Captura de pantalla 2025-11-11 210033" src="https://github.com/user-attachments/assets/31837fec-f507-4383-9128-435b09630748" />  

**Iniciamos sesión.**

<img width="950" height="600" alt="Captura de pantalla 2025-11-11 210248" src="https://github.com/user-attachments/assets/34314cba-c582-4be4-ad3e-cf705d326f03" />  

**Aplicaciones:**
Nos aparecerán un listado de módulos básicos a los cuales añadiremos unos cuantos. 

<img width="950" height="600" alt="image" src="https://github.com/user-attachments/assets/11284286-41c5-40a6-b651-dc264d8173fb" />

**Compra:** 

<img width="950" height="600" alt="Captura de pantalla 2025-11-11 210705" src="https://github.com/user-attachments/assets/f2a96206-4104-4a2f-811e-8ce1fa31a24e" />

**Venta:** 

<img width="950" height="600" alt="Captura de pantalla 2025-11-11 210919" src="https://github.com/user-attachments/assets/ad9dd1b1-0f6e-44ed-8d8e-0abdae5e5128" />

**Contactos:**

<img width="950" height="600" alt="Captura de pantalla 2025-11-11 213320" src="https://github.com/user-attachments/assets/198eac06-e965-4377-bff9-b818723f0fd0" />








