# LABORATORIO 6: SIMULACIÓN Y MONITOREO DE VARIABLES CARDIOVASCULARES Y EMODIMÁMICAS

### ***Instrumentación Biomédica y Biosensores***
### ***Ana María Abril***
### ***Leidy Valentina Rodríguez***

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

***Figura 1. Monitor de signos vitales Mindray uMEC 100 encendido en modo Monitor***

El monitor uMEC 100 de Mindray es un equipo multiparamétrico de cuidados intermedios. Incorpora módulos para ECG, SpO₂, capnografía y presión no invasiva, y cuenta con un sistema de alarmas configurable por parámetro con niveles de prioridad alta, media y baja. La pantalla muestra en tiempo real la onda fotopletismográfica (Plet), el valor numérico de SpO₂ y la frecuencia de pulso (FP).

### Pronk OxSim OX-1

<img width="480" height="360" alt="WhatsApp Image 2026-05-27 at 12 52 01 PM (10)" src="https://github.com/user-attachments/assets/86026502-dbf3-4995-8990-dd4c12d9eec0" />

***Figura 2. Simulador de parámetros hemodinámicos Pronk OxSim OX-1***

El Pronk OxSim OX-1 es un simulador compacto de parámetros de pulsioximetría que emite señales ópticas calibradas para reproducir diferentes combinaciones de SpO₂ y FC. Dispone de cinco modos de simulación seleccionables mediante un pulsador frontal y es compatible con sensores de las marcas Masimo, Nellcor y otros.

## 4. PARTE A
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

***Tabla 1. Modos de operación del simulador Pronk OxSim OX-1***

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

***Tabla 2. Errores Máximos Permitidos (EMP) según normas internacionales***

| Parámetro | EMP | Norma | Observación |
| :--- | :---: | :---: | :--- |
| SpO₂ | ± 2 % (rango 70–100%) | ISO 80601-2-61:2017 | Error de exactitud raíz cuadrada media (Arms ≤ 3%) ante condiciones estáticas con hemoglobina normal. |
| FC / FP | ± 3 bpm o ± 3% (el mayor) | IEC 60601-2-27:2011 | Aplica en rango de 15–300 bpm para monitores cardíacos de diagnóstico. |

Estos límites son de particular importancia en el contexto de metrología biomédica, ya que definen el criterio de aceptación o rechazo de un equipo durante las verificaciones periódicas. En Colombia, la normativa del INVIMA exige que los equipos de monitoreo de signos vitales cumplan con estas especificaciones para su comercialización y uso clínico.

## 5. PARTE B — Procedimiento Experimental y Resultado

### 5.1 Tabla de Verificación de Alarmas

Se construyó la siguiente tabla de verificación, registrando para cada escenario el límite de alarma configurado en el uMEC 100, el valor simulado por el OxSim OX-1, el valor efectivamente medido por el monitor, la activación de la alarma y el tiempo de respuesta aproximado:

***Tabla 3. Verificación de alarmas del monitor uMEC 100***

| # | Condición Simulada | Parámetro | Límite Configurado | Valor Simulado | Valor Medido uMEC100 | ¿Alarma Activa? | T. Respuesta |
| :---: | :--- | :---: | :---: | :---: | :---: | :--- | :---: |
| **1** | Bradicardia<br>40 bpm,<br>SpO₂=95% | FC (ppm) | Bajo: 50 bpm | 40 bpm | 40 ppm | **SÍ — !!FP baja <50** | < 5 s |
| **2** | Hipoxemia<br>80 bpm,<br>SpO₂=85% | SpO₂ (%) | Bajo: 90% | 85% | 85% | **SÍ — !!SpO₂ bajo <90** | ~8 s |
| **3** | Low Perfusion<br>SpO₂=99%,<br>~80 bpm | SpO₂ (%) | Alto: 97% | 99% | 100% | **SÍ — !!SpO₂ alto >97** | < 5 s |
| **4** | Taquicardia<br>140 bpm,<br>SpO₂=98% | FC (ppm) | Alto: 120 bpm | 140 bpm | 140 ppm | **SÍ — !!FP alta >120** | < 5 s |

### 5.2 Simulación de Bradicardia (40 bpm, SpO₂ = 95%)

Se configuró el OxSim en el Modo 2 (SpO₂ = 95%, FC = 40 bpm). El monitor uMEC 100 registró los valores mostrados a continuación. La alarma de FP baja se activó al ser 40 ppm inferior al umbral configurado de 50 bpm.

<img width="480" height="360" alt="WhatsApp Image 2026-05-27 at 12 52 01 PM (3)" src="https://github.com/user-attachments/assets/fc7a36b2-e0ed-4894-b6bd-9f13191692db" />

