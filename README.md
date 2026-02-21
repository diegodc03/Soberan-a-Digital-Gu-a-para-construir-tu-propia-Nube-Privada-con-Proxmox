# 🏡 Mi Homelab: Soberanía Digital con Proxmox

Bienvenido a la documentación de mi servidor casero. Este proyecto nace con el objetivo de recuperar el control de mis datos, aprender administración de sistemas y alojar mis propios servicios sin depender de la nube de terceros (Google, Apple, Microsoft, etc.).

Todo el entorno está montado sobre un único equipo físico, virtualizando los servicios para maximizar la eficiencia, el aprendizaje y la seguridad.

---

## 🧠 El Cerebro: La Infraestructura Base

El sistema operativo principal que gestiona todo el hardware es **Proxmox Virtual Environment (VE)**, un hipervisor de tipo 1 (bare-metal). 

* **Proxmox VE:** Permite dividir los recursos del servidor físico para crear Máquinas Virtuales (VMs) y Contenedores (LXC).
* **Almacenamiento (DicoHdd / local-lvm):** Uso discos separados para el sistema operativo y para el almacenamiento masivo de datos de mis aplicaciones.
* **Ventaja principal:** Si un servicio falla, el resto del servidor sigue funcionando intactamente gracias al aislamiento.

---

## 🛡️ Infraestructura y Red (Los Cimientos)

La seguridad y la conectividad son el primer paso antes de exponer cualquier servicio.

* **Tailscale (LXC 102):** Red privada virtual (Mesh VPN) basada en WireGuard. Me permite acceder a todos los servicios de mi casa desde cualquier lugar del mundo de forma segura, sin tener que abrir puertos en el router.
* **AdGuard Home (LXC 103):** Servidor DNS sumidero. Bloquea anuncios, rastreadores y dominios maliciosos a nivel de red para todos los dispositivos conectados en mi casa.

---

## ☁️ La Nube Personal (Productividad)

Servicios destinados a reemplazar a las grandes tecnológicas y mantener la privacidad de mis archivos y recuerdos.

* **NextCloud (LXC 101):** Mi alternativa a Google Drive/Dropbox. Sincronización de archivos, gestión de documentos, calendario (CalDAV) y contactos (CardDAV) totalmente autohospedados.

---

## 🏠 Domótica y Automatización (Hogar Inteligente)

El servidor trabaja de forma proactiva para automatizar mi entorno físico y digital.

* **Home Assistant (VM 100):** El cerebro de mi casa inteligente. Unifica dispositivos de múltiples marcas bajo una misma interfaz de control local, permitiendo automatizaciones complejas sin depender de internet.
* **n8n (LXC 107):** Alternativa autohospedada a Zapier. Lo utilizo para conectar APIs y automatizar flujos de trabajo entre mis distintas aplicaciones (ej. enviar notificaciones a Telegram si ocurre un evento en NextCloud).

---

## 🤖 IA Local y Sandbox (El Laboratorio)

Espacio dedicado al aprendizaje continuo y a la experimentación con nuevas tecnologías.

* **Ollama (LXC 108):** Ejecución de Modelos de Lenguaje Grande (LLMs) en local. Me permite tener un asistente tipo ChatGPT totalmente privado, sin que mis *prompts* o datos salgan de mi red.
* **Nodos Debian (VM 104, 105, 106):** Máquinas virtuales limpias dedicadas a realizar pruebas. Aquí aprendo comandos de terminal, instalo Docker/Docker Compose y despliego servicios nuevos de prueba. El uso de "Snapshots" (instantáneas) me permite romper el sistema sin miedo y restaurarlo en segundos.

---

## 🚀 Agradecimientos y Recursos

Gran parte de esta infraestructura ha sido posible gracias a la filosofía del código abierto y a las herramientas de la comunidad.

* **Proxmox Helper Scripts (por tteck):** Herramienta fundamental para el despliegue rápido y optimizado de contenedores LXC en Proxmox.
