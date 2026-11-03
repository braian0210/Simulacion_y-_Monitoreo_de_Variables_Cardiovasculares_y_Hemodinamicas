# Simulacion_y-_Monitoreo_de_Variables_Cardiovasculares_y_Hemodinamicas

# Introducción

En un hospital, la frecuencia cardíaca y la saturación de oxígeno (SpO₂) se vigilan de forma continua con monitores de signos vitales. Estos equipos no solo muestran los valores de las variables, sino  también activan una alarma cuando un valor se sale del rango seguro y el paciente podría estar en peligro. La SpO₂ se mide con un oxímetro de pulso, un sensor que se coloca en el dedo y usa luz para estimar cuánto oxígeno lleva la sangre, sin necesidad de pinchar al paciente (1).

Aunque es una técnica muy usada, tiene límites. Una mala circulación en el dedo, el color y el grosor de la piel, la temperatura o incluso el esmalte de uñas pueden hacer que la lectura se aleje del valor real (1), (2). Por eso no basta con confiar en el número de la pantalla, hay que comprobar que el monitor mide bien y que sus alarmas responden cuando deben.

Las alarmas también traen su propio problema. Cuando suenan con demasiada frecuencia por falsas alertas o avisos que no requieren acción, el personal de salud se cansa y empieza a prestarles menos atención. Esto se conoce como fatiga de alarmas y se considera un riesgo para la seguridad del paciente (3), (4). De ahí que los límites de alarma deban configurarse con criterio y probarse.

Para hacer estas pruebas sin usar un paciente real se emplean simuladores, como el Pronk OxSim OX-1. Este equipo reproduce valores de SpO₂, frecuencia cardíaca e índice de perfusión, y funciona con una gran variedad de sensores de pulsioximetría (5). En esta práctica conectamos el OxSim al monitor uMEC 100 y simulamos cuatro situaciones, frecuencia cardíaca baja, SpO₂ baja, perfusión débil y frecuencia cardíaca alta. En cada caso comparamos lo que mostraba el monitor con el valor simulado, calculamos el error y revisamos si la alarma se activaba. El procedimiento se repitió en cuatro monitores.

# Objetivos

Objetivo General

• Operar con el simulador Pronk OxSim (OX-1) y el monitor
de signos vitales uMEC 100 para pruebas funcionales.

Objetivos Específicos

• Identificar los modos de operación de un simulador de parámetros
hemodinámicos (Pronk OxSim).

• Verificar los límites de medición de un monitor de signos vitales mediante
simulación de variables hemodinámicas.

• Interpretar variaciones en los parámetros hemodinámicos asociadas a
estados fisiológicos y patológicos.

# Metodología

PARTE A

1. Realice una revisión bibliográfica para reunir información técnica referente al
monitor de signos vitales uMEC 100 y el simulador de parámetros
hemodinámicos Pronk OxSim OX-1. Se sugiere buscar en Internet el manual
de operación o “service manual” de ambos equipos y tener una copia impresa.
En caso de utilizar modelos de IA generativa (e.g., ChatGPT), debe verificarse
la información contra una fuente confiable (e.g., libros, manuales, informes
técnicos). A continuación, responda las siguientes preguntas:

El uMEC 100 es un monitor de signos vitales de la marca Mindray. Según la documentación presentada a la FDA, sirve para monitorizar, mostrar, guardar y transferir parámetros fisiológicos, y para generar alarmas. Se usa en pacientes adultos, pediátricos y neonatales, dentro de centros de salud y manejado por personal clínico (7). Tiene una pantalla táctil a color de 10,1 pulgadas, pesa 3,5 kg y su batería dura hasta 12 horas (10). Mide ECG, respiración, SpO₂, frecuencia de pulso y presión arterial no invasiva, y puede mostrar hasta ocho ondas a la vez (10). Su algoritmo de SpO₂ está pensado para reducir el efecto de las interferencias (11). A diferencia de los modelos 120 y 150, el uMEC 100 no incluye presión invasiva, gasto cardíaco ni CO₂ (10).

Para esta práctica importan dos datos de la hoja del fabricante. La SpO₂ tiene una exactitud de ±2 % entre 70 y 100 %, y por debajo de 70 % no se especifica. La frecuencia de pulso medida con el sensor de dedo tiene una exactitud de ±3 bpm (10). En nuestra búsqueda no encontramos retiros ni avisos de seguridad de la FDA específicos para el uMEC 100. Las fallas que más aparecen en la literatura vienen de la técnica de medición y no del equipo: mala perfusión, movimiento, luz ambiente, pigmentación de la piel y esmalte de uñas pueden dar lecturas erróneas (1), (2), (8). Esas lecturas generan falsas alarmas y, a la larga, fatiga de alarmas (3), (4). También hay avisos técnicos cuando falta un sensor, como “Deriv ECG desconect.” y “Señal PANI débil”, que se ven en nuestras capturas.

