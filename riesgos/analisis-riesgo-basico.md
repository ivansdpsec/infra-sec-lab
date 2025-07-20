# Análisis de Riesgo Básico – Entorno Simulado

**Entorno:** `infra-sec-lab`  
**Fecha:** [dd/mm/aaaa]  
**Responsable:** Iván Sotelo

---

## 🎯 Objetivo

Identificar y evaluar riesgos técnicos que puedan afectar la confidencialidad, integridad o disponibilidad de los activos en un entorno Linux simulado.

---

## 🗂️ Activos evaluados

| Activo                      | Tipo         | Valoración |
|----------------------------|--------------|------------|
| Servidor Debian (SSH+Samba) | Hardware/VPS | Alta       |
| Backups locales cifrados    | Datos        | Alta       |
| Configuración del sistema   | Software     | Media      |
| Usuarios con acceso remoto  | Humano       | Alta       |

---

## ⚠️ Riesgos identificados

| ID  | Riesgo                                        | Probabilidad | Impacto | Nivel de riesgo | Mitigación aplicada                  |
|-----|-----------------------------------------------|--------------|---------|------------------|--------------------------------------|
| R-01| Acceso no autorizado por SSH                  | Media        | Alta    | Alto             | `PermitRootLogin no`, firewall UFW   |
| R-02| Pérdida de datos por fallo físico             | Baja         | Alta    | Medio            | Backup semanal cifrado               |
| R-03| Exposición de puertos innecesarios            | Alta         | Media   | Alto             | Auditoría con `ss`, eliminación de servicios |
| R-04| Contraseñas débiles de usuario                | Media        | Alta    | Alto             | PAM con `libpam-pwquality`           |
| R-05| Ausencia de monitoreo de logs                 | Alta         | Media   | Alto             | Instalación de `logwatch`, `auditd`  |

---

## 🛠️ Plan de mejora continua

- Aplicar checklist CIS completo
- Documentar política de contraseñas y MFA (si procede)
- Simular incidente y validar recuperación desde backup
- Introducir análisis de riesgo periódico cada 3 meses

---

## 🧾 Evidencia documental

- Captura de `ufw status`, `auditctl -l`, `logwatch`
- Capturas de configuración PAM y `sshd_config`
- Logs de backup cifrado (simulado)

---

**Última revisión:** [dd/mm/aaaa]  
**Autor:** Iván Sotelo – Simulación formativa
