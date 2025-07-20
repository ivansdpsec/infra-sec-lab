# Política de Backup – Entorno Simulado

## Objetivo
Garantizar la disponibilidad y recuperación de la información en caso de fallo, pérdida de datos o incidente de seguridad.

## Alcance
Aplicable a los servidores Debian simulados en el entorno `infra-sec-lab`, con foco en configuraciones básicas y datos críticos.

## Frecuencia
- Backup completo semanal (cron)
- Backup incremental diario (rsync)

## Almacenamiento
- Destino: disco externo montado en `/mnt/backups`
- Tipo: backup cifrado (usando `gpg` o `duplicity`)
- Retención: 4 semanas

## Verificación
- Prueba mensual de recuperación en entorno separado
- Logs almacenados en `/var/log/backup.log`

## Responsabilidades
- Responsable técnico: administrador del entorno
- Supervisión documental: mediante checklist mensual

## Herramientas utilizadas
- `rsync`, `cron`, `gpg`, `logrotate`

---

**Última revisión:** [dd/mm/aaaa]
