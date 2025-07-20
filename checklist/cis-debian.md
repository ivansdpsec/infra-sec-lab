# Checklist CIS – Debian 11 (Simulación Técnica)
**Versión base**: Debian 11 (Bullseye)  
**Rol del sistema**: Servidor general (servicios SSH y Samba)

---

## 🔐 1. Seguridad de cuentas y contraseñas

| Control | Acción aplicada | Estado |
|--------|------------------|--------|
| 1.1.1  | Deshabilitar cuenta `root` por SSH (`PermitRootLogin no`) | ✅ |
| 1.1.2  | Configurar política de contraseñas seguras (PAM) | ⚠️ En revisión |
| 1.1.3  | Bloqueo tras intentos fallidos con `faillog` y `pam_tally2` | ✅ |

---

## 🔒 2. Servicios innecesarios

| Control | Acción aplicada | Estado |
|--------|------------------|--------|
| 2.1.1  | Desinstalación de paquetes innecesarios (`telnet`, `ftp`) | ✅ |
| 2.1.2  | Desactivar servicios no usados (`cups`, `avahi`) | ✅ |

---

## 📦 3. Actualizaciones y parches

| Control | Acción aplicada | Estado |
|--------|------------------|--------|
| 3.1.1  | `unattended-upgrades` activado para actualizaciones automáticas | ✅ |
| 3.1.2  | Revisión semanal manual con `apt list --upgradable` | ✅ |

---

## 🔍 4. Auditoría y logs

| Control | Acción aplicada | Estado |
|--------|------------------|--------|
| 4.1.1  | Activar `auditd` y configurar reglas básicas | ✅ |
| 4.1.2  | Revisión de logs con `logwatch` semanal | ⚠️ En pruebas |

---

## 🌐 5. Red y firewall

| Control | Acción aplicada | Estado |
|--------|------------------|--------|
| 5.1.1  | Activar `ufw` con reglas mínimas | ✅ |
| 5.1.2  | SSH solo permitido desde red interna | ✅ |

---

## 🗂️ Documentación de evidencia

- `/etc/ssh/sshd_config` con `PermitRootLogin no`
- Capturas de `apt remove`, `ufw status`
- Script de verificación semanal de actualizaciones
- Logs generados por `auditd` y `logwatch`

---

**Última revisión técnica:** [dd/mm/aaaa]  
**Responsable técnico:** Iván Sotelo  
**Entorno:** Simulado – `infra-sec-lab`
