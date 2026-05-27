
## 1. INTRODUCCIÓN
---

En el contexto clínico actual, el monitoreo continuo y fiable de variables fisiológicas — especialmente la frecuencia cardíaca (FC) y la saturación periférica de oxígeno (SpO₂) — es indispensable para detectar de forma oportuna condiciones que pueden representar un peligro inmediato para la vida del paciente, tales como arritmias, bradiarritmias, taquiarritmias e hipoxia. Los monitores de signos vitales deben ser capaces no solo de registrar estos parámetros de forma precisa, sino también de generar alarmas audibles y visuales cuando los valores excedan los límites fisiológicos configurados por el clínico.

Para verificar el correcto funcionamiento de estos equipos sin necesidad de exponer a pacientes reales, se emplean simuladores de señales biomédicas. El simulador Pronk OxSim OX-1, distribuido en Colombia por Medical IT, permite recrear de manera controlada diferentes condiciones fisiológicas y patológicas (bradicardia, taquicardia, hipoxemia y baja perfusión), generando la señal óptica que el sensor de pulsioximetría del monitor interpreta como si proviniese de un dedo real.

La presente práctica evaluó el desempeño del monitor Mindray uMEC 100 ante cuatro escenarios de simulación, verificando tanto la precisión de sus medidas frente a los valores de referencia del OxSim como la correcta y oportuna activación de sus alarmas configuradas. Este tipo de evaluación es parte fundamental del mantenimiento preventivo y la metrología de equipos biomédicos, y tiene soporte normativo en estándares internacionales como la ISO 80601-2-61 para pulsioxímetros y la IEC 60601-2-27 para monitores cardíacos.

## 2. OBJETIVOS
### 2.1 Objetivo Genera
Operar el simulador Pronk OxSim OX-1 y el monitor de signos vitales Mindray uMEC 100 para realizar pruebas funcionales de verificación de alarmas y precisión de medición de parámetros hemodinámicos.
### 2.2 Objetivos Específicos
•	Identificar los modos de operación del simulador Pronk OxSim OX-1 y los parámetros fisiológicos que permite simular.
•	Verificar los límites de medición del monitor uMEC 100 mediante simulación de variables hemodinámicas bajo condiciones fisiológicas y patológicas.
•	Calcular los errores absolutos y porcentuales entre los valores simulados por el OxSim OX-1 y los valores medidos por el uMEC 100, comparándolos con los Errores Máximos Permitidos (EMP) establecidos por normas internacionales.
•	Interpretar las variaciones en la onda fotopletismográfica asociadas a diferentes estados fisiológicos y patológicos.
•	Documentar la práctica de forma estructurada en un repositorio de GitHub.

## 3. EQUIPOS UTILIZADOS
<img width="1280" height="960" alt="WhatsApp Image 2026-05-27 at 12 52 01 PM (4)" src="https://github.com/user-attachments/assets/fd3791bf-4056-443e-b559-41ff4054b533" />

 
Figura 1. Monitor de signos vitales Mindray uMEC 100 encendido en modo Monitor
El monitor uMEC 100 de Mindray es un equipo multiparamétrico de cuidados intermedios. Incorpora módulos para ECG, SpO₂, capnografía y presión no invasiva, y cuenta con un sistema de alarmas configurable por parámetro con niveles de prioridad alta, media y baja. La pantalla muestra en tiempo real la onda fotopletismográfica (Plet), el valor numérico de SpO₂ y la frecuencia de pulso (FP).

 
Figura 2. Simulador de parámetros hemodinámicos Pronk OxSim OX-1
El Pronk OxSim OX-1 es un simulador compacto de parámetros de pulsioximetría que emite señales ópticas calibradas para reproducir diferentes combinaciones de SpO₂ y FC. Dispone de cinco modos de simulación seleccionables mediante un pulsador frontal y es compatible con sensores de las marcas Masimo, Nellcor y otros.