El Pronk OxSim OX-1 es un simulador óptico de SpO₂ que el fabricante presenta como el más pequeño del mercado (12). Pesa unos 140 g, mide 6,4 × 6,4 × 3,2 cm y funciona con una pila AA que dura 8 horas o más (13). El sensor del monitor se coloca sobre él, de modo que se prueba el oxímetro completo, con su cable y su sensor (12). Tiene cinco modos: 85 % con 80 bpm, 95 % con 40 bpm, 98 % con 80 bpm, 98 % con 140 bpm y 99 % en baja perfusión. En ese último modo el índice de perfusión baja de unos 2,0 a unos 0,2, una décima parte (12), (13), y  Se maneja con dos botones, uno de modo y otro de sensor.

Su valor está en que permite revisar un monitor sin necesidad de un paciente, repitiendo las mismas condiciones en cualquier equipo y comprobando que las alarmas respondan. Tiene límites que conviene conocer. La página del fabricante no publica su exactitud. El vendedor indica una tolerancia de ±2 % con sensores reutilizables y de ±2 a ±3 % con desechables, más ±1 % del oxímetro, con un error total teórico de hasta 4 % (13). El modo de 95 % con 40 bpm queda justo en el límite de especificación de muchos oxímetros, y el de baja perfusión no funciona con todos los monitores ni sensores (13). Con la batería en rojo el equipo puede reiniciarse. Se apaga solo a los 10 minutos sin sensor y no recuerda el ajuste anterior. Si los LED IR y rojo parpadean, puede haber una falla en el sensor (13).

a. ¿Cómo colocar al uMEC 100 en modo “monitor”?

El modo de monitorización es el modo normal de trabajo del equipo. Según el manual de esta familia de monitores Mindray, el monitor entra en ese modo de forma automática al encenderlo (6). Los pasos fueron: conectar el cable de alimentación, pulsar el interruptor de encendido y esperar a que arranque. Antes de medir se conecta el sensor y se revisa en pantalla que la categoría del paciente sea “Adulto” (6). Hay otros dos modos que no se deben confundir con este. El modo “Standby” pone la monitorización en pausa sin apagar el equipo. El modo “Demo” muestra datos de demostración y no debe usarse mientras se monitorea a un paciente (6). El uMEC 100 hace parte de la serie uMEC registrada ante la FDA (7)

b. ¿Qué tipo de parámetros o variables fisiológicas pueden simularse con el
Pronk OxSim OX-1? Explique cada uno.

El OxSim simula tres variables: la saturación de oxígeno (SpO₂), la frecuencia de pulso y el índice de perfusión (12), (13).

• SpO₂: es el porcentaje de la hemoglobina de la sangre arterial que lleva oxígeno. El oxímetro lo estima con luz, sin pinchar al paciente (1).

• Frecuencia de pulso: son los pulsos por minuto (bpm). En esta práctica el monitor la tomó del sensor de dedo, como se ve en las capturas, donde la pantalla dice “Origen: SpO2”.

• Índice de perfusión: indica qué tan fuerte llega el pulso al sensor. Si es bajo, la señal es débil y la lectura se vuelve menos confiable (8).

El equipo trae cinco modos predefinidos, que se ven impresos en el panel y se cambian con el botón “Mode” (12), (13):

**Tabla 1.** Modos del Pronk OxSim OX-1*

<img width="702" height="265" alt="image" src="https://github.com/user-attachments/assets/b8c34e3c-dad8-49e3-b4fa-5203b5b2e65a" />


c. En el ámbito clínico ¿Cuáles son las tolerancias o errores máximos
permitidos (EMP) para cada parámetro fisiológico mencionado en la parte
(b)?

En una verificación con simulador, el resultado del monitor se compara con la exactitud que declara el fabricante. Estos son los valores de la hoja de datos del uMEC 100 (10):

**Tabla 2.** Errores Máximos Permitidos*

<img width="822" height="257" alt="image" src="https://github.com/user-attachments/assets/ee9371a0-f6e6-4623-b60e-60d1c265fedf" />



Como referencia externa, la guía de la FDA para oxímetros considera típico un error cuadrático medio (rms) de hasta 3 % en sensores de dedo, entre 70 y 100 % de SpO₂ (9). Ese valor sale de estudios clínicos con muchas mediciones, así que lo usamos solo como comparación. También hay que sumar la tolerancia del propio simulador. El vendedor indica ±2 % con sensores reutilizables, más ±1 % del oxímetro, con un error total teórico de hasta 4 % (13). El fabricante del monitor declara cumplir las normas de ECG, pulsioximetría y alarmas (7).


PARTE B

1. Construya una tabla para verificación de alarmas en el uMEC 100 con los
siguientes ítems: límite configurado (alto/bajo), valor simulado, ¿alarma activa?
(sí/no) y tiempo de respuesta.

