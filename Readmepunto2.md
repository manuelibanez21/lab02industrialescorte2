# Implementación de Comunicación RS485 con Arduino  
## Modos: Simplex – Half Dúplex – Full Dúplex

### 🧰 **Materiales Utilizados**
- 2 placas **Arduino UNO**  
- 4 módulos **RS485 TTL**  
- Jumpers macho–macho  
- Cables de alimentación  
- Resistencias de terminación (cuando fue necesario)  
- Software de programación: **Arduino**

---

### 🧪 **1. Comunicación Simplex (Unidireccional)**

#### 📡 Descripción
En este modo, un Arduino actuó como **maestro transmisor** y el otro como **esclavo receptor**.  
Solo se utilizó **un bus de comunicación** (líneas A y B).

- Se configuró el pin **DE/RE** en el transmisor en HIGH para habilitar el envío.
- El receptor permaneció con DE/RE en LOW para habilitar la recepción.
- No hubo necesidad de control de colisiones.

#### ✅ Comprobaciones
- Se verificó la transmisión unidireccional correcta desde el maestro hacia el esclavo.  
- Los datos enviados desde el maestro fueron recibidos de manera estable.  
- Se confirmó la integridad de la señal mediante el monitor serial.

---

### 🔄 **2. Comunicación Half Dúplex (Bidireccional Alternada)**

#### 📡 Descripción
En este modo, ambos Arduinos pudieron transmitir y recibir **por el mismo bus**, pero **no al mismo tiempo**.

- Se controló la dirección de transmisión con el pin **DE/RE**, alternando entre HIGH (transmisión) y LOW (recepción).
- Se usaron **2 módulos RS485** (uno por cada Arduino).
- Se implementó un protocolo simple para evitar colisiones, enviando primero un mensaje del maestro y luego la respuesta del esclavo.

#### ✅ Comprobaciones
- La comunicación fue bidireccional y alternada correctamente.  
- Se comprobó que no hubo interferencias al controlar adecuadamente la dirección.  
- Se verificaron los datos transmitidos en ambas direcciones con el monitor serial.

---

### 🔁 **3. Comunicación Full Dúplex (Bidireccional Simultánea)**

#### 📡 Descripción
En este modo se utilizó **transmisión y recepción simultánea**, lo que permitió que ambos Arduinos enviaran y recibieran al mismo tiempo.

- Se emplearon **4 módulos RS485**:  
  - 2 para transmisión (uno por cada Arduino)  
  - 2 para recepción (uno por cada Arduino)  
- Se crearon **dos buses independientes**: uno para TX maestro → RX esclavo y otro para TX esclavo → RX maestro.
- No fue necesario alternar la dirección de transmisión.

#### ✅ Comprobaciones
- Se verificó la comunicación simultánea en ambos sentidos.  
- Los datos se recibieron de forma estable sin interferencias ni pérdida de mensajes.  
- Se confirmó que la configuración full dúplex mejora el rendimiento respecto a half dúplex.

---

### 📷 **Evidencias**
- Las evidencias de las pruebas fueron registradas en **imágenes y videos** numerados como:  
  **“Conexiones del 1 al 15”**.
- Estas muestran las conexiones físicas, las pruebas en monitor serial y el comportamiento esperado en cada modo.

---

### 📝 **Conclusiones**
- La comunicación **Simplex** es la más sencilla de implementar, pero limitada en funcionalidad.  
- El modo **Half Dúplex** permite bidireccionalidad controlada, ideal para aplicaciones con bajo tráfico.  
- El modo **Full Dúplex** brinda **mayor rendimiento y velocidad de intercambio**, a costa de más hardware (4 módulos).  
- La verificación por monitor serial y evidencias físicas demostró que **los tres modos funcionaron correctamente**.

---
