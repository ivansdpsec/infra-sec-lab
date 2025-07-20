# Hardening de Servidor Debian – Infraestructura Simulada

**Versión base:** Debian 11 (Bullseye)  
**Rol:** Servidor SSH + Samba  
**Objetivo:** Reducir superficie de ataque y fortalecer la configuración básica del sistema.

---

## 🛡️ 1. Gestión de usuarios

- Deshabilitar login de `root` por SSH:
  ```bash
  sudo nano /etc/ssh/sshd_config
  PermitRootLogin no
  
- Crear usuario con privilegios controlados (sin sudo generalizado).
- Aplicar umask restrictivo: umask 027

## 🔐 2. Políticas de contraseñas
- Editar /etc/login.defs:
  PASS_MAX_DAYS 90
  PASS_MIN_DAYS 7
  PASS_WARN_AGE 14

- Activar complejidad con libpam-pwquality:
  sudo apt install libpam-pwquality

- Configurar en /etc/pam.d/common-password:
  password requisite pam_pwquality.so retry=3 minlen=12 ucredit=-1 lcredit=-1 dcredit=-1

## 🔄 3. Actualizaciones automáticas

- Instalar y configurar:
  sudo apt install unattended-upgrades
sudo dpkg-reconfigure --priority=low unattended-upgrades

## 🔥 4. Firewall (UFW)
- Activar y definir reglas mínimas:
  sudo apt install ufw
  sudo ufw allow from 192.168.1.0/24 to any port 22
  sudo ufw enable

## 🧼 5. Servicios y puertos

- Auditar servicios activos:
  ss -tuln

- Eliminar servicios innecesarios:
  sudo apt remove avahi-daemon telnet ftp

## 🕵️ 6. Auditoría básica
- Instalar y activar auditd:
  sudo apt install auditd
  sudo systemctl enable auditd

- Activar revisión de logs semanal:
  sudo apt install logwatch
  sudo logwatch --detail Medium --mailto admin@example.com --range 'yesterday'

## 🧾 Evidencia documental
- Copias de configuración de /etc/ssh/sshd_config, /etc/pam.d/common-password

- Salida de ufw status, ss -tuln, auditctl -l

- Capturas del log de logwatch


**Última revisión técnica:** [dd/mm/aaaa]  
**Responsable:** Iván Sotelo  
**Entorno:** Simulado – `infra-sec-lab`