Antes de encender el equipo armamos la tabla que pide la guía. Tiene los cuatro datos exigidos: el límite de alarma configurado (alto o bajo), el valor que simulamos con el OxSim, si la alarma se activó (sí o no) y el tiempo de respuesta. Agregamos el valor que mostró el monitor y el mensaje en pantalla, porque ayudan a entender por qué en dos casos no sonó la alarma. La tabla se llenó con los resultados de los cuatro monitores.

**Tabla 3.** Verificación de Alarmas*

<img width="658" height="643" alt="image" src="https://github.com/user-attachments/assets/17701f7c-e2d0-4e35-9fc7-997cc5c5846b" />


“N/A: en estos casos el monitor tardó más de 3 a 5 minutos en mostrar el valor real, por lo que no se pudo cronometrar el tiempo de detección. Los valores de la tabla son los de la primera lectura. La alarma no sonó. Una detección que tarda más de cinco minutos se considera no aceptable en una emergencia.”

2. Encienda el uMEC 100 y seleccione el modo “monitor”.

Encendimos el uMEC 100 con el interruptor del equipo. Este monitor entra por sí solo en modo de monitorización al arrancar (6), así que no hizo falta elegirlo en ningún menú. Lo comprobamos en la pantalla: aparecían las curvas y los valores de los signos vitales, y la categoría del paciente estaba en “Adulto”. Mientras no había otros sensores conectados, el monitor mostró avisos técnicos como “Deriv ECG desconect.” y “Señal PANI débil”. Son normales, porque en esta práctica solo se usó el sensor de oxígeno, sin electrodos ni brazalete.

3. Conecte la pinza de pulsioximetría (sensor de SpO2) al simulador Pronk OxSim
OX-1.

Conectamos la pinza de pulsioximetría (el sensor de SpO₂) al uMEC 100 y la colocamos sobre el simulador Pronk OxSim OX-1, como si fuera el dedo de un paciente. Así el monitor lee la señal de luz que produce el simulador (12). El panel del OxSim confirmó que todo estaba bien conectado: la luz de batería estaba en verde, que indica buen estado, y las luces IR y Red estaban encendidas fijas, sin parpadear, lo que indica que el cable y el sensor estaban en buen estado (12), (13).

4. Configure el OxSim para simular un paciente bradicárdico (40 bpm, SpO2 =
95%) y calcule los errores absoluto y porcentual para cada variable en relación
con los mostrados en el uMEC100.

Pusimos el OxSim en el modo 95 % / 40 bpm, que simula un paciente con el corazón lento (bradicardia) y buena oxigenación. En la Figura 1 se ve el simulador con esa luz encendida, la pinza puesta sobre él y el monitor 1 mostrando el resultado.


<img width="1600" height="900" alt="paso 4  y 5" src="https://github.com/user-attachments/assets/6d75ffd4-2fc8-43ba-8796-0656d15eb948" />

**Figura 1.Captura “paso 4 y 5” del primer monitor.** *Monitor 1 con el OxSim en modo 95 % / 40 bpm. El monitor muestra 40 bpm y 95 % y activa la alarma “FP baja < 45”.*

Luego comparamos lo que mostró cada monitor con lo que simulamos. Para cada variable calculamos dos errores:

•  Error absoluto = |valor mostrado − valor simulado|
•  Error porcentual = error absoluto / valor simulado × 100

Como ejemplo, el monitor 2 mostró 60 bpm en vez de 40. El error absoluto es |60 − 40| = 20 bpm, y el porcentual es 20 / 40 × 100 = 50 %. En SpO₂ mostró 96 % en vez de 95 %: el error absoluto es 1 punto y el porcentual es 1 / 95 × 100 = 1,05 %.


<img width="1600" height="900" alt="paso 4 y 5" src="https://github.com/user-attachments/assets/29ac1f7a-ea5e-4302-ba38-7d22481b0ca4" />

**Figura 2. Captura “paso 4 y 5” del segundo monitor.** *Monitor 2 con el OxSim en modo 95 % / 40 bpm. El monitor muestra 60 bpm y 96 %, y no activa ninguna alarma de frecuencia. El aviso amarillo “Señal PANI débil” es un mensaje técnico, porque no había brazalete de presión conectado.*


**Tabla 4.** Errores en el paso 4 (40 bpm, 95 %)*

<img width="1151" height="266" alt="image" src="https://github.com/user-attachments/assets/3ec27ad5-4f49-4ac1-a1d3-6099209adbdd" />


Para saber si estos errores son aceptables los comparamos con los máximos del fabricante (10). La frecuencia medida con el sensor de dedo puede fallar hasta ±3 bpm: los monitores 1 y 3 cumplen, y los monitores 2 y 4 no. En SpO₂ el máximo es ±2 %: los cuatro monitores cumplen.

La alarma siguió el mismo patrón. Los monitores 1 y 3 activaron “FP baja < 45”, porque mostraron 40 bpm (Figura 1). Los monitores 2 y 4 no sonaron, porque mostraron 60 y 50 bpm, que no están por debajo de sus límites bajos. La Figura 2 muestra el caso del monitor 2, en donde el simulador estaba en 40 bpm, pero el monitor leyó 60 y por eso no avisó. Hay que tener presente que el vendedor del OxSim advierte que el modo de 40 bpm queda justo en el límite de especificación de muchos oxímetros (13). La explicación posible de estos errores se discute más adelante.

