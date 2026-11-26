

# README – Simulación del transporte de madera con tres bitrenes

## 1. Descripción del proyecto

Este proyecto consiste en una simulación del transporte de madera utilizando tres bitrenes, cuatro canchas de almacenamiento y una línea de astillado (L1).

El modelo representa un turno de trabajo de 12 horas (720 minutos), considerando los tiempos de viaje, carga y descarga, disponibilidad de grúas e inventario de madera en cada cancha.

El objetivo es comparar dos formas de seleccionar las canchas:

- **Regla base:** selecciona la cancha más cercana que tenga inventario disponible.
- **Regla inteligente:** considera la mezcla de especies, los tiempos de viaje y el aprovechamiento de la capacidad de carga.

La simulación ejecuta ambas reglas por separado, utilizando las mismas condiciones iniciales, para poder comparar sus resultados.

## 2. Requisitos para ejecutar el proyecto

Para ejecutar el código se necesita:

- Tener instalado Python o utilizar Google Colab.
- Contar con conexión a internet si se utiliza Google Colab o si es necesario instalar las librerías.
- Disponer del código completo de la simulación.

No se requieren archivos de datos externos, ya que los parámetros iniciales y las condiciones del sistema están definidos dentro del código.

## 3. Librerías necesarias

El proyecto utiliza las siguientes librerías de Python:

| Librería | Utilidad |
|---|---|
| Pandas | Organizar los datos de la simulación, generar tablas e indicadores de desempeño. |
| Matplotlib | Crear los gráficos de resultados y comparar ambas reglas. |
| NumPy | Realizar operaciones numéricas y apoyar la elaboración de los gráficos. |

### Instalación de las librerías

Antes de ejecutar el código, se deben instalar las librerías necesarias. Para esto, se utiliza el siguiente comando:

```bash
pip install pandas matplotlib numpy
```

Si se trabaja en Google Colab, también se puede ejecutar este comando directamente en una celda:

```python
!pip install pandas matplotlib numpy
```

## 4. Instrucciones para ejecutar el proyecto

Para ejecutar correctamente la simulación se deben seguir estos pasos:

1. Abrir Google Colab o Jupyter Notebook.
2. Crear un nuevo cuaderno de Python.
3. Copiar el código completo de la simulación.
4. Ejecutar la instalación de las librerías indicadas anteriormente.
5. Ejecutar el código desde el inicio.
6. Esperar a que termine la simulación con la regla base.
7. Luego se ejecutará automáticamente la simulación con la regla inteligente.
8. Al finalizar, se mostrarán los indicadores de desempeño, las tablas comparativas y los gráficos correspondientes a ambas reglas.

**Importante:** no es necesario cambiar manualmente el modo de la regla, ya que el código está preparado para ejecutar ambas simulaciones de manera independiente.

Cada simulación comienza nuevamente con los mismos inventarios, los tres bitrenes y las condiciones iniciales, evitando que los resultados de una regla afecten a la otra.

## 5. Parámetros principales de la simulación

El modelo considera los siguientes datos de operación:

| Parámetro | Valor |
|---|---:|
| Duración del turno | 720 minutos |
| Cantidad de bitrenes | 3 |
| Capacidad máxima por bitrén | 24 m³ |
| Tiempo de carga | 7 minutos |
| Tiempo de descarga | 7 minutos |
| Cantidad de canchas | 4 |
| Línea de astillado | L1 |
| Grúas por cancha | 1 |
| Grúas en línea | 1 |
| Producción mínima de referencia | 48 m³/h |
| Mezcla objetivo Nitens | 40% |
| Mezcla objetivo Globulus | 60% |

## 6. Indicadores de desempeño que genera el código

Una vez ejecutadas las dos simulaciones, el programa entrega indicadores que permiten comparar el funcionamiento de la regla base y la regla inteligente.

Los principales indicadores son:

