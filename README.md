# 🐼 PWNAGOTCHI: Guía Completa de Construcción 2026

---

## 📋 PORTADA OFICIAL

```
╔══════════════════════════════════════════════════════════════════════════════╗
║                                                                              ║
║                          🐼 PWNAGOTCHI 2026 🐼                              ║
║                                                                              ║
║                    Guía Completa de Instalación y Configuración             ║
║                                                                              ║
║                              Por: Hector I. Montano                         ║
║                                                                              ║
║                      🎯 MiTecHoy - Seguridad Ofensiva 🎯                   ║
║                                                                              ║
║                         📍 San Diego • Tijuana, MX                          ║
║                                                                              ║
║                          🗓️  Febrero 2026                                   ║
║                                                                              ║
║                 ⭐ De la frustración al éxito: Un viaje técnico ⭐         ║
║                                                                              ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

---

## 🎖️ INSIGNIAS Y RECONOCIMIENTOS

[![Pwnagotchi](https://img.shields.io/badge/Pwnagotchi-v2.9.5.4-brightgreen)](https://pwnagotchi.org/)
[![Python](https://img.shields.io/badge/Python-3.13-blue)](https://www.python.org/)
[![Raspberry Pi](https://img.shields.io/badge/Raspberry%20Pi-Zero%20W%20v1.1-red)](https://www.raspberrypi.org/)
[![Ubuntu](https://img.shields.io/badge/Ubuntu-Desktop%202026-orange)](https://ubuntu.com/)
[![Waveshare](https://img.shields.io/badge/Waveshare-2.13%20V4-yellow)](https://www.waveshare.com/)
[![License](https://img.shields.io/badge/License-Educational-important)](https://github.com/jayofelony/pwnagotchi)

---

## 📑 TABLA DE CONTENIDOS

- [🎯 Introducción](#introducción)
- [🛠️ Materiales Requeridos](#materiales-requeridos)
- [📦 Preparación del Hardware](#preparación-del-hardware)
- [💻 Proceso de Instalación](#proceso-de-instalación)
- [🐛 Troubleshooting Completo](#troubleshooting-completo)
- [🎓 Cátedra: Operación del Pwnagotchi](#cátedra-operación)
- [🚀 Casos de Uso Avanzados](#casos-de-uso-avanzados)
- [📚 Referencias y Recursos](#referencias-y-recursos)
- [🙏 Créditos y Agradecimientos](#créditos-y-agradecimientos)

---

## 🎯 INTRODUCCIÓN

El **Pwnagotchi** es una herramienta de auditoría de redes Wi-Fi basada en IA, diseñada para capturar "handshakes" de WPA2/WPA3 de forma autónoma. Es como un "Tamagotchi" para hackers: una entidad digital que aprende de su entorno y se alimenta de intercambios de autenticación Wi-Fi.

### ¿Para Quién es Esta Guía?

- **Penetration Testers** en formación
- **Profesionales de Ciberseguridad** que desean herramientas alternativas
- **Entusiastas de IoT** interesados en Raspberry Pi
- **Estudiantes** de seguridad ofensiva
- **Desarrolladores** que quieren contribuir a proyectos de código abierto

### Objetivos de Este Documento

✅ Proporcionar un paso a paso completo sin ambigüedades  
✅ Documentar TODOS los errores encontrados durante el proceso  
✅ Ofrecer soluciones verificadas en el campo  
✅ Facilitar la depuración de problemas comunes  
✅ Inspirar a nuevos profesionales en ciberseguridad  

---

## 🛠️ MATERIALES REQUERIDOS

### Hardware Obligatorio

| Componente | Especificación | Proveedor | Costo Aprox. |
|-----------|----------------|-----------|-------------|
| **Raspberry Pi** | Zero W (v1.1) - 32bit | Distribuidor oficial | $15-20 USD |
| **MicroSD** | 8GB - Clase 10+ | Kingston, SanDisk | $10-15 USD |
| **Pantalla** | Waveshare 2.13" V4 e-Ink | Amazon | $15-25 USD |
| **Cable USB** | Micro USB (DATOS, no solo carga) | Cualquiera | $3-8 USD |
| **Fuente de Poder** | Power Bank 5V/2A | Anker, Xiaomi | $15-30 USD |

### Software Recomendado

- **Sistema Operativo (Host)**: Ubuntu 24.04+ o Windows 10/11 con WSL2
- **Herramientas**: 
  - Raspberry Pi Imager (https://www.raspberrypi.com/software/)
  - nano o VS Code para editar archivos
  - Terminal POSIX (bash, zsh)

### Conocimientos Previos (Recomendado)

- Familiaridad con línea de comandos (terminal/bash)
- Conceptos básicos de Wi-Fi (SSID, MAC, canales)
- Noción de criptografía WPA2/WPA3
- Git básico (no obligatorio para este proceso)

---

## 📦 PREPARACIÓN DEL HARDWARE

### Paso 1: Descarga la Imagen Correcta

**⚠️ ERROR CRÍTICO A EVITAR**: No descargar la versión de 64 bits.  
La Raspberry Pi Zero W v1.1 es un procesador ARMv6 de 32 bits. Cualquier imagen arm64 **NO funcionará**.

```bash
# Descarga ESTA versión específica:
# pwnagotchi-32bit-2.9.5.4.img.xz (Jayofelony - Recomendado para 2026)