***Figura 3. uMEC 100 con bradicardia simulada***

La onda fotopletismográfica en bradicardia muestra picos bien definidos, con mayor separación temporal entre sí (~1.5 s entre pulsos), lo que corresponde a una frecuencia de ~40 bpm. La morfología de la onda es preservada y simétrica, indicando buena perfusión a pesar de la baja frecuencia.

***Tabla 4. Errores de medición — Modo 2: Bradicardia (40 bpm, SpO₂ = 95%)***

| Parámetro | V. Simulado | V. Medido | Error Abs. | Error % | EMP | ¿Dentro EMP? |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| FC (Frecuencia cardíaca) | 40 bpm | 40 ppm | 0 bpm | 0.0% | ±3 bpm | **✓ Dentro** |
| SpO₂ (Saturación O₂) | 95% | 96% | 1% | 1.05% | ±2% | **✓ Dentro** |

Fórmulas aplicadas: Error absoluto = |Valor simulado − Valor medido|  /  Error porcentual = (Error absoluto / Valor simulado) × 100%.
Para la FC, el monitor midió exactamente 40 ppm (error = 0 bpm, 0.0%). Para la SpO₂, el monitor registró 96% frente al 95% simulado, resultando en un error absoluto de 1% y un error porcentual de 1.05%. Ambos valores se encuentran dentro de los EMP internacionales.

### 5.3 Configuración de Alarmas

Se configuraron los límites de alarma de SpO₂ y FC/FP en el uMEC 100:

•	Límite inferior de SpO₂: 90% (prioridad Media)

•	Límite superior de SpO₂: 97%

•	Límite inferior FC/FP: 50 bpm

•	Límite superior FC/FP: 120 bpm

<img width="480" height="360" alt="image" src="https://github.com/user-attachments/assets/1dcfb86f-62aa-47cb-b87d-642f698eb489" />

***Figura 4. Pantalla de configuración de alarmas de SpO₂: Límite Alto = 100%, Límite Bajo = 90%***

### 5.4 Simulación de Hipoxemia (80 bpm, SpO₂ = 85%)

Se ajustó el OxSim al Modo 1 (SpO₂ = 85%, FC = 80 bpm). Con el límite inferior de SpO₂ configurado en 90%, el monitor activó la alarma !!SpO₂ bajo < 90 a los aproximadamente 8 segundos de iniciada la simulación.

<img width="480" height="360" alt="WhatsApp Image 2026-05-27 at 12 52 01 PM (7)" src="https://github.com/user-attachments/assets/0ade43e3-a32c-4c55-9e46-3c1e11fb86c0" />

***Figura 5. uMEC 100 con hipoxemia simulada***

***Tabla 5. Errores de medición — Modo 1: Hipoxemia (80 bpm, SpO₂ = 85%)***

| Parámetro | V. Simulado | V. Medido | Error Abs. | Error % | EMP | ¿Dentro EMP? |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| FC (Frecuencia cardíaca) | 80 bpm | 80 ppm | 0 bpm | 0.0% | ±3 bpm | **✓ Dentro** |
| SpO₂ (Saturación O₂) | 85% | 85% | 0% | 0.0% | ±2% | **✓ Dentro** |

En este modo, el monitor registró exactamente los valores simulados (FC = 80 ppm, SpO₂ = 85%), resultando en errores absolutos de 0 bpm y 0%, respectivamente. Este escenario representa la condición de mayor riesgo clínico entre los evaluados, dado que una SpO₂ de 85% indica hipoxemia severa.

### 5.5 Simulación en Modo Low Perfusion (SpO₂ = 99%)

Se configuró el límite superior de SpO₂ en 97% y se ajustó el OxSim al Modo 5 (Low Perfusion, SpO₂ = 99%). El monitor registró SpO₂ = 100% y activó la alarma !!SpO₂ alto > 97 en menos de 5 segundos.

<img width="480" height="360" alt="WhatsApp Image 2026-05-27 at 12 52 01 PM (14)" src="https://github.com/user-attachments/assets/cdf3bfb0-4178-4b50-9093-5ff9f2356f45" />

***Figura 6. uMEC 100 con low perfusion simulada***

La onda fotopletismográfica sí se distorsiona en el modo Low Perfusion: presenta amplitud reducida y variabilidad en la morfología, replicando la señal débil de un paciente con mala perfusión periférica. A pesar de la baja amplitud de la señal AC, el monitor logró calcular SpO₂ y FC correctamente.

***Tabla 6. Errores de medición — Modo 5: Low Perfusion (SpO₂ = 99%, FC ≈ 80 bpm)***

