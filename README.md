# Practica Multinube usando AZURE y AWS

# Configuración AWS
Se crea una unica instancia usando la practica proporcionada por el curso en AWS.

Overview Intance:
![alt text](image-7.png)

Overview Network Security
![alt text](image-8.png)

# Configuración vm AZURE
Desde la maquina azure se realizan las siguientes configuraciones

* Se realiza una creación de reglas de seguridad en Network settings

![alt text](image.png)

* Dentro de la maquina se ingresa usando par de claves ssh 

![alt text](image-1.png)

* Se desea desplgar un app sencilla de appnotas, con python y usando flask para desplegar el app.py es necesario crear un entorno virtual que permita el empaquetado.

**Pruba Ping entre ambas maquinas**

* Desde vm AZURE hacia vm AWS:
```
ping 54.237.247.175

```

![alt text](image-9.png)


* Desde vm AWS hacia vm AZURE
```
ping 20.92.161.3
```

![alt text](image-11.png)

* Global

![alt text](image-10.png)


# Configuración de API vm AZURE

**Instalar virtualenv si no está instalado:**

Si no tienes virtualenv instalado, puedes instalarlo con pip:
bash

```
sudo apt update
sudo apt install python3-venv -y
```
* Crear un entorno virtual venv
```
python3 -m venv venv
```
* Activar entorno virtual
```
source venv/bin/activate
```
![alt text](image-2.png)

# Instalar dependencias

Se instala todas las dependencias requeridas por el API
```
pip install -r requirements.txt
```

# Desplegar aplicación
Prueba inicial 
```
python app.py
```
* Prueba desde maquina aws

**<u>ENDPOINT CONSULTAR ESTUDIANTE</u>**
```
curl -X GET http://20.92.161.3:5000/getStudents
```
![alt text](image-3.png)

Prueba desde navegador web
![alt text](image-4.png)


**<u>ENDPOINT DE AGREGAR NUEVO ESTUDIANTE</u>**
```
curl -X POST http://20.92.161.3:5000/addNewStudent -H "Content-Type: application/json" -d '{ "name" : "Andrea", "id": "1245435", "grade" : 4.6}'
```
![alt text](image-5.png)

Desde navegador web
![alt text](image-6.png)

# Pruebas desde el postman

* get 

![alt text](image-12.png)

* Post
![alt text](image-13.png)