# Ubicación de descarga:
# https://github.com/jayofelony/pwnagotchi/releases
```

### Paso 2: Quemado de la Imagen en la SD

**Herramienta**: Raspberry Pi Imager o BalenaEtcher

```bash
# Usando la línea de comandos (Linux/Mac):
xzcat pwnagotchi-32bit-2.9.5.4.img.xz | sudo dd of=/dev/sdX bs=4M status=progress
sudo sync
```

### Paso 3: Configuración de Arranque

Una vez que la SD esté flasheada, **ANTES de insertar en la Pi**:

**⚠️ PASO CRÍTICO**: Crear el archivo `config.toml`

1. Monta la partición `bootfs` en tu laptop
2. Crea un archivo de texto con este contenido exacto:

```toml
main.name = "pwnagotchi"
main.lang = "en"
ui.display.enabled = true
ui.display.type = "waveshare_3"
ui.display.color = "black"

main.whitelist = [
  "TU_RED_WIFI_AQUI"
]
```

**⚠️ ERRORES COMUNES EN ESTE PASO**:
- ❌ Guardar como `config.toml.txt` (Windows agrega extensión automáticamente)
- ❌ Usar caracteres especiales en el nombre
- ❌ Dejar comillas mal cerradas

3. **Guárdalo exactamente como**: `config.toml` (sin extensión .txt)
4. Colócalo en la raíz de la partición `bootfs`

---

## 💻 PROCESO DE INSTALACIÓN

### Fase 1: Conexión Inicial (USB a Laptop)

#### En la Raspberry Pi:

1. Inserta la microSD
2. **Conecta el cable USB al puerto de DATOS** (no el de PWR)
3. Enciende tu laptop

#### En tu Laptop (Ubuntu/Linux):

Espera **5-10 minutos**. La Pi Zero está generando claves SSH.

```bash
# Verifica que aparezca la interfaz de red
ip a

# Deberías ver algo como: enx9a20da6da1b0 o enxaa239c963dbf
```

### Fase 2: Configuración de Red en Ubuntu

Si la interfaz aparece pero sin IP, configúrala manualmente:

```bash
# Obtén el nombre exacto de tu interfaz
ip a

# Asume que es enxXXXXXXXXXXXX
sudo ip addr add 10.0.0.1/24 dev enxXXXXXXXXXXXX
sudo ip link set enxXXXXXXXXXXXX up

# Prueba de conexión
ping -c 4 10.0.0.2
```

### Fase 3: Primera Conexión SSH

```bash
ssh pi@10.0.0.2
# Contraseña: raspberry

# Si funciona, verás el banner de bienvenida del Pwnagotchi
```

### Fase 4: Acceso a la Interfaz Web

```bash
# En tu navegador (Firefox, Chrome):
http://10.0.0.2:8080

