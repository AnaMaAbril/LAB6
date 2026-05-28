
## 1. INTRODUCCIÓN
---

En el contexto clínico actual, el monitoreo continuo y fiable de variables fisiológicas — especialmente la frecuencia cardíaca (FC) y la saturación periférica de oxígeno (SpO₂) — es indispensable para detectar de forma oportuna condiciones que pueden representar un peligro inmediato para la vida del paciente, tales como arritmias, bradiarritmias, taquiarritmias e hipoxia. Los monitores de signos vitales deben ser capaces no solo de registrar estos parámetros de forma precisa, sino también de generar alarmas audibles y visuales cuando los valores excedan los límites fisiológicos configurados por el clínico.

Para verificar el correcto funcionamiento de estos equipos sin necesidad de exponer a pacientes reales, se emplean simuladores de señales biomédicas. El simulador Pronk OxSim OX-1, distribuido en Colombia por Medical IT, permite recrear de manera controlada diferentes condiciones fisiológicas y patológicas (bradicardia, taquicardia, hipoxemia y baja perfusión), generando la señal óptica que el sensor de pulsioximetría del monitor interpreta como si proviniese de un dedo real.

La presente práctica evaluó el desempeño del monitor Mindray uMEC 100 ante cuatro escenarios de simulación, verificando tanto la precisión de sus medidas frente a los valores de referencia del OxSim como la correcta y oportuna activación de sus alarmas configuradas. Este tipo de evaluación es parte fundamental del mantenimiento preventivo y la metrología de equipos biomédicos, y tiene soporte normativo en estándares internacionales como la ISO 80601-2-61 para pulsioxímetros y la IEC 60601-2-27 para monitores cardíacos.

## 2. OBJETIVOS
---
### 2.1 Objetivo General
Operar el simulador Pronk OxSim OX-1 y el monitor de signos vitales Mindray uMEC 100 para realizar pruebas funcionales de verificación de alarmas y precisión de medición de parámetros hemodinámicos.
### 2.2 Objetivos Específicos
•	Identificar los modos de operación del simulador Pronk OxSim OX-1 y los parámetros fisiológicos que permite simular.
•	Verificar los límites de medición del monitor uMEC 100 mediante simulación de variables hemodinámicas bajo condiciones fisiológicas y patológicas.
•	Calcular los errores absolutos y porcentuales entre los valores simulados por el OxSim OX-1 y los valores medidos por el uMEC 100, comparándolos con los Errores Máximos Permitidos (EMP) establecidos por normas internacionales.
•	Interpretar las variaciones en la onda fotopletismográfica asociadas a diferentes estados fisiológicos y patológicos.
•	Documentar la práctica de forma estructurada en un repositorio de GitHub.

## 3. EQUIPOS UTILIZADOS
---
### Monitor uMEC 100

<img width="480" height="360" alt="WhatsApp Image 2026-05-27 at 12 52 01 PM (4)" src="https://github.com/user-attachments/assets/fd3791bf-4056-443e-b559-41ff4054b533" />

_Figura 1. Monitor de signos vitales Mindray uMEC 100 encendido en modo Monitor_

El monitor uMEC 100 de Mindray es un equipo multiparamétrico de cuidados intermedios. Incorpora módulos para ECG, SpO₂, capnografía y presión no invasiva, y cuenta con un sistema de alarmas configurable por parámetro con niveles de prioridad alta, media y baja. La pantalla muestra en tiempo real la onda fotopletismográfica (Plet), el valor numérico de SpO₂ y la frecuencia de pulso (FP).

### Pronk OxSim OX-1

<img width="480" height="360" alt="WhatsApp Image 2026-05-27 at 12 52 01 PM (10)" src="https://github.com/user-attachments/assets/86026502-dbf3-4995-8990-dd4c12d9eec0" />

_Figura 2. Simulador de parámetros hemodinámicos Pronk OxSim OX-1_

El Pronk OxSim OX-1 es un simulador compacto de parámetros de pulsioximetría que emite señales ópticas calibradas para reproducir diferentes combinaciones de SpO₂ y FC. Dispone de cinco modos de simulación seleccionables mediante un pulsador frontal y es compatible con sensores de las marcas Masimo, Nellcor y otros.

