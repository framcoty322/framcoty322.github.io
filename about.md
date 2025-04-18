---
layout: page
title: Detalles del Proyecto
---

# Arquitectura del Proyecto

Tengo una Raspberry Pi con 4 interfaces de red WiFi:
- `wg0`: Interfaz de la VPN con WireGuard
- `wlan0`: Provee conexión a internet a la Raspberry
- `wlan1`: WiFi para pentesting (chip Atheros)
- `wlan2`: Actúa como router para otros dispositivos

## 🔒 Conexión VPN WireGuard

1. Tengo un VPS como servidor WireGuard.
2. Configuré dos clientes:
   - Mi laptop personal
   - La Raspberry Pi Kali ARM
3. Ambas se conectan al mismo túnel VPN.
4. Usan una subred privada tipo `10.10.10.0/24`

## 🔗 Conexión por VNC Viewer

Una vez establecida la VPN, desde mi laptop uso `VNC Viewer` para conectarme a la IP privada de la Raspberry dentro de la VPN (`10.10.10.X`).

## 🔧 Extras Técnicos

- Configuré `iptables`/`nftables` para redireccionar tráfico.
- Hice forwarding de `wlan1` a `wlan2` para permitir salida a internet.