# Usuario por defecto: admin
# Contraseña: admin
```

---

## 🐛 TROUBLESHOOTING COMPLETO

### 🔴 PROBLEMA 1: "Connection Timed Out" en SSH

**Síntomas**: `ssh pi@10.0.0.2` devuelve "Connection timed out"

**Causas Raíz Identificadas**:

1. **Cable USB incorrecto**
   - Solución: Verificar que sea un cable de DATOS (no solo carga)
   - Prueba: Cambiar a un cable de teléfono viejo que sabes que funciona

2. **Puerto USB incorrecto**
   - Solución: La Pi Zero tiene dos puertos micro-USB
     - Central/Largo = DATOS ✅
     - Esquina/Corto = PWR ONLY ❌

3. **IP no asignada**
   - Solución: Ejecutar comando de red manual
   ```bash
   sudo ip addr add 10.0.0.1/24 dev enxXXXXXXXXXXXX
   ```

4. **Ubuntu Network Manager interfiriendo**
   - Solución: Deshabilitar gestión automática
   ```bash
   sudo nmcli device set enxXXXXXXXXXXXX managed no
   sudo ip addr add 10.0.0.1/24 dev enxXXXXXXXXXXXX
   ```

---

### 🔴 PROBLEMA 2: Pantalla Congelada / Blanca

**Síntomas**: Pantalla Waveshare se queda en blanco o no se actualiza

**Causas Raíz Identificadas**:

1. **Driver de pantalla incorrecto en config.toml**
   - Síntoma: Sistema arranca pero pantalla no responde
   - Solución:
   ```toml
   # Para Waveshare V4, usar:
   ui.display.type = "waveshare_4"
   # NO usar waveshare_3 si tienes V4
   ```

2. **config.toml con extensión .txt**
   - Síntoma: El Pwnagotchi ignora la configuración, pantalla se queda en blanco
   - Verificación: En Ubuntu, hacer `ls -la /media/.../bootfs/`
   - Solución:
   ```bash
   # En Ubuntu, renombrar el archivo
   mv /media/user/bootfs/config.toml.txt /media/user/bootfs/config.toml
   ```

3. **Errores de sintaxis en config.toml**
   - Síntoma: Sistema arranca parcialmente pero se congela
   - Verificación: Conectar por SSH y ejecutar
   ```bash
   sudo pwnagotchi --debug
   # Buscar TOMLDecodeError en la salida
   ```

---

### 🔴 PROBLEMA 3: "Destination Host Unreachable"

**Síntomas**: Ping a 10.0.0.2 devuelve "Destination Host Unreachable"

**Causas Raíz Identificadas**:

1. **cmdline.txt sin módulos de red USB**
   - Síntoma: Conexión física existe (425 Mb/s) pero no hay ping
   - Archivo afectado: `/boot/firmware/cmdline.txt`
   - Solución:
   ```bash
   # En Ubuntu, mientras la SD está montada, verificar:
   cat /media/user/rootfs/boot/firmware/cmdline.txt
   
   # Debe contener (EN UNA SOLA LÍNEA):
   # ...rootwait modules-load=dwc2,g_ether
   ```

2. **config.txt sin activación del modo gadget**
   - Verificación:
   ```bash
   grep "dtoverlay=dwc2" /media/user/rootfs/boot/firmware/config.txt
   ```
   - Solución:
   ```toml
   # En la sección [all], debe tener:
   dtoverlay=dwc2
   dtoverlay=dwc2,dr_mode=peripheral
   ```

3. **Firewall de Ubuntu bloqueando tráfico**
   - Solución temporal:
   ```bash
   sudo ufw disable
   ping 10.0.0.2
   # Si funciona aquí, reactivar firewall y crear regla específica
   sudo ufw enable
   sudo ufw allow from 10.0.0.0/24
   ```

---

### 🔴 PROBLEMA 4: Imagen Corrupta / No Arranca

**Síntomas**: 
- LED verde no parpadea
- Pantalla permanentemente negra
- SSH no responde después de 10 minutos

**Causas Raíz Identificadas**:

1. **Versión de 64 bits instalada en Pi Zero**
   - Solución: Re-flashear con versión de 32 bits correcta
   ```bash
   # Descargar la imagen CORRECTA
   wget https://github.com/jayofelony/pwnagotchi/releases/download/v2.9.5.4/pwnagotchi-32bit-2.9.5.4.img.xz
   
   # Re-flashear
   xzcat pwnagotchi-32bit-2.9.5.4.img.xz | sudo dd of=/dev/sdX bs=4M
   ```

2. **SD corrupta durante flasheado**
   - Verificación: Reintentar con cable USB diferente
   - Solución: Formatear completamente la SD
   ```bash
   sudo shred -vfz -n 3 /dev/sdX
   sudo mkfs.ext4 /dev/sdX
   ```

---

### 🔴 PROBLEMA 5: "name is invalid" en Logs

**Síntomas**: 
```
[WARNING] name 'bicho-2.4G' is invalid: min length is 2, max length 25, only a-zA-Z0-9- allowed
```

**Causa Raíz Identificada**:
- El nombre contiene caracteres no permitidos (puntos, espacios, caracteres especiales)

**Solución**:
```toml
# ❌ INCORRECTO:
main.name = "bicho-2.4G"
main.name = "bicho 2.4G"
main.name = "bicho_2.4G"