5. Observe y registre la forma de onda de la señal fotopletismográfica que
aparece en la pantalla del uMEC100.

La onda que aparece en la pantalla del uMEC 100, es la fotopletismografía. Muestra cómo cambia el volumen de sangre en el dedo con cada latido. Cada pulso de la curva corresponde a un latido, y por eso a 40 bpm los pulsos aparecen muy separados, uno cada 1,5 segundos. En la Figura 1 se ve que la onda es regular, con pulsos amplios que suben rápido y bajan más despacio. Por otro lado en la Figura 2 la onda del monitor 2 también se ve regular y con la misma forma, aunque el número en pantalla sea distinto.

6. En el uMEC100, establezca el límite inferior de alarma de SpO2 a 90%.

En el uMEC 100 entramos al menú de ajuste de alarmas, a la pestaña “Límites”, en la fila de SpO₂, y dejamos el límite bajo en 90 %. El límite alto estaba en 100 % y la prioridad de la alarma en “Alto”. En la Figura 3 se ve esa pantalla. Este valor de 90 % coincide con el que trae el monitor de fábrica según el manual (6). En esa misma pantalla aparece una alarma aparte, “Desat. SpO2”, fijada en 80 % y bloqueada con un candado. Es una alarma de desaturación grave que no se puede modificar.

<img width="1600" height="900" alt="paso 6" src="https://github.com/user-attachments/assets/2aa190c2-edcc-4bb4-b9c4-13be99926ace" />

**Figura 3.** *Menú “Ajuste alarma” del monitor 1. El límite bajo de SpO₂ está en 90 % y el alto en 100 %.*

7. Ajuste el OxSim hasta poder simular una frecuencia cardíaca de 80 bpm y
SPO2 = 85%. A partir de ese instante, cuente 5 segundos y, al cabo de ese
tiempo, verifique y registre la activación de la alarma sonora/visual en el
uMEC100. Nuevamente, calcule los errores absoluto y porcentual para cada
variable en relación con los mostrados en el uMEC100.

Pusimos el OxSim en el modo 85 % / 80 bpm, que simula un paciente con una oxigenación peligrosamente baja (hipoxemia). Desde ese momento contamos 5 segundos y, al terminar, revisamos si el monitor había activado la alarma. Después calculamos los errores con las mismas fórmulas del paso 4.

Los cuatro monitores mostraron exactamente 80 bpm y 85 %, así que los errores fueron cero.

**Tabla 5.** Errores en el paso 7 (80 bpm, 85 %).*

<img width="1137" height="252" alt="image" src="https://github.com/user-attachments/assets/9d34ee34-45f7-4690-9a86-4d87226b4e81" />


En los cuatro monitores se activó la alarma, tanto la sonora como la visual, porque 85 % está por debajo del límite de 90 % que configuramos. En la Figura 4 se ve el mensaje rojo “SpO2 bajo < 90” en la parte de arriba de la pantalla del monitor 1. La alarma que salió fue la del límite de 90 % y no la de desaturación de 80 %, porque 85 % queda entre las dos. Los cuatro monitores cumplen con los errores máximos del fabricante, que son ±3 bpm en frecuencia y ±2 % en SpO₂ (10).


<img width="1600" height="900" alt="paso 7" src="https://github.com/user-attachments/assets/018af0ed-99a3-457e-b595-e27253d946f1" />

**Figura 4.Captura “paso 7” del primer monitor.** Monitor 1 con el OxSim en modo 85 % / 80 bpm. El monitor muestra 80 bpm y 85 % y activa la alarma “SpO2 bajo < 90 *


8. Configure la alarma de límite superior en el uMEC100 a 97%.

En el mismo menú de ajuste de alarmas bajamos el límite alto de SpO₂, que estaba en 100 %, hasta 97 %. El límite bajo siguió en 90 %. En la Figura 5 se ven los dos valores. Con este ajuste, cualquier saturación por encima de 97 % debe disparar la alarma, y eso es justo lo que se prueba en el paso siguiente.


<img width="1600" height="900" alt="paso 8" src="https://github.com/user-attachments/assets/a1c3e266-053e-4d3c-9ae0-3519dcd75311" />

**Figura 5. Captura “paso 8” del primer monitor** Menú “Ajuste alarma” del monitor 1 con el límite alto de SpO₂ en 97 % y el bajo en 90 %. *


9. Ajuste el OxSim hasta poder simular una SPO2 = 99% (modo “Low Perfusion”).
A partir de ese instante, cuente 5 segundos y, al cabo de ese tiempo, verifique
y registre la activación de la alarma sonora/visual en el uMEC100.
Nuevamente, calcule los errores absoluto y porcentual para cada variable en
relación con los mostrados en el uMEC100. ¿La onda fotopletismográfica se
distorsiona?

