# 🚀 DevOps Parcial 2 · Ansible + Docker + Nginx

Proyecto de automatización de configuración de servidores web utilizando **Ansible**, simulando múltiples nodos con **Docker Compose**.

Se utilizan:

* 🐳 Docker para simular servidores
* ⚙️ Ansible para automatizar configuraciones
* 🌐 Nginx como servidor web

---

## 🧱 Arquitectura

Se crean dos nodos:

| Nodo  | SSH Port | HTTP Port |
| ----- | -------- | --------- |
| node1 | 2223     | 8080      |
| node2 | 2224     | 8081      |

Cada nodo:

* Corre un servidor SSH
* Es configurado por Ansible
* Instala Nginx
* Despliega una página web

---

## 📁 Estructura del proyecto

```
.
├── Dockerfile
├── README.md
├── docker-compose.yml
├── inventory.ini
├── playbook.yml
└── site
    ├── img
    │   ├── background.webp
    │   └── preview.png
    ├── index.html
    ├── scripts.js
    └── styles.css
```

---

## 🧰 Requisitos

* Docker
* Docker Compose
* Ansible
* sshpass (para autenticación por password)

---

## ⚙️ Instalación de Ansible

### 🔹 En Ubuntu / Linux

```bash
sudo apt update
sudo apt install ansible -y
```

---

### 🔹 Instalar sshpass

```bash
sudo apt install sshpass -y
```

---

### 🔹 Verificar instalación

```bash
ansible --version
```

---

## 🐳 Ejecución del proyecto

### 🔹 1. Levantar contenedores

```bash
docker compose up --build -d
```

---

### 🔹 2. Verificar contenedores

```bash
docker ps
```

---

### 🔹 3. Probar conexión Ansible

```bash
ansible -i inventory.ini all -m ping
```

Salida esperada:

```
node1 | SUCCESS => pong
node2 | SUCCESS => pong
```

---

### 🔹 4. Ejecutar playbook

```bash
ansible-playbook -i inventory.ini playbook.yml
```

Esto realizará:

* Instalación de Nginx
* Copia de archivos web
* Inicio del servicio

---

## 🌐 Acceso a la aplicación

Una vez ejecutado el playbook, puedes acceder a los servidores:

* http://localhost:8080 → node1
* http://localhost:8081 → node2

---

[![GitHub](https://img.shields.io/badge/Alb3rtsonTL-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/Alb3rtsonTL)