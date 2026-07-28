# Informe de Auditoría de Red Wi-Fi Insegura

## Introducción

El objetivo de esta práctica fue analizar el comportamiento de una conexión HTTP en una red pública para comprender los riesgos de seguridad asociados al uso de protocolos sin cifrado. Además, se estudió cómo una VPN puede proteger la privacidad del usuario mediante el cifrado del tráfico y el establecimiento de un túnel seguro.

---

# Sitio Analizado

**Sitio web:**

http://neverssl.com

Este sitio fue elegido porque utiliza el protocolo HTTP, permitiendo observar cómo viaja la información sin cifrado durante la comunicación entre el navegador y el servidor.

---

# Análisis del Tráfico

## 1. ¿Qué protocolo utiliza el sitio?

El sitio utiliza el protocolo **HTTP**.

HTTP transmite la información sin cifrado, por lo que cualquier persona que intercepte los paquetes de la comunicación puede leer su contenido.

A diferencia de HTTPS, HTTP no protege la confidencialidad ni la integridad de los datos transmitidos.

---

## 2. Información visible durante la solicitud

Al inspeccionar la solicitud desde la pestaña **Network** del navegador se pueden observar distintos elementos de la comunicación, entre ellos:

- URL solicitada.
- Método HTTP (GET).
- Host.
- Headers enviados por el navegador.
- User-Agent.
- Dirección solicitada.
- Código de respuesta del servidor.

Toda esta información viaja en texto plano cuando se utiliza HTTP.

---

# Evidencia Observada

Durante el análisis fue posible observar que la solicitud contiene información visible como:

- Host: neverssl.com
- Método: GET
- URL solicitada
- Encabezados HTTP
- User-Agent del navegador

Estos datos permiten identificar el sitio visitado y características del dispositivo utilizado.

<img width="555" height="1075" alt="7b9b3eaf-30e7-4970-a4ea-806bd019b854" src="https://github.com/user-attachments/assets/960cc714-642b-4a47-a63a-904508c9d7f9" />

---

# Riesgos Encontrados

Navegar mediante HTTP en una red Wi-Fi pública presenta diversos riesgos de seguridad.

Un atacante conectado a la misma red podría capturar el tráfico utilizando herramientas como Wireshark y obtener información como:

- Sitios web visitados.
- Recursos solicitados.
- Encabezados HTTP.
- Cookies sin protección.
- Información enviada mediante formularios.
- Datos personales si el sitio no utiliza cifrado.

Además, un atacante podría realizar un ataque **Man-in-the-Middle (MitM)** para interceptar o modificar la comunicación entre el usuario y el servidor.

Otro riesgo importante consiste en conectarse a una red **Evil Twin**, creada por un atacante con un nombre similar al de la red legítima para engañar a los usuarios.

---

# ¿Cómo ayuda una VPN?

Una **VPN (Virtual Private Network)** protege la comunicación creando un **túnel seguro** entre el dispositivo del usuario y un servidor VPN.

Todo el tráfico viaja mediante **cifrado**, por lo que aunque un atacante capture los paquetes en una red Wi-Fi pública, únicamente observará información cifrada e ilegible.

Además, la VPN realiza un **encapsulamiento** del tráfico de red, ocultando gran parte de la información que normalmente podría observarse durante una conexión HTTP.

Entre sus principales ventajas se encuentran:

- Cifrado de los datos transmitidos.
- Protección frente al sniffing.
- Mayor privacidad al ocultar la dirección IP pública.
- Reducción del riesgo en redes Wi-Fi públicas.

---

# Comparación entre HTTP y HTTPS

| HTTP | HTTPS |
|------|-------|
| No utiliza cifrado. | Utiliza cifrado TLS. |
| La información puede ser leída por terceros. | La información viaja protegida. |
| Mayor riesgo de robo de datos. | Mayor protección de la privacidad. |
| Vulnerable a ataques de interceptación. | Reduce significativamente estos riesgos. |

---

# 3 Reglas de Oro para usar redes Wi-Fi públicas

## 1. Evitar ingresar información sensible en sitios HTTP

Antes de introducir contraseñas o datos personales, verificar que el sitio utilice **HTTPS** y que la conexión sea segura.

---

## 2. Utilizar una VPN

Siempre que sea posible, activar una VPN para que todo el tráfico viaje mediante un **túnel cifrado**, especialmente al utilizar redes Wi-Fi públicas.

---

## 3. Verificar la autenticidad de la red

Confirmar con el establecimiento el nombre correcto de la red Wi-Fi antes de conectarse y evitar redes con nombres similares que puedan corresponder a ataques **Evil Twin**.

---

# Conclusión

El análisis permitió comprobar que el protocolo HTTP transmite la información sin cifrado, lo que facilita la interceptación del tráfico en redes públicas. Durante la inspección fue posible observar datos como el método HTTP, la URL solicitada, el host y los encabezados enviados por el navegador.

También se comprobó que el uso de una VPN mejora significativamente la seguridad al proteger la comunicación mediante **cifrado**, **encapsulamiento** y un **túnel seguro**, dificultando que terceros puedan acceder a la información transmitida.

La combinación de HTTPS, una VPN y buenas prácticas de navegación constituye una estrategia efectiva para reducir los riesgos asociados al uso de redes Wi-Fi públicas.