Pusimos el OxSim en el modo 99 % “Low Perf”, que simula una circulación muy débil en el dedo. En este modo el simulador entrega 80 bpm y baja el índice de perfusión a una décima parte de lo normal, de unos 2,0 a unos 0,2 (12), (13). Desde ese momento contamos 5 segundos y revisamos la alarma. Luego calculamos los errores con las mismas fórmulas de los pasos anteriores.

Los cuatro monitores mostraron 80 bpm y 100 % de SpO₂. En frecuencia no hubo error. En SpO₂ el error absoluto fue de 1 punto y el porcentual fue 1 / 99 × 100 = 1,01 %.

**Tabla 6. Errores en el paso 9 (80 bpm, 99 %, baja perfusión). *

<img width="1132" height="252" alt="image" src="https://github.com/user-attachments/assets/24c8c095-e468-4454-a3d6-ab98bd0c0ab7" />


Este error de 1 punto está dentro del máximo del fabricante, que es de ±2 % (10), y también dentro de la tolerancia del propio simulador (13). En los cuatro monitores se activó la alarma, tanto la sonora como la visual: “SpO2 alto > 97”, porque 100 % supera el límite que configuramos. El mensaje se ve en las Figuras 6 y 7.



<img width="1600" height="900" alt="paso 9" src="https://github.com/user-attachments/assets/335b75d9-4602-4d50-b5b4-837efdbcf30f" />

**Figura 6. Captura “paso 9” del primer monitor** Monitor 1 con el OxSim en modo 99 % “Low Perf”. Muestra 80 bpm y 100 %, activa la alarma “SpO2 alto > 97” y marca un índice de perfusión (IP) de 0,46.*


<img width="1600" height="900" alt="paso 9" src="https://github.com/user-attachments/assets/726395b0-0e21-4f2b-b9d3-b419f996933d" />

**Figura 7. Captura “paso 9” del Segundo monitor** Monitor 2 con el OxSim en modo 99 % “Low Perf”. Muestra 80 bpm y 100 % y activa la alarma “SpO2 alto > 97”. *


¿La onda fotopletismográfica se distorsiona? Muy poco. En las Figuras 6 y 7 se sigue reconociendo la forma de cada pulso, con su subida rápida y su pequeña curva en la bajada, igual que en el paso 7. Observando detalladamnete en el monitor 1 la línea se ve algo más irregular, con pequeños temblores, y en el monitor 2 se ve limpia. El cambio más claro está en el índice de perfusión del monitor 1, que se marcó en amarillo y bajó a 0,46, frente a 4,38 en el paso 7 y 4,36 en el paso 10. Es una caída de unas diez veces, como describe el fabricante del simulador (12). En resumen, la onda casi no se deforma, pero el monitor sí registra que la señal es mucho más débil.


10. Con un valor de SpO2 = 98%, genere una taquicardia (140 bpm) con el OxSim
y registre la onda en el uMEC100. ¿Se dispara la alarma de frecuencia
cardíaca elevada? Nuevamente, calcule los errores absoluto y porcentual para
cada variable en relación con los mostrados en el uMEC100.

Pusimos el OxSim en el modo 98 % / 140 bpm, que simula un paciente con el corazón muy acelerado (taquicardia) y buena oxigenación. Registramos la onda en la pantalla del uMEC 100, revisamos si saltaba la alarma de frecuencia alta y calculamos otra vez los errores.

Los cuatro monitores mostraron 140 bpm y 98 %, es decir, exactamente lo simulado. Los errores fueron cero.

**Tabla 7. Errores en el paso 10 (140 bpm, 98 %) *

<img width="1142" height="256" alt="image" src="https://github.com/user-attachments/assets/f4eb0412-ce03-4049-8966-b306c4201c52" />



Los cuatro monitores cumplen con los errores máximos del fabricante, que son ±3 bpm en frecuencia y ±2 % en SpO₂ (10).

¿Se dispara la alarma de frecuencia cardíaca elevada? Sí. En los cuatro monitores apareció la alarma “FP alta > 110”, porque 140 bpm supera el límite de 110 bpm. El mensaje rojo se ve en las Figuras 8 y 9.


<img width="1600" height="900" alt="paso 10" src="https://github.com/user-attachments/assets/fa6d4b5d-b583-441e-83c2-b2f3811ec506" />

**Figura 7. Captura “paso 10” del primer monitor ** Monitor 1 con el OxSim en modo 98 % / 140 bpm. Muestra 140 bpm y 98 % y activa la alarma “FP alta > 110”. *




<img width="1600" height="900" alt="paso 10" src="https://github.com/user-attachments/assets/0e09eb5b-5c74-4075-bf73-262f6e0945c3" />

**Figura 8. Captura “paso 10” del segundo monitor** Monitor 2 con el OxSim en modo 98 % / 140 bpm. Muestra 140 bpm y 98 % y activa la alarma “FP alta > 110”. *

