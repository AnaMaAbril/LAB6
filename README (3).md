# Laboratorio 5 — Simulación y Monitoreo de Variables Cardiovasculares y Hemodinámicas

**Universidad Militar Nueva Granada**  
**Facultad de Ingeniería — Programa: Ingeniería Biomédica**  
**Asignatura:** Instrumentación Biomédica y Biosensores — Semestre VII  
**Fecha:** 27 de mayo de 2026

---

## Tabla de Contenidos

1. [Introducción](#1-introducción)
2. [Objetivos](#2-objetivos)
3. [Equipos Utilizados](#3-equipos-utilizados)
4. [Parte A — Revisión Bibliográfica](#4-parte-a--revisión-bibliográfica)
5. [Parte B — Procedimiento Experimental y Resultados](#5-parte-b--procedimiento-experimental-y-resultados)
6. [Tabla de Verificación de Alarmas](#6-tabla-de-verificación-de-alarmas)
7. [Tabla de Errores de Medición](#7-tabla-de-errores-de-medición)
8. [Análisis de Resultados](#8-análisis-de-resultados)
9. [Preguntas para la Discusión](#9-preguntas-para-la-discusión)
10. [Conclusiones](#10-conclusiones)
11. [Bibliografía](#11-bibliografía)

---

## 1. Introducción

En el contexto clínico, el monitoreo continuo de variables fisiológicas como la frecuencia cardíaca (FC) y la saturación periférica de oxígeno (SpO₂) es fundamental para detectar estados que representen un riesgo inmediato para el paciente, tales como arritmias e hipoxia. Los monitores de signos vitales deben ser capaces de generar alarmas cuando estos parámetros superan los límites fisiológicos aceptables.

Para verificar el correcto funcionamiento de estos dispositivos, se emplean simuladores de señales biomédicas como el **Pronk OxSim OX-1**, que permiten recrear condiciones fisiológicas y patológicas controladas. Esta práctica evaluó el desempeño del monitor **Mindray uMEC 100** ante diferentes escenarios simulados, verificando la precisión de sus mediciones y la correcta activación de sus alarmas.

---

## 2. Objetivos

**General:** Operar el simulador Pronk OxSim (OX-1) y el monitor de signos vitales uMEC 100 para realizar pruebas funcionales de verificación de alarmas y precisión de medición.

**Específicos:**
- Identificar los modos de operación del simulador Pronk OxSim OX-1.
- Verificar los límites de medición del uMEC 100 mediante simulación de variables hemodinámicas.
- Interpretar variaciones en los parámetros hemodinámicos asociadas a estados fisiológicos y patológicos.
- Calcular los errores absoluto y porcentual entre los valores simulados y los medidos por el monitor.

---

## 3. Equipos Utilizados

| Equipo | Descripción |
|--------|-------------|
| **Mindray uMEC 100** | Monitor de signos vitales con sensor de SpO₂ (pulsioximetría) |
| **Pronk OxSim OX-1** | Simulador de parámetros hemodinámicos (SpO₂ y frecuencia cardíaca) |

### Monitor uMEC 100 (Mindray)

<p align="center">
  <img src="images/img00_umec100_inicio.jpg" width="600" alt="Monitor uMEC 100 en modo monitor"/>
  <br><em>Figura 1. Monitor de signos vitales Mindray uMEC 100 en funcionamiento</em>
</p>

El uMEC 100 es un monitor multiparamétrico de la marca Mindray. Para activar el **modo "Monitor"**, se procede desde el menú principal seleccionando *Tipo de paciente → Adulto → Monitor*, lo que configura el dispositivo para monitoreo continuo en tiempo real. El equipo muestra en pantalla la onda fotopletismográfica (Plet), la SpO₂ en porcentaje y la FC en ppm, además de permitir la configuración de alarmas con límites superior e inferior para cada parámetro.

### Simulador Pronk OxSim OX-1

<p align="center">
  <img src="images/img02_oxsim_ox1_frontal.jpg" width="400" alt="Simulador Pronk OxSim OX-1"/>
  <br><em>Figura 2. Simulador Pronk OxSim OX-1 de Pronk Technologies</em>
</p>

---

## 4. Parte A — Revisión Bibliográfica

### 4a. Modo "Monitor" en el uMEC 100

Para colocar el uMEC 100 en modo monitor se siguen los siguientes pasos:
1. Encender el equipo presionando el botón de encendido.
2. En la pantalla de inicio, seleccionar el perfil de paciente *Adulto*.
3. Verificar que en la barra superior aparezca la leyenda **"Monitor"**, lo que indica que el equipo está en modo de monitoreo continuo (no en modo de desfibrilación ni de marcapasos).
4. El equipo queda listo para recibir señales de los sensores conectados y visualizar las formas de onda en tiempo real.

### 4b. Parámetros simulables con el Pronk OxSim OX-1

El OxSim OX-1 dispone de **5 modos de simulación** seleccionables mediante el botón MODE, indicados por LEDs:

| Modo | SpO₂ (%) | FC (bpm) | Condición Clínica Representada |
|------|-----------|----------|-------------------------------|
| 1 | 85 | 80 | Hipoxemia moderada con FC normal |
| 2 | 95 | 40 | Normoxia con bradicardia marcada |
| 3 | 98 | 80 | Estado normal (referencia) |
| 4 | 98 | 140 | Estado normal con taquicardia |
| 5 | 99 | — | Baja perfusión (*Low Perfusion*) |

El simulador emite dos longitudes de onda (infrarrojo IR y rojo Red) que replican la absorción diferencial de la hemoglobina oxigenada y desoxigenada, que es el principio físico que utiliza el pulsioxímetro para calcular la SpO₂. Mediante el botón SENSOR se selecciona el tipo de sensor compatible (Auto, HP/Ohm u Other).

**Descripción de cada parámetro simulado:**

- **SpO₂ (Saturación periférica de oxígeno):** Porcentaje de hemoglobina unida al oxígeno respecto al total. El simulador reproduce la relación de absorción entre las longitudes de onda IR (940 nm) y roja (660 nm) para generar el índice R que el monitor convierte en SpO₂. Valores normales: 95–100%.

- **FC/FP (Frecuencia cardíaca / Frecuencia de pulso):** Número de pulsaciones por minuto. El simulador genera una señal pulsátil (onda fotopletismográfica) a la frecuencia programada. Valores normales en adulto en reposo: 60–100 bpm. Bradicardia: < 60 bpm. Taquicardia: > 100 bpm.

- **Onda fotopletismográfica (Plet):** Señal de forma de onda que representa los cambios de volumen sanguíneo en el lecho capilar con cada latido. Su morfología varía con la frecuencia y la perfusión.

### 4c. Tolerancias o Errores Máximos Permitidos (EMP)

Según estándares internacionales (ISO 80601-2-61 para pulsioxímetros) y normativas clínicas:

| Parámetro | EMP (Clínico) | Referencia |
|-----------|---------------|------------|
| SpO₂ | ± 2% (rango 70–100%) | ISO 80601-2-61 / FDA |
| FC (Frecuencia cardíaca) | ± 3 bpm o ± 3% (el mayor) | IEC 60601-2-27 |

---

## 5. Parte B — Procedimiento Experimental y Resultados

### Paso 1 — Conexión del sistema

Se conectó la pinza de pulsioximetría (sensor SpO₂) al simulador Pronk OxSim OX-1 y se encendió el uMEC 100 en modo Monitor.

<p align="center">
  <img src="images/img01_umec100_vista_lateral.jpg" width="600" alt="Sistema conectado"/>
  <br><em>Figura 3. Sistema uMEC 100 conectado al OxSim OX-1</em>
</p>

---

### Paso 2 — Simulación de Bradicardia (40 bpm, SpO₂ = 95%)

Se configuró el OxSim en el **Modo 2** (95% SpO₂, 40 bpm). El monitor uMEC 100 registró los siguientes valores:

- **FC medida:** 40 ppm  
- **SpO₂ medida:** 96%  
- La pantalla muestra la alarma `!!FP baja < 50` (frecuencia de pulso baja, umbral de bradicardia extrema del sistema = 35 bpm, pero la alarma de FC/FP bajo 50 se activa porque 40 < 50).

<p align="center">
  <img src="images/img04_umec100_bradicardia_40bpm_spo2_96.jpg" width="600" alt="Bradicardia 40 bpm"/>
  <br><em>Figura 4. uMEC 100 mostrando bradicardia simulada: FC = 40 ppm, SpO₂ = 96%</em>
</p>

<p align="center">
  <img src="images/img05_umec100_bradicardia_40bpm_spo2_96_onda.jpg" width="600" alt="Onda pletismográfica bradicardia"/>
  <br><em>Figura 5. Onda fotopletismográfica para bradicardia: pulsos amplios y espaciados (baja frecuencia)</em>
</p>

La onda fotopletismográfica (Plet) muestra picos bien definidos, amplios y con mayor separación temporal entre sí, lo que es característico de una frecuencia cardíaca baja. La morfología de la onda es preservada.

---

### Paso 3 — Configuración de Alarmas de SpO₂

Se configuró el **límite inferior de SpO₂ en 90%** y se verificó la configuración de alarmas del monitor:

<p align="center">
  <img src="images/img06_umec100_config_alarma_spo2_bajo90.jpg" width="600" alt="Configuración alarma SpO2"/>
  <br><em>Figura 6. Configuración de alarmas SpO₂: Límite Alto = 100%, Límite Bajo = 90% (prioridad Media)</em>
</p>

<p align="center">
  <img src="images/img07_umec100_config_alarma_ecg.jpg" width="600" alt="Configuración alarma ECG/FC"/>
  <br><em>Figura 7. Configuración de alarmas ECG: FC/FP Alto = 120 bpm, Bajo = 50 bpm; Taq. Extrema = 160 bpm; Bradi. Extrema = 35 bpm</em>
</p>

---

### Paso 4 — Simulación de Hipoxemia (80 bpm, SpO₂ = 85%) con Alarma de Límite Inferior

Se ajustó el OxSim al **Modo 1** (85% SpO₂, 80 bpm) con el límite inferior de alarma de SpO₂ configurado en 90%.

- **FC medida:** 80 ppm  
- **SpO₂ medida:** 85%  
- **Alarma:** `!!SpO2 bajo < 90` → **SÍ, alarma activa** (confirmada a los ~8 segundos según la imagen 08 a las 08:38:08)

<p align="center">
  <img src="images/img08_umec100_80bpm_spo2_85_alarma_activa.jpg" width="600" alt="Alarma SpO2 bajo 90"/>
  <br><em>Figura 8. Alarma !!SpO₂ bajo < 90 activa — FC = 80 ppm, SpO₂ = 85%</em>
</p>

<p align="center">
  <img src="images/img09_umec100_config_alarma_spo2_alto97.jpg" width="600" alt="Config alarma SpO2 limite 97"/>
  <br><em>Figura 9. Configuración del límite superior de alarma SpO₂ ajustado a 97%</em>
</p>

---

### Paso 5 — Simulación en modo Low Perfusion (SpO₂ = 99%, 80 bpm)

Se ajustó el OxSim al **Modo 5** (99% Low Perfusion) con el límite superior de SpO₂ configurado en 97%.

- **FC medida:** 80 ppm  
- **SpO₂ medida:** 100%  
- **Alarma:** `!!SpO₂ alto > 97` → **SÍ, alarma activa**

<p align="center">
  <img src="images/img11_oxsim_modo_99_lowperf.jpg" width="400" alt="OxSim modo Low Perfusion"/>
  <br><em>Figura 10. OxSim configurado en Modo 5: 99% Low Perfusion — LED verde en "99% Low Perf"</em>
</p>

<p align="center">
  <img src="images/img12_umec100_99lowperf_spo2_100_fc80.jpg" width="600" alt="Low Perf SpO2 100"/>
  <br><em>Figura 11. uMEC 100 en modo Low Perfusion: FC = 80 ppm, SpO₂ = 100% (alarma activa por > 97%)</em>
</p>

**¿La onda fotopletismográfica se distorsiona en modo Low Perfusion?**

<p align="center">
  <img src="images/img13_umec100_99lowperf_onda_plet.jpg" width="600" alt="Onda Plet Low Perfusion"/>
  <br><em>Figura 12. Onda fotopletismográfica en modo Low Perfusion — morfología preservada aunque amplitud varía</em>
</p>

<p align="center">
  <img src="images/img16_umec100_99lowperf_onda3.jpg" width="600" alt="Onda Plet Low Perfusion 2"/>
  <br><em>Figura 13. Onda fotopletismográfica en modo Low Perfusion — se observan variaciones en amplitud características de baja perfusión</em>
</p>

Sí, la onda fotopletismográfica presenta una **amplitud reducida y morfología ligeramente distorsionada** en modo Low Perfusion. Esto es esperado ya que el simulador replica la señal de baja amplitud que produciría un paciente con perfusión periférica deficiente (hipotensión, vasoconstricción, hipotermia). A pesar de la distorsión, el monitor logra calcular la SpO₂ y la FC correctamente.

---

### Paso 6 — Simulación de Taquicardia (140 bpm, SpO₂ = 95%)

Se ajustó el OxSim al **Modo 4** (98% SpO₂, 140 bpm).

- **FC medida:** 140 ppm  
- **SpO₂ medida:** 98–99%  
- **Alarma de FC elevada:** `!!FP alta > 120` → **SÍ, alarma activa**
- **Alarma de SpO₂ alto:** `!!SpO₂ alto > 97` → también activa (SpO₂ > límite superior 97%)

<p align="center">
  <img src="images/img18_oxsim_modo_98_140bpm.jpg" width="400" alt="OxSim modo 140 bpm"/>
  <br><em>Figura 14. OxSim en Modo 4: 98% SpO₂, 140 bpm — LED verde en "98% 140 bpm"</em>
</p>

<p align="center">
  <img src="images/img19_umec100_taquicardia_140bpm_alarma1.jpg" width="600" alt="Taquicardia 140 bpm"/>
  <br><em>Figura 15. Taquicardia 140 bpm — FC = 140 ppm en fondo amarillo, SpO₂ = 99%</em>
</p>

<p align="center">
  <img src="images/img21_umec100_taquicardia_140bpm_alarma_fpalta.jpg" width="600" alt="Alarma FP alta 120"/>
  <br><em>Figura 16. Alarma !!FP alta > 120 activa — FC = 140 ppm, SpO₂ = 98%</em>
</p>

<p align="center">
  <img src="images/img22_umec100_taquicardia_140bpm_spo2_98.jpg" width="600" alt="Taquicardia FC 140 SpO2 98 sin alarma"/>
  <br><em>Figura 17. Taquicardia con FC = 140 ppm y SpO₂ = 98% — onda pletismográfica de alta frecuencia</em>
</p>

La onda fotopletismográfica en taquicardia muestra picos frecuentes y de menor amplitud relativa, con menor tiempo de llenado diastólico visible. El patrón es sinusoidal regular y de alta frecuencia, consistente con el valor simulado.

---

## 6. Tabla de Verificación de Alarmas

| # | Condición Simulada | Parámetro | Límite Configurado | Valor Simulado | Valor Medido uMEC100 | ¿Alarma Activa? | Tiempo de Respuesta |
|---|-------------------|-----------|-------------------|---------------|----------------------|-----------------|---------------------|
| 1 | Bradicardia | FC | Bajo: 50 bpm | 40 bpm | 40 ppm | **SÍ** — `!!FP baja < 50` | < 5 s |
| 2 | Hipoxemia | SpO₂ | Bajo: 90% | 85% | 85% | **SÍ** — `!!SpO₂ bajo < 90` | ~8 s |
| 3 | Hiperoxia / Low Perf | SpO₂ | Alto: 97% | 99% (Low Perf) | 100% | **SÍ** — `!!SpO₂ alto > 97` | < 5 s |
| 4 | Taquicardia | FC | Alto: 120 bpm | 140 bpm | 140 ppm | **SÍ** — `!!FP alta > 120` | < 5 s |

---

## 7. Tabla de Errores de Medición

### Fórmulas utilizadas

$$E_{absoluto} = |V_{simulado} - V_{medido}|$$

$$E_{porcentual} = \frac{|V_{simulado} - V_{medido}|}{V_{simulado}} \times 100\%$$

### Resultados

| Condición | Parámetro | Valor Simulado | Valor Medido | Error Absoluto | Error Porcentual | ¿Dentro del EMP? |
|-----------|-----------|---------------|--------------|---------------|-----------------|------------------|
| Bradicardia | FC | 40 bpm | 40 ppm | **0 bpm** | **0.0%** | ✅ SÍ (EMP: ±3 bpm) |
| Bradicardia | SpO₂ | 95% | 96% | **1%** | **1.05%** | ✅ SÍ (EMP: ±2%) |
| Hipoxemia | FC | 80 bpm | 80 ppm | **0 bpm** | **0.0%** | ✅ SÍ |
| Hipoxemia | SpO₂ | 85% | 85% | **0%** | **0.0%** | ✅ SÍ |
| Low Perfusion | FC | 80 bpm (aprox.) | 80 ppm | **0 bpm** | **0.0%** | ✅ SÍ |
| Low Perfusion | SpO₂ | 99% | 100% | **1%** | **1.01%** | ✅ SÍ |
| Taquicardia | FC | 140 bpm | 140 ppm | **0 bpm** | **0.0%** | ✅ SÍ |
| Taquicardia | SpO₂ | 98% | 98–99% | **0–1%** | **0–1.02%** | ✅ SÍ |

> **EMP = Error Máximo Permitido** según ISO 80601-2-61 (SpO₂: ±2%) e IEC 60601-2-27 (FC: ±3 bpm o ±3%).

**Todos los valores medidos se encuentran dentro de los errores máximos permitidos por las normas técnicas internacionales.**

---

## 8. Análisis de Resultados

### Análisis 1 — Evaluación estadística de errores de medición

Los errores obtenidos en SpO₂ oscilaron entre **0% y 1%**, con una media de **0.51%** y una desviación estándar de **0.50 puntos porcentuales**. Para la frecuencia cardíaca, el error fue de **0 bpm** en todos los casos medidos, lo que indica que el algoritmo de detección de pulso del uMEC 100 es altamente preciso ante señales de simulación controladas.

El error porcentual máximo observado fue de **1.05%** (SpO₂ en bradicardia: valor simulado 95%, medido 96%), lo que queda bien por debajo del EMP de ±2% establecido por la norma ISO 80601-2-61. Estos resultados indican que el uMEC 100 se encuentra **dentro de las especificaciones de fabricante y dentro de los rangos normativos** para las condiciones evaluadas.

### Análisis 2 — Relación entre la onda fotopletismográfica y las variables FC/SpO₂

La señal fotopletismográfica (onda Plet) mostrada en el uMEC 100 evidencia una correlación directa con los parámetros hemodinámicos:

- **Bradicardia (40 bpm):** Picos anchos, bien definidos y con mayor separación temporal (~1.5 s entre picos). La morfología es regular y simétrica.
- **Hipoxemia (85% SpO₂, 80 bpm):** Picos de frecuencia normal pero con amplitud moderada. La forma de onda es regular.
- **Low Perfusion (99% SpO₂):** Amplitud reducida y variabilidad en la morfología. El monitor mantiene la lectura pero la calidad de la señal es menor, lo que el uMEC 100 indica mediante la barra de índice de perfusión reducida.
- **Taquicardia (140 bpm):** Picos frecuentes, de menor amplitud, con patrón prácticamente sinusoidal de alta frecuencia (~0.43 s entre picos). El tiempo diastólico reducido se refleja en la forma de la onda.

La frecuencia de la onda Plet corresponde exactamente a la FC medida, validando que el monitor deriva la FC/FP directamente de la onda fotopletismográfica cuando no hay señal de ECG disponible.

---

## 9. Preguntas para la Discusión

### Pregunta 1: ¿Cuál es el principio de operación del Pronk OxSim OX-1 para simular una onda pulsátil?

El OxSim OX-1 opera emitiendo luz en dos longitudes de onda (**infrarrojo a ~940 nm** y **rojo a ~660 nm**) con una modulación de intensidad que imita la variación pulsátil del volumen sanguíneo en el lecho capilar. El sensor de SpO₂ del monitor, al colocarse sobre el simulador, detecta estas variaciones de absorbancia. El simulador genera una señal electrónica que controla los diodos emisores de luz (LEDs) replicando la relación de absorción característica de la hemoglobina según el nivel de SpO₂ programado:

$$R = \frac{AC_{660}/DC_{660}}{AC_{940}/DC_{940}}$$

Donde R es el índice de ratio del que el monitor extrae la SpO₂ mediante una curva de calibración empírica. La frecuencia de modulación de la señal determina la FC simulada. El modo Low Perfusion reduce la amplitud AC de la señal para simular una baja relación señal/ruido propia de mala perfusión periférica.

### Pregunta 2: ¿Por qué la SpO₂ baja puede ser un falso positivo (falsa alarma) en una situación de mala perfusión?

En situaciones de mala perfusión periférica (hipotensión, vasoconstricción por frío, shock, etc.), la señal pulsátil AC detectada por el pulsioxímetro se vuelve muy pequeña en relación al componente de luz continua DC (ruido de fondo, luz ambiental, movimiento). Esta reducción de la relación señal/ruido altera el cálculo del índice R, que tiende a desplazarse hacia valores más bajos incluso cuando la saturación arterial real es normal. Matemáticamente, el ruido en la señal AC amplifica el error en el cálculo de la relación R, y como la curva de calibración empírica asocia valores más bajos de R a SpO₂ más bajas, el monitor puede reportar una SpO₂ artificialmente disminuida.

Por esta razón, en la práctica clínica, una lectura baja de SpO₂ acompañada de un **índice de perfusión bajo** (barra pequeña en el monitor) debe interpretarse con cautela antes de intervenir. El modo "Low Perfusion" del OxSim replica exactamente este escenario, siendo de gran utilidad para verificar que el monitor advierte al clínico sobre la posible falta de confiabilidad de la medición.

---

## 10. Conclusiones

1. **Precisión del uMEC 100:** El monitor demostró un desempeño altamente preciso ante las condiciones de simulación, con errores de SpO₂ de 0–1% y de FC de 0 bpm en todos los escenarios evaluados. Todos los valores se encontraron dentro de los EMP establecidos por las normas ISO 80601-2-61 e IEC 60601-2-27.

2. **Funcionamiento de alarmas:** El uMEC 100 activó correctamente todas las alarmas configuradas (límite inferior SpO₂ < 90%, límite superior SpO₂ > 97%, FC baja < 50 bpm, FC alta > 120 bpm) en los tiempos esperados (< 10 segundos), lo que confirma la fiabilidad del sistema de alarmas para detección clínica oportuna.

3. **Onda fotopletismográfica:** La morfología de la señal Plet se correlacionó directamente con la condición simulada. La bradicardia produjo ondas lentas y amplias; la taquicardia generó ondas rápidas y estrechas; el modo Low Perfusion redujo la amplitud de la señal, replicando fielmente condiciones de perfusión deficiente.

4. **Limitaciones del OxSim OX-1:** El simulador no replica la variabilidad fisiológica real (variabilidad de la FC latido a latido, artefactos de movimiento, interferencia ambiental) ni condiciones patológicas complejas como arritmias irregulares. Tampoco permite simular la influencia de la metahemoglobina o carboxihemoglobina sobre la SpO₂. Estas limitaciones deben tenerse en cuenta al extrapolar los resultados a situaciones clínicas reales.

5. **Confiabilidad del uMEC 100:** El monitor resultó confiable para las pruebas funcionales realizadas. La consistencia entre los valores simulados y los medidos valida su uso clínico dentro de los rangos de operación evaluados.

---

## 11. Bibliografía

[1] Instituto de Salud Pública de Chile (ISP), "Guía para la Clasificación de Dispositivos Médicos según Riesgo," ISPCH, Santiago, Chile, 2021. [En línea]. Disponible en: https://www.ispch.cl

[2] Instituto Nacional de Vigilancia de Medicamentos y Alimentos (INVIMA), *ABC de Dispositivos Médicos — Guía Reguladora*, Bogotá, Colombia. [En línea]. Disponible en: https://www.invima.gov.co/

[3] Medical IT, "Metrología Biomédica — OxSim OX-1," [En línea]. Disponible en: https://www.medicalitech.com/producto/ox-sim/

[4] Mindray, *uMEC 100 Patient Monitor Operator's Manual*, Shenzhen: Mindray Bio-Medical Electronics Co., Ltd., 2019.

[5] Pronk Technologies, *OxSim OX-1 Pulse Oximeter Simulator User Manual*, 2020.

[6] International Organization for Standardization, *ISO 80601-2-61: Medical electrical equipment — Pulse oximeter equipment*, 2017.

[7] International Electrotechnical Commission, *IEC 60601-2-27: Medical electrical equipment — Cardiac monitors*, 2011.

---

<p align="center">
  <sub>Laboratorio de Instrumentación Biomédica y Biosensores — Universidad Militar Nueva Granada — 2026</sub>
</p>