| Indicador | Descripción |
|---|---|
| Volumen total astillado (m³) | Cantidad total de madera procesada durante el turno. |
| Volumen Globulus (m³) | Cantidad de madera Globulus astillada. |
| Volumen Nitens (m³) | Cantidad de madera Nitens astillada. |
| Nitens (%) | Porcentaje de Nitens respecto al volumen total. |
| Globulus (%) | Porcentaje de Globulus respecto al volumen total. |
| Desviación Nitens 40% | Diferencia entre el porcentaje real y la meta de mezcla. |
| Viajes iniciados | Cantidad de viajes que comenzaron durante el turno. |
| Viajes completados | Cantidad de viajes que terminaron su descarga. |
| Espera en canchas (min) | Tiempo acumulado esperando disponibilidad de las grúas de carga. |
| Espera en línea (min) | Tiempo acumulado esperando disponibilidad de la grúa de descarga. |
| Utilización de bitrenes (%) | Porcentaje del turno que los bitrenes permanecen en actividades operativas. |
| Inventario final (m³) | Cantidad de madera que queda disponible al finalizar la simulación. |

Además, se genera un detalle individual para cada bitrén, mostrando sus tiempos de espera, minutos operativos y porcentaje de utilización.

## 7. Gráficos que genera el código

El proyecto genera cuatro gráficos principales para analizar y comparar los resultados de ambas reglas.

### 7.1. Carta Gantt de los tres bitrenes

Muestra las actividades realizadas por cada bitrén durante los 720 minutos del turno.

Permite identificar los tiempos utilizados en:

- Viajes vacíos.
- Esperas en canchas.
- Carga de madera.
- Viajes cargados.
- Esperas en línea.
- Descarga de madera.

Este gráfico ayuda a observar cómo se distribuye el tiempo de trabajo y dónde se producen mayores esperas.

### 7.2. Volumen acumulado astillado en el tiempo

Compara la cantidad de madera acumulada que recibe la línea durante el turno para ambas reglas.

Permite identificar cuál de las estrategias presenta un mayor ritmo de producción y cuál termina con un mayor volumen astillado.

### 7.3. Porcentaje de Nitens acumulado en el tiempo

Muestra cómo evoluciona el porcentaje de Nitens respecto al volumen total astillado.

Se incorpora una línea de referencia del 40%, que representa la mezcla objetivo establecida para el proyecto.

Esto permite revisar qué tan cerca se encuentra cada estrategia de cumplir con la composición de especies requerida.

### 7.4. Volumen recibido por la línea en cada hora

Compara el volumen de madera recibido por la línea L1 durante cada una de las 12 horas del turno.

Se incorpora una línea de referencia de 48 m³/h para evaluar si se alcanza la producción mínima establecida.

## 8. Tablas y resultados adicionales

Además de los indicadores y gráficos, el código genera información complementaria para revisar el funcionamiento de la simulación:

- Indicadores generales de cada regla.
- Comparación entre la regla base y la inteligente.
- Diferencias de desempeño entre ambas estrategias.
- Indicadores individuales de los tres bitrenes.
- Registro de los viajes realizados.
- Producción acumulada por minuto.
- Producción recibida por hora.
- Cumplimiento de la meta mínima de 48 m³/h.

Toda esta información permite revisar con mayor detalle el comportamiento del sistema durante el turno.

## 9. Consideraciones importantes

Para interpretar correctamente los resultados se deben considerar las siguientes condiciones:

- El inventario se descuenta cuando comienza la carga del bitrén.
- No se reserva inventario cuando se asigna una cancha.
- La carga máxima por viaje es de 24 m³.
- Se permiten cargas parciales cuando el inventario disponible es menor a 24 m³.
- La meta de 48 m³/h se utiliza como referencia para evaluar la producción, no como una restricción de operación.
- La mezcla de 40% Nitens y 60% Globulus corresponde a un objetivo de evaluación.
- El volumen astillado se contabiliza cuando termina la descarga en la línea L1.
- Se considera una grúa por cancha y una única grúa para la descarga en la línea.
- Los tiempos de viaje, carga y descarga se mantienen constantes.

## 10. Resultado final del proyecto

Al ejecutar el código completo se obtienen dos simulaciones independientes: una con la regla base y otra con la regla inteligente.

A partir de los resultados se pueden comparar los volúmenes astillados, la mezcla de especies, los tiempos de espera, los viajes realizados y la utilización de los bitrenes.

Los cuatro gráficos permiten complementar esta información y visualizar de mejor manera el comportamiento de cada estrategia durante el turno.

De esta forma, el proyecto entrega una herramienta para analizar el funcionamiento del transporte de madera y evaluar cuál de las dos reglas presenta mejores resultados bajo las condiciones operacionales consideradas.