Onda registrada. A 140 bpm los pulsos aparecen muy juntos, uno cada 0,43 segundos aproximadamente, y la onda se ve casi como una ola regular. A diferencia de lo que se veía a 80 bpm en el paso 7, ya no se distingue la pequeña curva en la bajada de cada pulso. Esto se ve igual en los dos monitores fotografiados (Figuras 8 y 9). El monitor 1 marcó un índice de perfusión de 4,36, parecido al de 4,38 del paso 7, es decir, la señal se mantuvo fuerte.

PARTE C

Análisis y discusión de Resultados

En total hicimos 16 verificaciones de alarma, 4 pasos en cada uno de los 4 monitores. En 14 de ellas la alarma saltó como se esperaba para el valor simulado: frecuencia baja a 40 bpm, SpO₂ baja a 85 %, SpO₂ alta a 99 % y frecuencia alta a 140 bpm. Las dos excepciones fueron los monitores 2 y 4 en el paso 4, que no avisaron. En esos dos casos la lectura tardó más de 3 a 5 minutos en ajustarse al valor real y no pudimos cronometrarla, por eso su tiempo de respuesta quedó como N/A. Mientras estuvieron mostrando 60 y 50 bpm, el comportamiento de la alarma fue coherente con la pantalla, porque esos valores no están por debajo de sus límites bajos. Aun así, en ningún momento sonó la alarma de frecuencia baja. En la SpO₂ los cuatro monitores quedaron dentro del error máximo del fabricante de ±2 % (10), y el error más grande fue de 1 punto en el paso 9. En la frecuencia, 14 de 16 lecturas registradas quedaron dentro de ±3 bpm. Las dos que no cumplieron fueron las primeras lecturas de los monitores 2 y 4, con 60 y 50 bpm en lugar de 40.

Ese error de frecuencia es el hallazgo más importante, porque es el que tiene consecuencias. Si un paciente real tuviera 40 bpm y el monitor leyera 60, la alarma de bradicardia no sonaría. Además, el problema no fue solo el número equivocado sino el tiempo: tardar más de cinco minutos en detectar bien, ante una emergencia, es demasiado. No podemos decir con seguridad de dónde viene el error, pero hay pistas. El rango de pulso del uMEC 100 va de 20 a 300 bpm (10), así que 40 bpm está dentro de lo que debe medir. Sin embargo, el vendedor del OxSim advierte que 40 bpm queda justo en el límite de especificación de muchos oxímetros (13). El hecho de que la lectura terminara ajustándose a 40 bpm apunta a que el monitor tardó en “enganchar” la señal, más que a un error fijo. Además, en esta práctica la frecuencia se tomó del sensor de dedo y no del ECG, y los monitores no tenían la misma configuración: los límites bajos de frecuencia eran de 45 bpm en los monitores 1 y 3, y de 50 bpm en el 2. A 140 bpm los cuatro monitores acertaron, lo que apunta a que el problema aparece en frecuencias bajas y no en el monitor entero. Si se usó el mismo simulador con los cuatro, lo más probable es que la diferencia venga del monitor o de su sensor. Para saberlo, lo sensato sería repetir la prueba con electrodos de ECG, que el fabricante especifica con ±1 bpm (10), y revisar los monitores 2 y 4 con mantenimiento.

La prueba de baja perfusión mostró algo distinto. La onda casi no cambió de forma, pero el índice de perfusión del monitor 1 cayó de 4,38 a 0,46, unas diez veces. Aun así el monitor siguió dando la frecuencia correcta y una SpO₂ con solo 1 punto de diferencia. Esto puede deberse en parte al algoritmo de SpO₂ que Mindray diseñó para resistir interferencias (11). Hay que tener cuidado al sacar conclusiones, porque el simulador produce una señal limpia y repetible. No reproduce el movimiento del paciente, el esmalte de uñas ni la pigmentación de la piel, que en la práctica sí alteran la lectura (1), (8). Por eso estos resultados sirven para verificar que el monitor y sus alarmas funcionan, pero no demuestran cómo se comportaría con un paciente real. Una limitación más de la práctica es que no cronometramos con precisión el tiempo de respuesta de las alarmas, por lo que ese dato es aproximado. En los casos con N/A fue porque la detección tardó más de 3 a 5 minutos y no pudimos medirla.
Preguntas Para la Discusión

• Pregunta 1: ¿Cuál es el principio de operación del Pronk OxSim OX-1 para
simular una onda pulsátil?

El OX-1 funciona como un dedo artificial. Un pulsioxímetro mide la saturación enviando luz roja e infrarroja a través del dedo y viendo cuánta le llega al fotodetector del otro lado. El simulador aprovecha eso ya que recibe los destellos de luz del sensor, los bloquea y, con técnicas electrónicas, ópticas y mecánicas, genera nuevos destellos que imitan lo que el sensor vería a través del dedo de un paciente (14). Para el monitor, esa luz que le llega es la señal de un paciente real, aunque no haya sangre de por medio.

