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


<img width="702" height="265" alt="image" src="https://github.com/user-attachments/assets/b8c34e3c-dad8-49e3-b4fa-5203b5b2e65a" />


El botón “Sensor” permite elegir entre “Auto”, “HP / Ohm” y “Other”. En “Auto” el equipo reconoce solo la tecnología del oxímetro (12). “HP / Ohm” sirve para los sensores de marcas como HP/Philips, Ohmeda y Novametrix (13).


c. En el ámbito clínico ¿Cuáles son las tolerancias o errores máximos
permitidos (EMP) para cada parámetro fisiológico mencionado en la parte
(b)?

En una verificación con simulador, el resultado del monitor se compara con la exactitud que declara el fabricante. Estos son los valores de la hoja de datos del uMEC 100 (10):


<img width="822" height="257" alt="image" src="https://github.com/user-attachments/assets/ee9371a0-f6e6-4623-b60e-60d1c265fedf" />


En nuestra práctica la frecuencia vino del sensor de dedo y no de los electrodos de ECG. Por eso el límite que se aplica es ±3 bpm.

Como referencia externa, la guía de la FDA para oxímetros considera típico un error cuadrático medio (Arms) de hasta 3 % en sensores de dedo, entre 70 y 100 % de SpO₂ (9). Ese valor sale de estudios clínicos con muchas mediciones, así que lo usamos solo como comparación. También hay que sumar la tolerancia del propio simulador. El vendedor indica ±2 % con sensores reutilizables, más ±1 % del oxímetro, con un error total teórico de hasta 4 % (13). El fabricante del monitor declara cumplir las normas de ECG, pulsioximetría y alarmas (7).


PARTE B

1. Construya una tabla para verificación de alarmas en el uMEC 100 con los
siguientes ítems: límite configurado (alto/bajo), valor simulado, ¿alarma activa?
(sí/no) y tiempo de respuesta.

Antes de encender el equipo armamos la tabla que pide la guía. Tiene los cuatro datos exigidos: el límite de alarma configurado (alto o bajo), el valor que simulamos con el OxSim, si la alarma se activó (sí o no) y el tiempo de respuesta. Agregamos el valor que mostró el monitor y el mensaje en pantalla, porque ayudan a entender por qué en dos casos no sonó la alarma. La tabla se llenó con los resultados de los cuatro monitores.


<img width="658" height="643" alt="image" src="https://github.com/user-attachments/assets/17701f7c-e2d0-4e35-9fc7-997cc5c5846b" />


En el monitor 4 no se fotografió el límite bajo de frecuencia. Como con 50 bpm no sonó la alarma, el límite bajo debía ser de 50 bpm o menos.

Los límites de SpO₂ (90 % y 97 %) los ajustamos siguiendo los pasos 6 y 8 de la guía. Los de frecuencia ya venían configurados en cada monitor, y en los monitores 1 y 3 el mensaje de alarma indica 45 bpm. Los tiempos no se cronometraron. La guía pide esperar 5 segundos después de cada ajuste y entonces verificar la alarma, y en todos los casos con alarma esta ya estaba activa al cumplirse ese tiempo. Por eso los valores de la tabla son aproximados.

2. Encienda el uMEC 100 y seleccione el modo “monitor”.

Encendimos el uMEC 100 con el interruptor del equipo. Este monitor entra por sí solo en modo de monitorización al arrancar (6), así que no hizo falta elegirlo en ningún menú. Lo comprobamos en la pantalla: aparecían las curvas y los valores de los signos vitales, y la categoría del paciente estaba en “Adulto”. Mientras no había otros sensores conectados, el monitor mostró avisos técnicos como “Deriv ECG desconect.” y “Señal PANI débil”. Son normales, porque en esta práctica solo se usó el sensor de oxígeno, sin electrodos ni brazalete.

3. Conecte la pinza de pulsioximetría (sensor de SpO2) al simulador Pronk OxSim
OX-1.

Conectamos la pinza de pulsioximetría (el sensor de SpO₂) al uMEC 100 y la colocamos sobre el simulador Pronk OxSim OX-1, como si fuera el dedo de un paciente. Así el monitor lee la señal de luz que produce el simulador (12). El panel del OxSim confirmó que todo estaba bien conectado: la luz de batería estaba en verde, que indica buen estado, y las luces IR y Red estaban encendidas fijas, sin parpadear, lo que indica que el cable y el sensor estaban en buen estado (12), (13).

4. Configure el OxSim para simular un paciente bradicárdico (40 bpm, SpO2 =
95%) y calcule los errores absoluto y porcentual para cada variable en relación
con los mostrados en el uMEC100.


5. Observe y registre la forma de onda de la señal fotopletismográfica que
aparece en la pantalla del uMEC100.


6. En el uMEC100, establezca el límite inferior de alarma de SpO2 a 90%.


7. Ajuste el OxSim hasta poder simular una frecuencia cardíaca de 80 bpm y
SPO2 = 85%. A partir de ese instante, cuente 5 segundos y, al cabo de ese
tiempo, verifique y registre la activación de la alarma sonora/visual en el
uMEC100. Nuevamente, calcule los errores absoluto y porcentual para cada
variable en relación con los mostrados en el uMEC100.


8. Configure la alarma de límite superior en el uMEC100 a 97%.


9. Ajuste el OxSim hasta poder simular una SPO2 = 99% (modo “Low Perfusion”).
A partir de ese instante, cuente 5 segundos y, al cabo de ese tiempo, verifique
y registre la activación de la alarma sonora/visual en el uMEC100.
Nuevamente, calcule los errores absoluto y porcentual para cada variable en
relación con los mostrados en el uMEC100. ¿La onda fotopletismográfica se
distorsiona?


10. Con un valor de SpO2 = 98%, genere una taquicardia (140 bpm) con el OxSim
y registre la onda en el uMEC100. ¿Se dispara la alarma de frecuencia
cardíaca elevada? Nuevamente, calcule los errores absoluto y porcentual para
cada variable en relación con los mostrados en el uMEC100.


PARTE C

# Conclusión


# Referencias



