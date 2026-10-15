# Homelab — Virtualización, servicios self-hosted y automatización

![Proxmox](https://img.shields.io/badge/Virtualization-Proxmox%20VE-E57000?logo=proxmox)
![Kubernetes](https://img.shields.io/badge/Containers-k3s-326CE5?logo=kubernetes)
![Terraform](https://img.shields.io/badge/IaC-Terraform-7B42BC?logo=terraform)
![Linux](https://img.shields.io/badge/Systems-Linux-FCC624?logo=linux&logoColor=black)

Proyecto personal de laboratorio orientado a desarrollar habilidades prácticas en **administración de sistemas, virtualización, contenedores, infraestructura como código, observabilidad y automatización**.

La infraestructura se mantiene intencionalmente privada. Este repositorio presenta el alcance técnico y las competencias del proyecto, no un inventario operativo ni instrucciones para acceder a los sistemas.

## Áreas técnicas

- **Virtualización y sistemas:** administración de un entorno basado en Proxmox VE y servicios Linux.
- **Contenedores y orquestación:** despliegue y operación de servicios contenerizados; experimentación con Kubernetes ligero (k3s).
- **Infraestructura como código:** uso y evaluación de Terraform para definir infraestructura reproducible.
- **Observabilidad:** trabajo práctico con métricas, dashboards, registros y alertas mediante herramientas del ecosistema Prometheus y Grafana.
- **Servicios self-hosted:** evaluación y operación de servicios privados para uso personal.
- **Automatización y operaciones:** scripting, flujos de trabajo, diagnóstico de fallos y mantenimiento.
- **Control de versiones:** documentación técnica y cambios gestionados con Git.

## Objetivos de aprendizaje

1. Mejorar la reproducibilidad de los despliegues y la gestión de configuración.
2. Practicar monitorización, diagnóstico y respuesta ante incidentes.
3. Separar configuraciones de laboratorio, pruebas y servicios estables.
4. Aplicar principios de mínimo privilegio y manejo seguro de credenciales.
5. Mantener documentación útil sin publicar detalles internos de la red.

## Tecnologías

**Proxmox VE · Linux · Docker · Kubernetes/k3s · Terraform · Prometheus · Grafana · Git · GitHub Actions**

La lista refleja tecnologías trabajadas en el proyecto; no implica que todos los componentes estén activos simultáneamente en la infraestructura actual.

## Seguridad y alcance público

Por seguridad, este repositorio no publica direcciones IP privadas, nombres internos de hosts, identificadores de contenedores, endpoints administrativos, inventarios completos, capturas de paneles internos ni configuraciones operativas específicas. Los ejemplos públicos deben ser genéricos y no contener credenciales, tokens, claves privadas, kubeconfigs ni datos de acceso.

Este proyecto es un laboratorio personal en evolución, no una declaración de disponibilidad ni un servicio público de producción.