La onda pulsátil sale de cómo se calcula la saturación. Según el manual, el oxímetro separa la luz que llega para cada color en una parte pequeña que va y viene con cada latido (AC) y una parte grande y estable que representa el resto del tejido (DC). Luego hace el cociente entre las dos para cada color y compara los resultados, R = (RedAC/RedDC)/(IRAC/IRDC). Ese valor R se pasa a un porcentaje de SpO₂ con una curva de calibración propia de cada fabricante. En términos generales, un R cercano a 0.6 equivale a 100 % y uno cercano a 1.0 equivale a 81 % (14). El OX-1 produce justamente esa parte que late. Por eso la frecuencia cardíaca fija el ritmo de la pulsación, la saturación fija la relación entre los dos colores y el índice de perfusión fija qué tan grande es la pulsación frente a la parte estable. El manual no describe el circuito interno que logra esto, así que solo se puede decir lo que hace y no cómo lo hace.

Esos tres valores no se pueden elegir libremente ya que  vienen en cinco modos predefinidos que se cambian con el botón MODE (14). Dos luces del equipo, IR y Red, se encienden cuando detectan la luz del sensor y sirven para comprobar que el sensor quedó bien puesto (14). El botón SENSOR sirve para indicarle al simulador qué tipo de sensor tiene conectado. Lo que cuenta es el sensor y no el monitor, porque un mismo monitor puede usar sensores de distinta marca (14). Un detalle práctico es que parte de la luz del sensor se escapa por los lados del dedo y llega al detector sin pasar por el simulador. Eso suma al componente estable y puede mover la lectura unos puntos, por lo que la posición del sensor importa (14). Por eso el simulador sirve para probar todo el sistema (sensor, cable y monitor), pero no para certificar la exactitud absoluta de un pulsioxímetro (15, 16). El propio fabricante indica que una lectura dentro del 2 % de lo que marca el simulador es un resultado razonable (14), cifra que coincide con lo que obtuvimos en el laboratorio.

• Pregunta 2: ¿Por qué la SpO2 baja puede ser un falso positivo (falsa
alarma) en una situación de mala perfusión?

Con mala perfusión llega muy poca sangre pulsátil al dedo, por ejemplo con manos frías, shock o vasos sanguíneos contraídos. Eso hace que la parte de la señal que late (la AC) sea diminuta frente a la parte estable. Como el monitor calcula la saturación a partir de ese cociente, cualquier ruido pequeño pesa mucho como un movimiento, la luz del ambiente o interferencia eléctrica (2, 8). El resultado es que la cuenta se vuelve inestable y el monitor puede mostrar una saturación baja que en realidad es un error de la señal y no del oxígeno en la sangre. Si esa cifra cruza el límite configurado, suena la alarma aunque el paciente esté bien, y eso es un falso positivo (15, 17).

Esto es más común de lo que parece, y no es un problema menor. Cuando suenan muchas alarmas que no corresponden a nada, el personal se acostumbra a ellas y empieza a responder más lento o a ignorarlas, un efecto que se conoce como fatiga de alarmas (3, 4). El riesgo es que una alarma verdadera quede entre las falsas. Por eso, ante una SpO₂ baja con mala señal, lo recomendable es revisar primero al paciente y la calidad de la señal (la forma de la onda y el índice de perfusión) y probar otro dedo antes de actuar sobre el valor registrado en el monitor(2, 8).

En el laboratorio lo vimos con el modo “Low Perfusion”. El manual lo define con un índice de perfusión de 0.2 y advierte que es un reto para el monitor y que algunos no funcionarán bien con él (14). En el primer monitor, el índice mostrado cayó a 0.46, frente a 4.38 en el paso 7 y 4.36 en el paso 10. Ese monitor siguió leyendo 99 y 100 % sin problema, así que esa señal débil no lo desorientó. Aun así, es un buen recordatorio de por qué un valor aislado no basta para decidir.


# Conclusión

La práctica buscaba saber si un monitor de signos vitales avisa a tiempo y mide bien cuando un paciente se sale de lo normal. Para comprobarlo se conectaron cuatro monitores uMEC 100 al simulador OxSim OX-1, que imita la luz que atraviesa un dedo. En general los monitores respondieron bien: la saturación quedó dentro de ±2 % en las 16 mediciones y 14 de las 16 condiciones activaron la alarma esperada, incluidas SpO₂ baja (85 %), SpO₂ alta (99 %) y taquicardia (140 lpm), con tiempos de respuesta de pocos segundos que se estimaron sin cronómetro. La excepción fue el pulso a 40 lpm. En dos monitores la lectura tardó más de 3 a 5 minutos en ajustarse al valor real, no se pudo cronometrar y por eso su tiempo quedó como N/A, y además la alarma de pulso bajo nunca sonó. El manual del simulador advierte que 40 lpm está en el límite de lo que muchos oxímetros leen (14), pero en una emergencia real tardar más de cinco minutos en detectar bien es una falla grave. Este montaje permite a quien revisa equipos comprobar sin pacientes que un monitor avisa cuando debe y detectar de antemano un pulso mal leído en frecuencias bajas, aunque el simulador solo ofrece cinco combinaciones fijas, sin ruido, movimiento ni arritmias, y no certifica la exactitud absoluta (14, 15). Como siguiente paso, habría que repetir la prueba de 40 lpm en más monitores tomando el pulso desde el ECG, cronometrar los tiempos y probar con una señal con ruido o movimiento.

