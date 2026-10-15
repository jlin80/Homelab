# Homelab — Proxmox, self-hosted services and Hermes

![Proxmox](https://img.shields.io/badge/Proxmox-VE-E57000?logo=proxmox)
![Kubernetes](https://img.shields.io/badge/Kubernetes-k3s-326CE5?logo=kubernetes)
![Terraform](https://img.shields.io/badge/Terraform-IaC-7B42BC?logo=terraform)

Homelab de tres nodos Proxmox con servicios self-hosted, k3s, Forgejo y Hermes. Este repositorio conserva configuraciones de una etapa anterior; **no todo lo que aparece en Terraform, CI/CD o monitoring representa el estado real actual**.

> **Precaución:** no ejecutar `terraform apply` ni workflows de despliegue hasta reconciliar el código con los recursos reales. Terraform aún contiene nombres, IDs y direcciones antiguas. La configuración versionada no debe tratarse como fuente de verdad de la infraestructura actual.

## Inventario reportado

| Nodo | IP de administración | CT | Servicio | Observaciones |
|---|---|---:|---|---|
| PVE | `192.168.100.10` | 100 | Pi-hole | Inventariado; estado actual por verificar |
| PVE | `192.168.100.10` | 101 | Vaultwarden | No es n8n; estado actual por verificar |
| PVE | `192.168.100.10` | 102 | k3s | Inventariado; estado actual por verificar |
| PVE2 | `192.168.100.11` | 104 | Streaming | IP y puertos pendientes de confirmar |
| PVE2 | `192.168.100.11` | 201 | ownCloud Infinite Scale (oCIS) | `https://192.168.100.41:9200` |
| PVE2 | `192.168.100.11` | 206 | Base de datos | Motor, IP y puertos pendientes de confirmar |
| PVE3 | `192.168.100.12` | 301 | Forgejo | Inventariado; disponibilidad no verificada |
| PVE3 | `192.168.100.12` | 303 | Hermes | Inventariado; disponibilidad no verificada |

### Incidencia de PVE3

Se reportó que PVE3 no aceptaba conexiones SSH y no volvió a arrancar después de reconectar la alimentación. La recuperación no está confirmada. Por tanto, Forgejo y Hermes no deben considerarse disponibles hasta verificar el nodo y sus CT.

## Hermes: roles documentados

- **Sniper:** búsqueda y selección focalizada de oportunidades.
- **Trading:** análisis y operación de trading según permisos explícitos.
- **Watchdog / Alerts:** detección de condiciones y generación de alertas.
- **NOC:** operaciones y diagnóstico de infraestructura.
- **Developer:** desarrollo y revisión de proyectos.
- **Research:** investigación y síntesis.

La lista describe roles conocidos, no confirma que estén ejecutándose ni sus integraciones actuales. Mantener credenciales fuera de Git y limitar las acciones destructivas o financieras a permisos expresamente autorizados.

## Configuraciones heredadas que requieren revisión

- **`terraform/`:** declara un inventario antiguo, incluida la referencia a n8n en CT101, CT103 como monitoring y Nextcloud en CT201, además de la red `192.168.1.0/24`. No aplicar hasta reconciliar state, configuración y recursos reales.
- **`.github/workflows/deploy.yml`:** referencia rutas de monitoring y despliegues k3s de la configuración anterior. El despliegue automático por push debe permanecer deshabilitado hasta validar destinos y efectos.
- **`monitoring/`:** contiene configuraciones de Prometheus, Grafana, Loki/Promtail, Alertmanager y Homepage. Su presencia en Git no demuestra que estén activos.
- **`k8s/`:** revisar el contexto y el estado real del clúster antes de aplicar manifiestos.
- **`.github/workflows/terraform.yml`:** la validación de sintaxis no demuestra que el plan coincida con la infraestructura real.

## Reconciliación pendiente

1. Recuperar y verificar PVE3.
2. Confirmar IDs, nombres, IP, estado y almacenamiento de los CT en los tres nodos.
3. Verificar backups mediante una prueba de restauración; no asumir que ZFS/NFS o la retención histórica siguen activos.
4. Comparar Terraform state, código y recursos existentes antes de cualquier cambio.
5. Auditar runner, secretos y workflows; reactivar despliegues solo tras una prueba controlada.
6. Actualizar la documentación de monitoring y k3s después de confirmar qué componentes siguen en uso.

## Seguridad operativa

- No versionar tokens, contraseñas, claves privadas, kubeconfigs ni statefiles con secretos.
- Revisar el plan de Terraform antes de aplicar.
- No ejecutar workflows heredados sin confirmar sus destinos.
- Distinguir explícitamente entre inventario reportado, estado comprobado y configuración histórica.

## Estructura del repositorio

- [Terraform](terraform/)
- [Manifiestos k3s](k8s/)
- [Configuraciones históricas de monitoring](monitoring/)
- [Estado actual y plan de reconciliación](docs/current-state.md)
- [Proyecto de infraestructura AWS](https://github.com/jlin80/cloud-engineer-portfolio)
