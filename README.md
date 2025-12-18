
# AWS Inventory Project – Python, Flask, Docker & ECS

Este proyecto consiste en una **aplicación web completa** (Frontend + Backend + Base de Datos) desarrollada con **Python y Flask**, cuyo objetivo es demostrar cómo una aplicación **CRUD sencilla** puede ser **containerizada con Docker** y desplegada correctamente en **AWS**, siguiendo buenas prácticas de arquitectura, redes y seguridad.

La aplicación está preparada para ejecutarse **localmente** para pruebas y para escalarse a un entorno **cloud productivo** sin modificar el código, únicamente ajustando la infraestructura y las variables de entorno.

---

## 📂 Estructura del Proyecto

- **BACKEND/**: API en Python (Flask) que maneja la lógica de negocio y las operaciones CRUD.
- **FRONTEND/**: Aplicación Web en Flask + HTML que consume la API y renderiza páginas.
- **docker-compose.yml**: Configuración para levantar una base de datos MySQL local para pruebas.
- **Dockerfile**: Cada servicio (frontend y backend) cuenta con su propio Dockerfile para su despliegue en contenedores.

---

## 🧩 Arquitectura y Tecnologías

- **Lenguaje**: Python  
- **Framework**: Flask  
- **Contenedores**: Docker  
- **Cloud (AWS)**:
  - ECS Fargate (frontend y backend como servicios independientes)
  - Application Load Balancer + Target Groups
  - Amazon ECR (almacenamiento de imágenes Docker)
  - Amazon RDS (MySQL) en subred privada
  - VPC con subredes públicas y privadas
  - Security Groups aplicando principio de mínimo privilegio

---

## 🚀 Requisitos Previos

1. **Python 3.10+** instalado.
2. **Docker Desktop** instalado y ejecutándose.

---

## 🛠️ Configuración Inicial (Ejecución Local)

### 1. Base de Datos (Docker)

Para iniciar la base de datos MySQL localmente, abre una terminal en la carpeta raíz del proyecto y ejecuta:

```bash
docker-compose up -d db
````

Esto levantará un contenedor MySQL en el puerto `3306`.

> Nota: La primera vez puede tardar unos segundos mientras se inicializa la base de datos.

---

### 2. Entorno Virtual (Opcional pero recomendado)

Crea y activa un entorno virtual para instalar las dependencias:

```bash
# Windows
python -m venv venv
.\venv\Scripts\activate

# Mac/Linux
python3 -m venv venv
source venv/bin/activate
```

---

### 3. Instalación de Dependencias

Instala las librerías necesarias para el Backend y el Frontend:

```bash
pip install -r BACKEND/requirements.txt
pip install requests
```

---

## ▶️ Ejecución de la Aplicación

Necesitarás **dos terminales abiertas** (una para el Backend y otra para el Frontend).

### Terminal 1: Backend (API Flask)

```bash
python BACKEND/app.py
```

* Corre en el puerto `5000`
* Expone operaciones CRUD
* Se conecta a MySQL mediante variables de entorno

---

### Terminal 2: Frontend (Flask + HTML)

```bash
python FRONTEND/app.py
```

* Corre en el puerto `3000`
* Consume la API del backend
* Renderiza páginas HTML desde Flask

---

## 🌐 Probar la Aplicación

Abre tu navegador y ve a:

👉 **[http://127.0.0.1:3000](http://127.0.0.1:3000)**

Desde la interfaz podrás:

1. Ver listas de usuarios y productos.
2. Crear nuevos registros.
3. Editar registros existentes.
4. Eliminar registros.

Esto permite probar el flujo completo:
**Frontend → Backend → Base de Datos**.

---

## ☁️ Despliegue en AWS

Este proyecto fue diseñado para desplegarse en AWS utilizando contenedores Docker:

1. **Base de Datos**: Crear una instancia de Amazon RDS (MySQL) en subred privada.
2. **Imágenes Docker**: Construir y subir las imágenes a Amazon ECR.
3. **Servicios**: Desplegar frontend y backend en ECS Fargate.
4. **Balanceo**: Exponer los servicios mediante Application Load Balancer y Target Groups.
5. **Seguridad**: Configurar Security Groups restringiendo el acceso entre componentes.

No es necesario modificar el código fuente, únicamente configurar las variables de entorno y la infraestructura.

---

## 🎯 Objetivo del Proyecto

El propósito de este repositorio es demostrar:

* Uso práctico de **Python y Flask**
* Implementación real de **operaciones CRUD**
* Uso correcto de **Docker** para aplicaciones backend
* Capacidad de diseñar y desplegar una **arquitectura funcional en AWS**
* Comprensión de conceptos de **redes, balanceo de carga y seguridad**

---

## 🙌 Créditos

Proyecto desarrollado en equipo como ejercicio de arquitectura cloud.

Repositorio original del equipo:
[https://github.com/ElDevos/aws-project-topicos](https://github.com/ElDevos/aws-project-topicos)

Este repositorio corresponde a mi **versión personal de portafolio**, con énfasis en documentación, arquitectura y despliegue.

```