| Parámetro | V. Simulado | V. Medido | Error Abs. | Error % | EMP | ¿Dentro EMP? |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| FC (Frecuencia cardíaca) | 80 bpm | 80 ppm | 0 bpm | 0.0% | ±3 bpm | **✓ Dentro** |
| SpO₂ (Saturación O₂) | 99% | 100% | 1% | 1.01% | ±2% | **✓ Dentro** |

El error en SpO₂ fue de 1% (valor simulado 99%, medido 100%), con error porcentual de 1.01%, dentro del EMP de ±2%. La FC no presentó error.

### 5.6 Simulación de Taquicardia (140 bpm, SpO₂ = 98%)

Se ajustó el OxSim al Modo 4 (SpO₂ = 98%, FC = 140 bpm). El monitor uMEC 100 registró FC = 140 ppm y SpO₂ = 98–99%, activando dos alarmas simultáneas: !!FP alta > 120 y !!SpO₂ alto > 97.

<img width="480" height="360" alt="WhatsApp Image 2026-05-27 at 12 52 01 PM (18)" src="https://github.com/user-attachments/assets/a1b1351d-f215-4965-adbf-0c1e0cc985c0" />

***Figura 7. uMEC 100 con low taquicardia simulada***

La onda fotopletismográfica en taquicardia muestra picos frecuentes (~0.43 s entre pulsos), de menor amplitud relativa y patrón prácticamente sinusoidal de alta frecuencia, consistente con el valor simulado. La alarma de FC elevada se disparó correctamente dado que 140 bpm > 120 bpm (límite configurado).

***Tabla 7. Errores de medición — Modo 4: Taquicardia (140 bpm, SpO₂ = 98%)***

| Parámetro | V. Simulado | V. Medido | Error Abs. | Error % | EMP | ¿Dentro EMP? |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| FC (Frecuencia cardíaca) | 140 bpm | 140 ppm | 0 bpm | 0.0% | ±3 bpm | **✓ Dentro** |
| SpO₂ (Saturación O₂) | 98% | 98-99% | 0-1% | 0-1.02% | ±2% | **✓ Dentro** |

La FC fue medida con error de 0 bpm. La SpO₂ osciló entre 98% y 99% (error de 0–1%, dentro del EMP). Las dos alarmas activadas simultáneamente (FP alta y SpO₂ alto) confirman el correcto funcionamiento del sistema de alertas del monitor bajo condiciones de taquicardia con alta saturación.

## 6. ANÁLISIS DE RESULTADOS
   
### 6.1 Análisis Estadístico de Errores de Medición

A continuación se presenta el análisis estadístico de los errores obtenidos en SpO₂ a lo largo de los cuatro escenarios de simulación:

•	Valores de error absoluto en SpO₂: 1%, 0%, 1%, 0–1% → Media = 0.5%, Desviación estándar ≈ 0.5 puntos porcentuales.

•	Valores de error absoluto en FC: 0 bpm en todos los escenarios → Media = 0 bpm, Desviación estándar = 0 bpm.

•	Error porcentual máximo observado: 1.05% (SpO₂ en bradicardia: valor simulado 95%, medido 96%).

Todos los errores se encuentran por debajo del EMP de ±2% para SpO₂ (ISO 80601-2-61) y ±3 bpm para FC (IEC 60601-2-27). La exactitud del uMEC 100 para FC fue perfecta (0 bpm de error) en todos los escenarios, lo que indica que el algoritmo de detección de pulso del monitor es altamente preciso ante señales de simulación controladas.

El ligero error en SpO₂ (1% en bradicardia y Low Perfusion) puede atribuirse a la curva de calibración empírica del monitor, que aproxima la relación R-SpO₂ con una función polinómica basada en estudios con voluntarios humanos. Pequeñas diferencias en la relación óptica generada por el simulador respecto a la que produciría un dedo real pueden resultar en desviaciones de ±1% en la lectura, lo cual es esperado y aceptable.

6.2 Relación entre la Onda Fotopletismográfica y los Parámetros FC/SpO₂

La señal Plet registrada en el uMEC 100 mostró una correlación directa con los parámetros hemodinámicos simulados:

•	Bradicardia (40 bpm): Picos amplios, bien definidos y con mayor separación temporal (~1.5 s entre picos). Morfología regular y simétrica. La FC se deriva directamente del período entre picos.

•	Hipoxemia (85% SpO₂, 80 bpm): Picos de frecuencia normal y morfología regular. La SpO₂ disminuida no afecta la morfología de la onda Plet, ya que esta refleja variaciones de volumen y no la oxigenación per se.

•	Low Perfusion (99% SpO₂): Amplitud AC reducida y variabilidad morfológica. El monitor señaló baja confiabilidad mediante el índice de perfusión reducido. A pesar de la señal débil, la lectura de SpO₂ y FC fue correcta.

