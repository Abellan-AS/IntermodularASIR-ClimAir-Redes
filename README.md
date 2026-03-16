# Proyecto Intermodular ASIR-Redes: Infraestructura de Red Climair S.L.

## 📝 Descripción
Diseño e implementación de una red corporativa jerárquica para **Climair S.L.** El proyecto contempla la segmentación de red mediante VLANs, enrutamiento Inter-VLAN y políticas de seguridad avanzadas para una estructura de dos plantas.

## 🛠️ Especificaciones Técnicas
* **Topología:** Estrella extendida con niveles de distribución y acceso.
* **Enrutamiento:** Router-on-a-Stick distribuido en dos interfaces físicas (`Gig0/0` y `Gig0/1`).
* **Direccionamiento:** Pools de DHCP automáticos por VLAN; direccionamiento estático para servidores.
* **Seguridad:** Listas de Control de Acceso (ACLs) extendidas y seguridad WPA2-PSK en WiFi.

## 📊 Tabla de Direccionamiento (VLANs)
| VLAN | Departamento | Red | Gateway | Ubicación |
| :--- | :--- | :--- | :--- | :--- |
| 10 | Administración | 192.168.10.0/24 | 192.168.10.1 | Planta Baja |
| 20 | Dirección | 192.168.20.0/24 | 192.168.20.1 | Planta Baja |
| 30 | Desarrollo | 192.168.30.0/24 | 192.168.30.1 | Primera Planta |
| 40 | Soporte | 192.168.40.0/24 | 192.168.40.1 | Primera Planta |
| 50 | Aula Formación | 192.168.50.0/24 | 192.168.50.1 | Primera Planta |
| 60 | Servidores (CPD)| 192.168.60.0/24 | 192.168.60.1 | Planta Baja |
| 99 | Gestión (MGMT) | 192.168.99.0/24 | 192.168.99.1 | P. Baja / WiFi |

## 🛡️ Políticas de Seguridad Implementadas
* **ACL_AULA:** Deniega tráfico desde el Aula (V50) hacia Dirección (V20).
* **ACL_DEV:** Deniega tráfico desde Desarrollo (V30) hacia Administración (V10).
* **VTY_ACCESS:** El acceso por terminal virtual al Router está restringido únicamente a la VLAN 99.

## 📶 Configuración Wireless
* **SSID:** `SSID_EMPRESA`
* **Seguridad:** WPA2-PSK
* **Asignación:** Mapeado a la VLAN 99 (Gestión) mediante puerto de acceso dedicado.

## ✅ Pruebas de Validación
1. **DHCP Test:** Verificado el correcto funcionamiento del handshake DHCP en todos los departamentos.
2. **Ping Test (Permitido):** Conectividad exitosa entre Administración (V10) y Servidores (V60).
3. **ACL Test (Bloqueo):** Verificación de "Destination host unreachable" en intentos de acceso no autorizados.

---
**Entorno de simulación:** Cisco Packet Tracer 8.2+
**Autor:** Climair IT Department
