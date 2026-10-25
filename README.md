![Juan David Villota — Ingeniería Electrónica, UNAL Manizales](https://capsule-render.vercel.app/api?type=waving&color=0:0B1220,55:0F2A3F,100:0E7490&height=200&section=header&text=Juan%20David%20Villota&fontSize=44&fontColor=E2E8F0&fontAlignY=38&desc=Ingenier%C3%ADa%20Electr%C3%B3nica%20%C2%B7%20UNAL%20Manizales&descAlignY=58&descSize=15&animation=fadeIn)

**Hardware, firmware y sistemas embebidos.**

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/juan-david-villota-bernal-7929573ba)
[![Gmail](https://img.shields.io/badge/Gmail-EA4335?style=flat&logo=gmail&logoColor=white)](mailto:juanda7031@gmail.com)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat&logo=github&logoColor=white)](https://github.com/juan-villota-b)

---

## 📓 Perfil

Estudiante de **Ingeniería Electrónica** (VIII semestre) en la **Universidad Nacional de Colombia, Sede Manizales**. Documento proyectos y las decisiones técnicas detrás.

---

## 📚 Proyectos

### 🖊️ Mini CNC: dónde se pierde la precisión

`STM32F030` `ESP32-C3` `G-code` `Flask`

**Descripción:** CNC de 3 ejes para dibujo con G-code, calibración manual y dashboard web.

**Arquitectura:** Flask → ESP32-C3 (WiFi / HTTP / SPIFFS) → UART 115 200 baud → STM32F030 (Bresenham, half-stepping) → 3× 28-BYJ48.

El reto no es el motor, sino la suma de errores pequeños.

- **Bresenham** reparte los pasos entre X e Y sin calcular punto por punto.
- **Backlash:** sin compensarlo, cada cambio de dirección deja un error sistemático.
- **Handshake línea a línea:** esperar `ok` evita desbordar el buffer del STM32.

**Aprendizaje:** la precisión se pierde en la interpolación, el origen y el protocolo, no solo en la mecánica.

[Repositorio →](https://github.com/juan-villota-b/Mini-CNC-para-dibujo)

### 🌱 Granja IoT: qué vive en el borde y qué en el SCADA

`ESP32-C6` `Thread` `CoAP / CBOR` `ThingsBoard`

**Descripción:** Red de sensores y riego automático para agricultura de precisión, con telemetría e históricos.

**Arquitectura:** 4× ESP32-C6 (Thread) → OTBR en Raspberry Pi 4 → bridge CoAP/CBOR → MQTT → ThingsBoard Edge → ThingsBoard CE (SCADA).

- **Borde:** OTBR, ThingsBoard Edge, PostgreSQL y el bridge; el riego sigue operando si se cae la red.
- **SCADA:** el servidor central supervisa, historia y permite comandos manuales; no sostiene el lazo de control.
- **Escala:** un edge por finca y multi-tenant; repetir el despliegue es configuración, no reescritura.

**Aprendizaje:** si el control crítico depende de la nube, el sistema falla cuando falla la red.

[Repositorio →](https://github.com/juan-villota-b/Granja-IoT-col)

### ⚙️ Buck digital: por qué un PI no siempre alcanza

`STM32G4` `HRTIM 200 kHz` `3p3z` `MQTT / TLS`

**Descripción:** Buck síncrono con lazo digital 3p3z, telemetría y setpoint remoto.

**Arquitectura:** STM32G474RE (HRTIM 200 kHz + ADC / DMA + 3p3z) y variante ESP32-C6 (MCPWM + ADC + 3p3z a 10 kHz + MQTT / TLS).

- **3p3z, no PI:** permite ubicar polos y ceros para cumplir margen de fase y ancho de banda en una planta de segundo orden.
- **Frecuencia:** 200 kHz de conmutación en el STM32G474RE; lazo a 10 kHz en el ESP32-C6. Más rápido no siempre es mejor: el ruido y el retardo desestabilizan.
- **Control en el MCU:** HRTIM + ADC + DMA en el STM32 reduce latencia y *jitter* frente a un lazo externo.

**Aprendizaje:** el modelo ideal miente. Sin ESR, DCR y Rds(on), la simulación se ve perfecta y la respuesta real es otra; el osciloscopio decide.

[STM32G474RE →](https://github.com/juan-villota-b/EPOT-STM32-Buck_voltage) · [ESP32-C6 →](https://github.com/juan-villota-b/buck-controller)

**Otros:** [RTL-SDR](https://github.com/juan-villota-b/LAB-SDR-DEMO-FM) · [UART-WEB](https://github.com/juan-villota-b/UART-WEB_LAB) · [OTBR nRF52840](https://github.com/juan-villota-b/Promicro-nrf52840-otbr-rcp-guide) · [Room Control](https://github.com/juan-villota-b/Room_Control_Final_2025_2) · [Robótica ROS 2](https://github.com/juan-villota-b/Robotica-unal-informes)

---

## 🧰 Habilidades

- **IoT:** nodos de bajo consumo, Thread / 6LoWPAN, CoAP / CBOR, MQTT y gateways edge.
- **Diseño de hardware:** esquemático, layout, acondicionamiento, aislamiento, presupuesto de potencia y protecciones.
- **Arquitectura de firmware:** C bare-metal, HAL, FreeRTOS, máquinas de estado, ADC + DMA y HRTIM / MCPWM.
- **Agentes de IA:** datasheets, scaffolding y pruebas con herramientas (PDFs, Git, serial); validación en banco.
- **Linux:** desarrollo, Docker, scripts y despliegue en Raspberry Pi.

---

## 🛠️ Herramientas

![C, C++, Python, Bash, Linux, Git y GitHub](https://skillicons.dev/icons?i=c,cpp,python,bash,linux,git,github)

![Raspberry Pi, ROS, Docker, FastAPI, PostgreSQL, CMake y LaTeX](https://skillicons.dev/icons?i=raspberrypi,ros,docker,fastapi,postgres,cmake,latex)

![ESP-IDF](https://img.shields.io/badge/ESP--IDF-E7352C?style=flat&logo=espressif&logoColor=white)
![STM32](https://img.shields.io/badge/STM32-03234B?style=flat&logo=stmicroelectronics&logoColor=white)
![FreeRTOS](https://img.shields.io/badge/FreeRTOS-2E7D32?style=flat)
![KiCad](https://img.shields.io/badge/KiCad-314CB0?style=flat&logo=kicad&logoColor=white)
![Altium Designer](https://img.shields.io/badge/Altium_Designer-7A5C2E?style=flat)
![MQTT](https://img.shields.io/badge/MQTT-660066?style=flat&logo=mqtt&logoColor=white)

SPI · I²C · UART · RS-485 · Modbus RTU · MQTT / TLS · CoAP / CBOR · Thread / 6LoWPAN · Wi-Fi HaLow

---

## 🎓 Formación

**Ingeniería Electrónica** · Universidad Nacional de Colombia — Sede Manizales · VIII semestre

Cursos: estructuras computacionales, robótica (ROS 2), IoT (Thread / CoAP), electrónica de potencia, diseño electrónico y procesamiento digital de señales.

---

## 📫 Contacto

[![Gmail](https://img.shields.io/badge/juanda7031@gmail.com-EA4335?style=flat&logo=gmail&logoColor=white)](mailto:juanda7031@gmail.com)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/juan-david-villota-bernal-7929573ba)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat&logo=github&logoColor=white)](https://github.com/juan-villota-b)