•	Taquicardia (140 bpm): Picos frecuentes (~0.43 s entre pulsos), amplitud menor, patrón sinusoidal de alta frecuencia. El tiempo diastólico reducido se refleja en la forma de la onda.

La frecuencia de la onda Plet corresponde exactamente a la FC/FP medida, validando que el monitor extrae la frecuencia de pulso directamente del período de la señal fotopletismográfica cuando el módulo ECG no está disponible.

 
## 7. PREGUNTAS PARA LA DISCUSIÓN

### Pregunta 1: ¿Cuál es el principio de operación del Pronk OxSim OX-1 para simular una onda pulsátil?

El OxSim OX-1 opera generando dos señales luminosas moduladas: una en el espectro infrarrojo (~940 nm) y otra en el espectro rojo (~660 nm), a través de diodos emisores de luz (LEDs). La intensidad de cada señal se modula de forma temporal para imitar la variación pulsátil del volumen sanguíneo que ocurre en el lecho capilar con cada latido cardíaco.

El sensor de SpO₂ del monitor, al colocarse sobre el simulador, mide la atenuación de ambas longitudes de onda y calcula el índice R según la ecuación:

R = (AC₆₆₀ / DC₆₆₀) / (AC₉₄₀ / DC₉₄₀)

Donde AC representa el componente pulsátil (alternante) de la señal y DC el componente continuo (luz constante). El simulador programa electrónicamente la relación entre AC y DC para generar el valor de R correspondiente a cada nivel de SpO₂, basándose en las curvas de calibración empíricas conocidas. La frecuencia de modulación temporal de la señal AC determina la FC simulada. En el modo Low Perfusion, la amplitud AC se reduce significativamente para replicar la débil señal pulsátil de un paciente con mala perfusión periférica.

### Pregunta 2: ¿Por qué la SpO₂ baja puede ser un falso positivo (falsa alarma) en una situación de mala perfusión?

En situaciones de mala perfusión periférica — como hipotensión, vasoconstricción por frío, shock hipovolémico o uso de vasoconstrictores — el flujo sanguíneo en el lecho capilar distal (dedo, lóbulo de la oreja) se reduce significativamente. Esto provoca que la señal pulsátil AC detectada por el pulsioxímetro sea muy pequeña en relación al componente de fondo DC, resultando en una relación señal/ruido (SNR) muy baja.

Con una SNR baja, el denominador del índice R (DC₆₆₀ y DC₉₄₀) permanece relativamente estable mientras que los numeradores AC₆₆₀ y AC₉₄₀ son afectados por ruido (luz ambiental, artefactos de movimiento, electrónica del sensor). Esto desvía el cálculo de R hacia valores más altos o erráticos que, según la curva de calibración empírica, se traducen en lecturas de SpO₂ artificialmente más bajas. De este modo, el monitor puede reportar una SpO₂ disminuida (por ejemplo, 85–90%) cuando la saturación arterial real del paciente es normal (95–99%).

Esta es la razón por la cual en la práctica clínica se recomienda siempre correlacionar la lectura de SpO₂ con el índice de perfusión que muestra el monitor (amplitud de la barra Plet): una SpO₂ baja acompañada de un índice de perfusión bajo debe interpretarse con cautela y confirmarse con otros métodos (gasometría arterial, ECG) antes de intervenir. El modo "Low Perfusion" del OxSim OX-1 replica exactamente este escenario, siendo especialmente útil para verificar que el monitor advierta al operador sobre la posible falta de confiabilidad de la medición.

## 8. CONCLUSIONES 
- El monitor uMEC 100 cumple con los estándares metrológicos internacionales (ISO 80601-2-61 e IEC 60601-2-27), registrando errores de FC de 0 bpm y errores de SpO₂ máximos de 1% en todos los escenarios, lo que lo acredita como apto para uso clínico.

- El sistema de alarmas funcionó correctamente en los cuatro escenarios simulados, aunque la mayor latencia observada en hipoxemia (~8 s frente a <5 s en los demás casos) indica que el algoritmo del monitor pondera con mayor cautela las caídas de SpO₂ para evitar falsas alarmas.

- El modo Low Perfusion demostró que una señal pulsátil de baja amplitud no impide el cálculo correcto de SpO₂ y FC, pero sí introduce una pequeña deriva en la lectura (+1%), lo que confirma la importancia clínica de correlacionar siempre el valor numérico de SpO₂ con el índice de perfusión antes de tomar decisiones terapéuticas.

- El simulador Pronk OxSim OX-1 demostró ser una herramienta confiable y reproducible para la verificación funcional de monitores de signos vitales, permitiendo replicar condiciones patológicas controladas sin exponer pacientes reales, lo que valida su uso como instrumento estándar en programas de mantenimiento preventivo y metrología biomédica hospitalaria.