# Referencias

(1) R. Al-Halawani, P. H. Charlton, M. Qassem, and P. A. Kyriacou, “A review of the effect of skin pigmentation on pulse oximeter accuracy,” Physiol. Meas., vol. 44, no. 5, Jun. 2023, doi: 10.1088/1361-6579/acd51a.

(2) U.S. Food and Drug Administration, “FDA Brief: FDA warns about limitations and accuracy of pulse oximeters,” Feb. 19, 2021. [Online]. Available: https://www.fda.gov/news-events/fda-brief/fda-brief-fda-warns-about-limitations-and-accuracy-pulse-oximeters

3) J. O. Jämsä, K. H. Uutela, A.-M. Tapper, and L. Lehtonen, “Clinical alarms in a gynaecological surgical unit: A retrospective data analysis,” Int. J. Environ. Res. Public Health, vol. 20, no. 5, Art. no. 4193, Feb. 2023, doi: 10.3390/ijerph20054193. [Online]. Available: https://doi.org/10.3390/ijerph20054193

(4) Nyarko et al., “The effect of educational interventions in managing nurses’ alarm fatigue: An integrative review,” J. Clin. Nurs., vol. 32, no. 13–14, pp. 2985–2997, 2023, doi: 10.1111/jocn.16479.

(5) Medical IT, “Metrología Biomédica: OX-SIM,” product page. [Online]. Available: https://www.medicalitech.com/producto/ox-sim/

(6) Mindray, “uMEC10/uMEC12/uMEC15 Patient Monitor Operator’s Manual,” 2016. [Online]. Available: http://mindray.sy/wp-content/uploads/2019/09/uMEC-Operator%E2%80%99s-Manual.pdf

(7) U.S. Food and Drug Administration, “510(k) K253170: uMEC 60/70/80/100/120/150 patient monitors,” Apr. 2026. [Online]. Available: https://fda.innolitics.com/device/K253170

(8) K. Moon et al., “Pulse oximetry: A perioperative perspective,” Diagnostics, vol. 16, no. 12, Jun. 2026, doi: 10.3390/diagnostics16121812.

(9) U.S. Food and Drug Administration, “Pulse Oximeters – Premarket Notification Submissions [510(k)s]: Guidance for Industry and FDA Staff,” Mar. 4, 2013. [Online]. Available: https://www.fda.gov/media/72470/download

(10) Mindray, “uMEC 100/120/150 Patient Monitor Data Sheet,” Jun. 2023. [Online]. Available: https://healthtechghana.com/wp-content/uploads/2024/07/Datasheet_uMEC-100-120-150_20230628.pdf

(11) Mindray, “uMEC 100/120/150: Optimized uses at your fingertips,” brochure, Jun. 2023. [Online]. Available: https://healthtechghana.com/wp-content/uploads/2024/07/Brochure_uMEC-100-120-150_ENG_20230629_s.pdf

(12) Pronk Technologies, “OX-1 OxSim,” 2013 (mod. 2018). [Online]. Available: https://www.pronktech.com/ox-1-oxsim-review/

(13) BioMedEquip, “OX-1 OxSim SpO₂ simulator,” product page. [Online]. Available: https://biomedequip.com/index.php?route=product/product&product_id=93

(14) Pronk Technologies, “OxSim SpO₂ Simulator Operator’s Manual,” Rev. O, doc. 501-0603, Jul. 2017. [Online]. Available: https://www.pronktech.com/wp-content/uploads/2015/02/501-0603-OX-1-Op-Manual-Rev-O.pdf

(15) D. J. McMahon, “There’s no such thing as a SpO₂ simulator,” Fluke Biomedical, white paper, 2013. [Online]. Available: https://www.flukebiomedical.com/sites/default/files/resources/Prosimspot_whitepaper_nosuchthing_A_W.PDF

(16) P. Zhang, J. Chen, and Y. Yang, “Design of pulse oximeter simulator calibration equipment,” in Proc. IMEKO TC4 Symp., 2011. [Online]. Available: https://www.imeko.org/publications/tc4-2011/IMEKO-TC4-2011-082.pdf

(17) M. Proença et al., “Performance assessment of a dedicated reflectance pulse oximeter in a neonatal intensive care unit,” in Proc. 40th Annu. Int. Conf. IEEE Eng. Med. Biol. Soc. (EMBC), 2018, pp. 1502–1505, doi: 10.1109/EMBC.2018.8512504.

