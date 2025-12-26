

## ¿Qué es Aircrack-ng?

**Aircrack-ng** es una **suite de herramientas de auditoría de redes inalámbricas (Wi-Fi)** diseñada para evaluar la seguridad de redes basadas en el estándar **IEEE 802.11**.

No es una única herramienta, sino un **conjunto de utilidades especializadas** orientadas al análisis, captura e interpretación de tráfico inalámbrico.

---

## ¿Para qué se utiliza?

Desde un enfoque **profesional y ético**, Aircrack-ng se utiliza para:

- Auditorías de seguridad Wi-Fi
- Pentesting inalámbrico autorizado
- Evaluación de configuraciones débiles
- Formación en ciberseguridad
- Investigación académica y pruebas de laboratorio

> ⚠️ El uso sin autorización expresa del propietario de la red es ilegal.

---

## Protocolos y estándares involucrados

Aircrack-ng trabaja principalmente con:

- **IEEE 802.11 (Wi-Fi)**
- Modos de operación:
  - Managed
  - Monitor
- Tipos de cifrado:
  - WEP
  - WPA
  - WPA2 (PSK / Enterprise)

---

## Componentes principales de la suite

### 🔹 airmon-ng
- Habilita y gestiona el **modo monitor**
- Configura interfaces inalámbricas
- Detiene procesos que interfieren (NetworkManager, wpa_supplicant)

El modo monitor permite capturar y analizar tramas sin necesidad de asociarse a una red.

---

### 🔹 airodump-ng
- Captura tráfico Wi-Fi en tiempo real
- Muestra información como:
  - BSSID
  - ESSID
  - Canal
  - Clientes conectados
  - Tipo de cifrado
- Guarda capturas (`.cap`) para análisis posterior

Es fundamental para la captura de **handshakes WPA/WPA2**.

---

### 🔹 aireplay-ng
- Inyecta tráfico en redes Wi-Fi
- Permite:
  - Desautenticación de clientes
  - Reinyección de paquetes
  - Generación de tráfico artificial

Se utiliza para forzar eventos que faciliten el análisis de seguridad.

---

### 🔹 aircrack-ng
- Motor de **análisis criptográfico**
- Analiza archivos de captura (`.cap`)
- Realiza ataques:
  - Diccionario
  - Fuerza bruta limitada
  - Análisis estadístico (WEP)

No rompe el cifrado directamente, sino que **evalúa la fortaleza de la clave**.

---

### 🔹 airbase-ng
- Permite crear **puntos de acceso falsos (Evil Twin)**
- Se usa en ataques avanzados:
  - Rogue AP
  - Man-in-the-Middle
- Herramienta sensible y de alto impacto

---

## Tipos de ataques (visión teórica)

### 🔸 WEP
- Vulnerable por diseño
- Ataques basados en:
  - IVs débiles
  - Reinyección de paquetes
- Considerado **obsoleto e inseguro**

---

### 🔸 WPA / WPA2-PSK
- Ataques **offline**
- Requiere captura de handshake
- La seguridad depende de:
  - Longitud de la contraseña
  - Complejidad
  - Uso de diccionarios adecuados

> No se “rompe” WPA, se **intenta adivinar la clave**.

---

### 🔸 WPA2-Enterprise
- No es el foco principal de Aircrack-ng
- Requiere otras técnicas y herramientas (EAP, RADIUS)
- Aircrack-ng tiene uso limitado en este contexto

---

## Requisitos técnicos

- Tarjeta Wi-Fi compatible con:
  - Modo monitor
  - Inyección de paquetes
- Drivers adecuados
- Sistema operativo Linux:
  - Kali Linux
  - Parrot OS
  - Arch / Ubuntu (configurado)

---

## Limitaciones de Aircrack-ng

- No vulnera cifrados fuertes
- No funciona sin tráfico o handshakes válidos
- No supera contraseñas robustas
- Dependiente del hardware
- Fácilmente detectable en entornos monitorizados

---

## Detección y defensa (visión Blue Team)

Para mitigar ataques relacionados con Aircrack-ng:

- Monitorizar deauth floods
- Implementar WIDS / WIPS
- Usar WPA3
- Activar PMF (Protected Management Frames)
- Contraseñas largas, únicas y no reutilizadas

---

## Aspectos legales y éticos

Uso permitido:
- Auditorías autorizadas
- Laboratorios controlados
- Redes propias

Uso prohibido:
- Redes ajenas sin permiso
- Interrupción de servicio
- Acceso no autorizado

> La autorización define la legalidad.

---

## Conclusión

Aircrack-ng es una herramienta:

- Educativa y profesional
- Ideal para comprender la seguridad Wi-Fi
- Basada en análisis estadístico y criptografía aplicada
- Ineficaz frente a buenas prácticas de seguridad

Su valor real está en **aprender cómo defender mejor las redes inalámbricas**.