# ✅ CORRECTO:
main.name = "bicho24G"
main.name = "HectorV4"
main.name = "pwn-2026"
```

---

## 🎓 CÁTEDRA: OPERACIÓN DEL PWNAGOTCHI

### Los Estados de Ánimo (Carita)

```
(^‿^) HAPPY      - Todo va bien, escaneando activamente
(◕‿◕) EXCITED    - Encontró una red nueva o está capturando handshakes
(⌐■_■) COOL      - Acaba de ejecutar un ataque exitoso
(-__-) BORED      - No hay redes cercanas, necesita moverse
(╥☁╥) SAD        - Ocurrió un error en el sistema
(☓‿‿☓) BROKEN    - Falla crítica (generalmente por config.toml)
```

### Plugins Esenciales

#### 1. **memtemp** (Temperatura y Memoria)

Ver recursos del sistema en tiempo real.

**Ubicación**: `/home/pi/.pwn/lib/python3.13/site-packages/pwnagotchi/plugins/default/memtemp.py`

**Verificar instalación**:
```bash
ssh pi@10.0.0.2
ls -la /home/pi/.pwn/lib/python3.13/site-packages/pwnagotchi/plugins/default/memtemp.py
```

**Activar en Web UI**: Ir a Plugins > memtemp > Enable

#### 2. **grid** (Reportes Globales)

Sube tus capturas a OpwnGrid (opcional).

**Activar**:
```bash
# En Web UI: Plugins > grid > Enable
```

#### 3. **webcfg** (Configuración Web)

Permite editar config.toml desde la interfaz web.

**Usar**: Web UI > Plugins > webcfg

---

### Modos de Operación

#### MANU Mode (Manual)
- Activado: Cuando conectas por USB a la laptop
- Comportamiento: Muy conservador, no ataca activamente
- Uso: Configuración, descarga de archivos

#### AUTO Mode
- Activado: Cuando solo recibe energía (batería)
- Comportamiento: Ataca activamente, captura handshakes
- Uso: Auditoría de campo

**Cambiar modo**:
```bash
# Desde Web UI:
# Home > "Restart in AUTO mode"

# O por SSH:
sudo systemctl restart pwnagotchi
```

---

### Protección de Tus Propias Redes

**⚠️ CRÍTICO**: Sin esto, tu Pwnagotchi atacará tu propio Wi-Fi

```toml
main.whitelist = [
  "IZZI-44F6-5G",      # Red 5G
  "IZZI-44F6",         # Red 2.4G
  "AA:BB:CC:DD:EE:FF"  # MAC de tu teléfono
]
```

**Encontrar MAC de tu iPhone**:
1. Ajustes > General > Información
2. Busca "Dirección Wi-Fi"
3. Desactiva "Dirección Wi-Fi privada" en tu red

---

### Ver Logs en Tiempo Real

```bash
# Acceso remoto por SSH
tail -f /var/log/pwnagotchi.log

# Filtrar solo handshakes capturados
tail -f /var/log/pwnagotchi.log | grep "handshake"

# Comando corto
pwnlog
```

---

## 🚀 CASOS DE USO AVANZADOS

### 1. Compartir Internet desde Ubuntu a Pwnagotchi

Para que pueda actualizar plugins y conectarse a la red global (OpwnGrid).

```bash
# En Ubuntu:
sudo iptables -t nat -A POSTROUTING -o wlp4s0 -j MASQUERADE
sudo iptables -A FORWARD -i enxXXXXXXXXXXXX -o wlp4s0 -j ACCEPT
sudo sysctl -w net.ipv4.ip_forward=1

