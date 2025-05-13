# Examen-Parcial-2
https://github.com/Gmongtor/Examen-Parcial-2.git
# 🌌 Parte I – Misiones de Conocimiento Teórico (60%)

---

## 🛰️ Misión 1: Direccionamiento IP y Subredes – Base Eco (Hoth)

**Red base asignada:** `172.16.0.0/24`  
**Objetivo:** Dividir la red eficientemente en subredes para:

- Comando Central (~50 hosts)
- Defensa Perimetral (~30 hosts)
- Centro Médico (~20 hosts)
- Hangar y Taller (~14 hosts)
- Enlace Troncal con la antena

| Departamento           | Hosts necesarios | Hosts asignados | Subred CIDR | Máscara            | Rango de Hosts                 | Broadcast              |
|------------------------|------------------|------------------|--------------|---------------------|-------------------------------|------------------------|
| Comando Central        | 50               | 64               | 172.16.0.0/26 | 255.255.255.192     | 172.16.0.1 – 172.16.0.62      | 172.16.0.63           |
| Defensa Perimetral     | 30               | 32               | 172.16.0.64/27| 255.255.255.224     | 172.16.0.65 – 172.16.0.94     | 172.16.0.95           |
| Centro Médico          | 20               | 32               | 172.16.0.96/27| 255.255.255.224     | 172.16.0.97 – 172.16.0.126    | 172.16.0.127          |
| Hangar y Taller        | 14               | 16               | 172.16.0.128/28| 255.255.255.240    | 172.16.0.129 – 172.16.0.142   | 172.16.0.143          |
| Enlace Troncal         | 6                | 8                | 172.16.0.144/29| 255.255.255.248    | 172.16.0.145 – 172.16.0.150   | 172.16.0.151          |

**Espacio restante:** `172.16.0.152 – 172.16.0.255` disponible para futuras subredes.

---

## 🔀 Misión 2: Enrutamiento Estático vs Dinámico

### Comparativa de Enrutamiento

| Tipo        | Ventajas                                                   | Desventajas                                                   |
|-------------|-------------------------------------------------------------|----------------------------------------------------------------|
| Estático    | - Control total<br>- Menor uso de CPU<br>- Mayor seguridad | - No se adapta a fallos<br>- No escalable fácilmente           |
| Dinámico    | - Se adapta automáticamente<br>- Escalable                 | - Más complejo<br>- Más tráfico de actualización               |

### Protocolos de Enrutamiento Dinámico

- **RIP (Routing Information Protocol)**  
  - Basado en vector de distancia  
  - Fácil configuración  
  - Convergencia lenta

- **OSPF (Open Shortest Path First)**  
  - Basado en estado de enlace  
  - Usa algoritmo de Dijkstra  
  - Rápido y eficiente

### Diferencias clave

- **Vector de distancia**: conoce solo los saltos hacia vecinos.  
- **Estado de enlace**: conoce el estado de toda la red.

---

## 🌐 Misión 3: Sistema DNS y Resolución de Nombres

### ¿Qué es DNS?

El **Sistema de Nombres de Dominio (DNS)** traduce nombres de dominio (por ejemplo, `holonet.rebelion.org`) a direcciones IP (`192.168.10.50`).

### Funcionamiento del DNS

1. El cliente consulta su caché o el DNS configurado.
2. Si no está, hace consultas:
   - Servidor raíz (`.`)
   - Servidor TLD (`.org`)
   - Servidor autoritativo (`rebelion.org`)
3. Devuelve un **registro A** con la IP.

### Ejemplo

holonet.rebelion.org → 192.168.10.50

### ¿Qué pasa si el servidor DNS no responde?

- La red no puede traducir nombres a IPs.
- No se accede a servicios por nombre.
- Solo funcionaría con IPs conocidas.

---

## 📡 Misión 4: Comparación TCP vs UDP

| Característica   | TCP                                         | UDP                                      |
|------------------|----------------------------------------------|-------------------------------------------|
| Tipo de conexión | Orientado a conexión                        | No orientado a conexión                   |
| Fiabilidad       | Alta – garantiza entrega y orden            | Baja – puede perder paquetes              |
| Confirmaciones   | Sí (ACKs, retransmisiones)                  | No                                        |
| Rendimiento      | Menor, por control de errores               | Mayor, por ser más ligero                 |
| Casos de uso     | Emails, descargas, HTTP                     | Streaming, VoIP, juegos en tiempo real    |

### Ejemplos

- **TCP**: Transferencia de planos secretos, mensajes críticos.  
- **UDP**: Transmisión en vivo desde naves, coordenadas de ataque.

---

## 🔐 Misión 5: Criptografía y Seguridad

### Cifrado Simétrico

- Misma clave para cifrar y descifrar.
- **Rápido** y eficiente.
- **Ejemplo**: Leia y Luke comparten una contraseña.

### Cifrado Asimétrico

- Clave pública para cifrar, privada para descifrar.
- **No requiere compartir clave previamente**.
- **Ejemplo**: enviar mensajes a un nuevo aliado.

### Autenticación y No Repudio

- **Autenticación**: garantiza que el emisor es quien dice ser.
- **No repudio**: el emisor no puede negar su envío.
- Se logra con **firmas digitales** (hash cifrado con clave privada).

### Protocolos Seguros

| Protocolo | ¿Cifrado? | Seguridad |
|-----------|-----------|-----------|
| Telnet    | ❌ No      | Inseguro  |
| SSH       | ✅ Sí      | Seguro    |

**Conclusión:** Usar **SSH** para administrar remotamente routers y servidores rebelde es esencial para evitar espionaje imperial.

---