## Parte A
---
### 4.1 Modo "Monitor" en el uMEC 100
Para colocar el uMEC 100 en modo Monitor se sigue el siguiente procedimiento, según el manual de operación del equipo:
1.	Encender el equipo presionando el botón de encendido ubicado en el panel frontal.
2.	En la pantalla de inicio, seleccionar el perfil de paciente (Adulto, Pediátrico o Neonato según corresponda).
3.	Verificar que en la barra superior de la pantalla aparezca la leyenda "Monitor", indicando que el dispositivo se encuentra en modo de monitoreo continuo en tiempo real.
4.	El equipo queda activo para recibir señales de los sensores conectados y visualizar las formas de onda, valores numéricos y alarmas.
En el modo Monitor, el uMEC 100 actualiza las lecturas de SpO₂ y FC cada ciclo de pulso y activa las alarmas configuradas cuando los valores salen de los rangos establecidos.

### 4.2 Parámetros Simulables con el Pronk OxSim OX-1

El simulador OxSim OX-1 dispone de cinco modos de operación que permiten reproducir diferentes condiciones hemodinámicas. Cada modo genera una combinación específica de SpO₂ y FC, como se resume en la tabla siguiente:

_Tabla 1. Modos de operación del simulador Pronk OxSim OX-1_

| Modo | SpO₂ (%) | FC (bpm) | Condición | Descripción clínica |
| :---: | :---: | :---: | :---: | :--- |
| **1** | 85% | 80 bpm | Hipoxemia moderada | SpO₂ bajo umbral fisiológico (< 90%), frecuencia cardíaca normal. Simula situación de hipoxemia moderada con posible riesgo de hipoxia tisular. |
| **2** | 95% | 40 bpm | Bradicardia marcada | SpO₂ normal-bajo, frecuencia cardíaca muy reducida (< 60 bpm = bradicardia). Simula situaciones como bloqueo cardíaco, hipotiroidismo severo o efectos de fármacos. |
| **3** | 98% | 80 bpm | Estado normal (ref.) | Condición fisiológica de referencia. SpO₂ y FC dentro de rangos normales. Útil para verificar la línea base del monitor. |
| **4** | 98% | 140 bpm | Taquicardia | SpO₂ normal, frecuencia cardíaca elevada (> 100 bpm = taquicardia). Simula estados como estrés, fiebre, hipovolemia o taquicardia supraventricular. |
| **5** | 99% | ~80 bpm | Low Perfusion | SpO₂ alta pero con amplitud de señal pulsátil reducida. Simula mala perfusión periférica (vasoconstricción, hipotensión, shock). Permite verificar el comportamiento del monitor ante señal débil. |

El dispositivo opera emitiendo luz en dos longitudes de onda: infrarrojo (~940 nm) y rojo (~660 nm). La relación de absorción entre ambas longitudes de onda es la base del cálculo de la SpO₂ en el monitor. La modulación temporal de estas emisiones reproduce la señal pulsátil a la frecuencia cardíaca programada.

Los parámetros que simula son:

•	SpO₂ (Saturación periférica de oxígeno): Porcentaje de hemoglobina saturada con oxígeno. Valores normales en adultos: 95–100%. El simulador genera la relación óptica R correspondiente a cada nivel programado.
•	FC / FP (Frecuencia cardíaca / Frecuencia de pulso): Número de pulsos por minuto derivados de la onda pletismográfica. Normal en adulto en reposo: 60–100 bpm. El OxSim modula la señal a la frecuencia definida para cada modo.
•	Onda fotopletismográfica (Plet): Señal que representa los cambios de volumen en el lecho capilar con cada latido. Su amplitud, forma y frecuencia varían según el modo simulado. En Low Perfusion, la amplitud AC se reduce deliberadamente para imitar baja perfusión periférica.

### 4.3 Tolerancias o Errores Máximos Permitidos (EMP) Clínicos

Los errores máximos permitidos para equipos de pulsioximetría y monitoreo cardíaco están establecidos por estándares internacionales de la siguiente manera:

_Tabla 2. Errores Máximos Permitidos (EMP) según normas internacionales_

| Parámetro | EMP | Norma | Observación |
| :--- | :---: | :---: | :--- |
| SpO₂ | ± 2 % (rango 70–100%) | ISO 80601-2-61:2017 | Error de exactitud raíz cuadrada media (Arms ≤ 3%) ante condiciones estáticas con hemoglobina normal. |
| FC / FP | ± 3 bpm o ± 3% (el mayor) | IEC 60601-2-27:2011 | Aplica en rango de 15–300 bpm para monitores cardíacos de diagnóstico. |