# En SSH del Pwnagotchi:
sudo systemctl restart networking
```

### 2. Extraer Handshakes a tu Laptop

Los archivos .pcap capturados se guardan en `/root/handshakes/`

```bash
# Desde Ubuntu:
scp pi@10.0.0.2:/root/handshakes/*.pcap ~/Desktop/

# Ver con Wireshark:
wireshark ~/Desktop/*.pcap
```

### 3. Intentar Crackear un Handshake

Usando hashcat o john:

```bash
# Con hashcat (recomendado, más rápido):
hashcat -m 22000 handshake.pcap wordlist.txt

# Con john the ripper:
john --format=wpapsk --wordlist=wordlist.txt handshake.pcap
```

### 4. Configurar Bluetooth Tethering (Avanzado)

Conectarse al Pwnagotchi desde tu iPhone sin cables.

```bash
# Editar config.toml:
[main.plugins.bt-tether]
enabled = true
devices.iphone.enabled = true
devices.iphone.mac = "MAC_DE_TU_IPHONE"

# Luego configurar en iPhone:
# Ajustes > Punto de acceso personal > Bluetooth encendido
```

---

## 📚 REFERENCIAS Y RECURSOS

### Documentación Oficial

- **Pwnagotchi Oficial**: https://pwnagotchi.org/
- **Repositorio Jayofelony**: https://github.com/jayofelony/pwnagotchi
- **Raspberry Pi Official**: https://www.raspberrypi.org/documentation/
- **Waveshare Wiki**: https://www.waveshare.com/wiki/2.13inch_e-Paper_HAT_(C)

### Herramientas de Seguridad

- **Wireshark**: https://www.wireshark.org/ (Análisis de paquetes)
- **Hashcat**: https://hashcat.net/ (Crack de handshakes)
- **John the Ripper**: https://www.openwall.com/john/ (Fuerza bruta)
- **WPA-Sec**: https://wpa-sec.stanev.org/ (Base de datos de contraseñas)

### Comunidades y Foros

- **GitHub Issues Jayofelony**: https://github.com/jayofelony/pwnagotchi/issues
- **Reddit r/pwnagotchi**: https://reddit.com/r/pwnagotchi
- **Hacker Forums**: Various security-focused communities

### Recursos de Aprendizaje

- **Documentación de Ciberseguridad**: https://owasp.org/
- **Riesgos de Seguridad Inalámbrica**: https://www.wifi-warriors.com/

---

## 🙏 CRÉDITOS Y AGRADECIMIENTOS

### Desarrolladores Principales

- **Evilsocket** (@evilsocket): Creador original del Pwnagotchi
  - GitHub: https://github.com/evilsocket/pwnagotchi
  - Concepto revolucionario que hizo esto posible

- **Jayofelony** (@jayofelony): Mantenedor actual (2024-2026)
  - GitHub: https://github.com/jayofelony/pwnagotchi
  - Mejoras, compatibilidad y actualizaciones continuas

### Comunidades de Soporte

- **Equipo Waveshare**: Por drivers y soporte de pantalla
- **Comunidad Raspberry Pi**: Por documentación y soporte
- **Comunidad de Ciberseguridad**: Por feedback y mejoras

### Herramientas Utilizadas en Esta Guía

- **Bettercap**: Motor de ataque de red
- **Linux**: Sistema operativo base
- **Python 3.13**: Lenguaje de programación
- **Git/GitHub**: Control de versiones y colaboración

### Reconocimiento Especial

Agradecimiento a todos los usuarios que reportaron bugs, compartieron soluciones y contribuyeron a hacer que el Pwnagotchi sea más accesible para los nuevos profesionales de ciberseguridad.

---

## 🌟 ACERCA DE MITECHOY

**MiTecHoy** es una iniciativa dedicada a **democratizar la ciberseguridad** a través de:

- 📚 Educación técnica de calidad
- 🎥 Contenido en video (YouTube)
- 🔧 Herramientas prácticas y documentación
- 🤝 Comunidad de profesionales

### Conexiones de MiTecHoy

| Recurso | URL |
|---------|-----|
| **Sitio Web** | https://www.mitechoy.com |
| **YouTube** | https://www.youtube.com/@Mitechoy |
| **GitHub** | https://github.com/MiTecHoy |
| **Ubicación** | San Diego • Tijuana, MX |

### Síguenos

Para más contenido de seguridad ofensiva, tutorials y actualizaciones:

```
🎥 YouTube: @Mitechoy
💻 Web: www.mitechoy.com
🔗 GitHub: MiTecHoy
```

---

## 📜 LICENCIA Y DISCLAIMER

### Licencia

Este proyecto utiliza la **misma licencia que Pwnagotchi**: 
- Basado en trabajo de Evilsocket y Jayofelony
- Sujeto a licencias de software de código abierto

### Disclaimer Legal

```
⚠️ ADVERTENCIA IMPORTANTE ⚠️

El Pwnagotchi es una herramienta de auditoría de red. Solo debe utilizarse:

✅ En redes que posees
✅ En redes donde tienes permiso explícito
✅ Con fines educativos y de investigación
✅ En ambientes controlados (laboratorios, sandboxes)

❌ PROHIBIDO su uso en:
- Redes ajenas sin autorización (ILEGAL)
- Sistemas de terceros sin consentimiento escrito
- Fines maliciosos o de sabotaje
- Violación de leyes locales de ciberseguridad

El autor y MiTecHoy NO son responsables del mal uso de esta herramienta.
Úsala responsablemente y dentro de los marcos legales de tu jurisdicción.
```

---

## 🎬 VERSIÓN DE VIDEO

Próximamente en **YouTube @Mitechoy**:

- 📹 Tutorial paso a paso completo
- 🐛 Troubleshooting visual
- 🎥 Captura de handshakes en tiempo real
- 💡 Tips avanzados y casos reales

**Suscríbete** para ser el primero en verlo: https://www.youtube.com/@Mitechoy

---

## 🔄 HISTORIAL DE CAMBIOS

| Versión | Fecha | Cambios |
|---------|-------|---------|
| 1.0 | Feb 2026 | Documento inicial - Guía completa |
| 1.1 | Pendiente | Agregar casos de uso avanzados |
| 1.2 | Pendiente | Integración con vídeos de YouTube |

---

## 📞 SOPORTE Y CONTACTO

¿Problemas o sugerencias?

1. **Busca en esta guía**: El 90% de los problemas están documentados
2. **GitHub Issues**: https://github.com/jayofelony/pwnagotchi/issues
3. **MiTecHoy Comunidad**: www.mitechoy.com/soporte
4. **Reddit**: r/pwnagotchi

---

## ✨ CONCLUSIÓN

Felicidades por completar esta guía. Has:

✅ Configurado un Pwnagotchi desde cero  
✅ Resuelto problemas técnicos complejos  
✅ Aprendido sobre seguridad inalámbrica  
✅ Contribuido a la comunidad de ciberseguridad  

**El Pwnagotchi es tu compañero digital en la auditoría de redes.**

Úsalo sabiamente, aprende constantemente y comparte tu conocimiento.

---

```
╔══════════════════════════════════════════════════════════════════════════════╗
║                                                                              ║
║                    Creado con ❤️ por Hector I. Montano                      ║
║                                                                              ║
║                              MiTecHoy 2026                                  ║
║                                                                              ║
║                    "La seguridad es educación constante"                    ║
║                                                                              ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

---

**Última actualización**: Febrero 2026  
**Mantenedor**: Hector I. Montano (@Mitechoy)  
**Estado**: ✅ Documentación Activa

---

## 📁 ESTRUCTURA DEL REPOSITORIO

```
Pwnagotchi-MiTecHoy/
├── README.md (Este archivo)
├── docs/
│   ├── installation-guide.md
│   ├── troubleshooting.md
│   ├── advanced-usage.md
│   └── security-considerations.md
├── scripts/
│   ├── setup.sh
│   ├── backup-handshakes.sh
│   └── crack-wpa.sh
├── configs/
│   ├── config.toml.example
│   ├── config.txt.example
│   └── cmdline.txt.example
├── CONTRIBUTING.md
├── LICENSE
└── CHANGELOG.md
```

---

**¡Bienvenido a la comunidad Pwnagotchi! 🐼**
