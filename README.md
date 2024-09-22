# Reto-13

Este repo tiene como fin dar solución al reto 13 propuesto en la clase de Diccionarios.
**1. Desarrollar un algoritmo que imprima de manera ascendente los valores (todos del mismo tipo) de un diccionario.**
```python
# Definir un diccionario con valores del mismo tipo (números)
mi_diccionario = {
    'a': 30,
    'b': 5,
    'c': 20,
    'd': 10,
    'e': 50
}

# Obtener los valores del diccionario
valores = list(mi_diccionario.values())

# Ordenar los valores de manera ascendente
valores_ordenados = sorted(valores)

# Imprimir los valores ordenados
print("Valores ordenados de manera ascendente:")
for valor in valores_ordenados:
    print(valor)
```

**2.Desarrollar una función que reciba dos diccionarios como parámetros y los mezcle, es decir, que se construya un nuevo diccionario con las llaves de los dos diccionarios; si hay una clave repetida en ambos diccionarios, se debe asignar el valor que tenga la clave en el primer diccionario
```python
def mezclar_diccionarios(dic1, dic2):
    # Crear un nuevo diccionario que inicialmente contiene todos los items de dic2
    diccionario_mezclado = dic2.copy()
    
    # Actualizar con los items de dic1. Si hay claves repetidas, se conservan los valores de dic1.
    diccionario_mezclado.update(dic1)
    
    return diccionario_mezclado

# Ejemplo de uso
diccionario1 = {'a': 1, 'b': 2, 'c': 3}
diccionario2 = {'b': 4, 'd': 5, 'e': 6}

# Mezclar los diccionarios
resultado = mezclar_diccionarios(diccionario1, diccionario2)

# Imprimir el resultado
print("Diccionario mezclado:", resultado)
```

3. Dado el JSON:
```python
{
	"jadiazcoronado":{
		"nombres": "Juan Antonio",
		"apellidos": "D��az Coronado",
		"edad":19,
		"colombiano":true,
		"deportes":["F�utbol","Ajedrez","Gimnasia"]
	},
	"dmlunasol":{
		"nombres": "Dorotea Maritza",
		"apellidos": "Luna Sol",
		"edad":25,
		"colombiano":false,
		"deportes":["Baloncesto","Ajedrez","Gimnasia"]
	}
```
Cree un programa que lea de un archivo con dicho JSON y:

- Imprima los nombres completos (nombre y apellidos) de las personas que practican el deporte ingresado por el usuario.
- Imprima los nombres completos (nombre y apellidos) de las personas que est�en en un rango de edades dado por el usuario

Para desarrollar este punto:
1. Leer el archivo JSON.
2. Pedir al usuario un deporte para filtrar las personas que lo practican.
3. Pedir al usuario un rango de edades (mínima y máxima) para filtrar las personas en ese rango.
4. Imprimir los resultados basados en los filtros anteriores.

```python
import json

# Cargar el archivo JSON desde un archivo o directamente desde una cadena
# Simulamos que lo estamos leyendo desde un archivo
data = {
    "jadiazcoronado": {
        "nombres": "Juan Antonio",
        "apellidos": "Díaz Coronado",
        "edad": 19,
        "colombiano": True,
        "deportes": ["Fútbol", "Ajedrez", "Gimnasia"]
    },
    "dmlunasol": {
        "nombres": "Dorotea Maritza",
        "apellidos": "Luna Sol",
        "edad": 25,
        "colombiano": False,
        "deportes": ["Baloncesto", "Ajedrez", "Gimnasia"]
    }
}

# Función para imprimir nombres completos (nombres y apellidos) de personas que practican el deporte dado
def imprimir_por_deporte(data, deporte):
    print(f"Personas que practican el deporte '{deporte}':")
    for usuario, info in data.items():
        if deporte in info["deportes"]:
            nombre_completo = info["nombres"] + " " + info["apellidos"]
            print(nombre_completo)

# Función para imprimir nombres completos de personas que están en un rango de edad dado
def imprimir_por_rango_edad(data, edad_min, edad_max):
    print(f"Personas en el rango de edad {edad_min}-{edad_max}:")
    for usuario, info in data.items():
        if edad_min <= info["edad"] <= edad_max:
            nombre_completo = info["nombres"] + " " + info["apellidos"]
            print(nombre_completo)

# Pedir deporte al usuario
deporte_ingresado = input("Ingresa un deporte: ")

# Pedir rango de edades al usuario
edad_min = int(input("Ingresa la edad mínima: "))
edad_max = int(input("Ingresa la edad máxima: "))

# Llamar a las funciones
imprimir_por_deporte(data, deporte_ingresado)
imprimir_por_rango_edad(data, edad_min, edad_max)
```


**4. El siguiente código contiene un JSON con el pronostivo detallado del clima para 8 días:**
import json

```python
# Cargar archivo
jsonString = '''
{\"dt\": {\"0\": 1685116800, \"1\": 1685203200, \"2\": 1685289600, \"3\": 1685376000, \"4\": 1685462400, \"5\": 1685548800, \"6\": 1685635200, \"7\": 1685721600}, \"sunrise\": {\"0\": 1685097348, \"1\": 1685183745, \"2\": 1685270143, \"3\": 1685356542, \"4\": 1685442942, \"5\": 1685529342, \"6\": 1685615743, \"7\": 1685702145}, \"sunset\": {\"0\": 1685143042, \"1\": 1685229458, \"2\": 1685315875, \"3\": 1685402291, \"4\": 1685488708, \"5\": 1685575124, \"6\": 1685661541, \"7\": 1685747958}, \"moonrise\": {\"0\": 1685118300, \"1\": 1685207460, \"2\": 1685296620, \"3\": 1685385720, \"4\": 1685474880, \"5\": 1685564220, \"6\": 1685653740, \"7\": 1685743500}, \"moonset\": {\"0\": 0, \"1\": 1685164320, \"2\": 1685253000, \"3\": 1685341560, \"4\": 1685430120, \"5\": 1685518740, \"6\": 1685607600, \"7\": 1685696640}, \"moon_phase\": {\"0\": 0.22, \"1\": 0.25, \"2\": 0.28, \"3\": 0.31, \"4\": 0.35, \"5\": 0.38, \"6\": 0.41, \"7\": 0.45}, \"pressure\": {\"0\": 1011, \"1\": 1012, \"2\": 1012, \"3\": 1012, \"4\": 1012, \"5\": 1012, \"6\": 1012, \"7\": 1011}, \"humidity\": {\"0\": 85, \"1\": 61, \"2\": 68, \"3\": 74, \"4\": 84, \"5\": 66, \"6\": 81, \"7\": 82}, \"dew_point\": {\"0\": 23.93, \"1\": 22.5, \"2\": 23.67, \"3\": 23.35, \"4\": 24.22, \"5\": 22.73, \"6\": 23.18, \"7\": 22.93}, \"velViento\": {\"0\": 3.56, \"1\": 5.07, \"2\": 5.38, \"3\": 3.95, \"4\": 4.74, \"5\": 3.75, \"6\": 4.08, \"7\": 5.94}, \"dirViento\": {\"0\": 188, \"1\": 14, \"2\": 21, \"3\": 23, \"4\": 40, \"5\": 330, \"6\": 176, \"7\": 168}, \"wind_gust\": {\"0\": 6.47, \"1\": 8.86, \"2\": 8.95, \"3\": 6.12, \"4\": 7.17, \"5\": 5.4, \"6\": 5.13, \"7\": 9.67}, \"weather\": {\"0\": [{\"id\": 501, \"main\": \"Rain\", \"description\": \"lluvia moderada\", \"icon\": \"10d\"}], \"1\": [{\"id\": 500, \"main\": \"Rain\", \"description\": \"lluvia ligera\", \"icon\": \"10d\"}], \"2\": [{\"id\": 501, \"main\": \"Rain\", \"description\": \"lluvia moderada\", \"icon\": \"10d\"}], \"3\": [{\"id\": 500, \"main\": \"Rain\", \"description\": \"lluvia ligera\", \"icon\": \"10d\"}], \"4\": [{\"id\": 501, \"main\": \"Rain\", \"description\": \"lluvia moderada\", \"icon\": \"10d\"}], \"5\": [{\"id\": 500, \"main\": \"Rain\", \"description\": \"lluvia ligera\", \"icon\": \"10d\"}], \"6\": [{\"id\": 500, \"main\": \"Rain\", \"description\": \"lluvia ligera\", \"icon\": \"10d\"}], \"7\": [{\"id\": 500, \"main\": \"Rain\", \"description\": \"lluvia ligera\", \"icon\": \"10d\"}]}, \"clouds\": {\"0\": 100, \"1\": 82, \"2\": 99, \"3\": 100, \"4\": 100, \"5\": 59, \"6\": 100, \"7\": 100}, \"pop\": {\"0\": 1.0, \"1\": 0.65, \"2\": 0.98, \"3\": 0.86, \"4\": 1.0, \"5\": 0.62, \"6\": 0.93, \"7\": 0.95}, \"prcp\": {\"0\": 40.0, \"1\": 1.65, \"2\": 14.01, \"3\": 5.07, \"4\": 16.55, \"5\": 2.17, \"6\": 2.77, \"7\": 1.73}, \"uvi\": {\"0\": 10.14, \"1\": 12.78, \"2\": 12.73, \"3\": 8.44, \"4\": 0.59, \"5\": 1.0, \"6\": 1.0, \"7\": 1.0}, \"temp.day\": {\"0\": 26.62, \"1\": 30.95, \"2\": 30.17, \"3\": 28.37, \"4\": 27.22, \"5\": 29.78, \"6\": 26.83, \"7\": 26.36}, \"tmpMin\": {\"0\": 25.64, \"1\": 24.64, \"2\": 25.84, \"3\": 25.56, \"4\": 25.72, \"5\": 24.86, \"6\": 25.96, \"7\": 25.47}, \"tmpMax\": {\"0\": 27.16, \"1\": 31.1, \"2\": 30.2, \"3\": 29.5, \"4\": 28.87, \"5\": 29.78, \"6\": 28.96, \"7\": 28.25}, \"temp.night\": {\"0\": 25.67, \"1\": 27.39, \"2\": 26.24, \"3\": 27.2, \"4\": 25.92, \"5\": 27.14, \"6\": 26.56, \"7\": 25.66}, \"temp.eve\": {\"0\": 25.91, \"1\": 28.73, \"2\": 27.42, \"3\": 28.27, \"4\": 27.94, \"5\": 29.29, \"6\": 28.96, \"7\": 28.12}, \"temp.morn\": {\"0\": 26.5, \"1\": 24.64, \"2\": 26.13, \"3\": 25.72, \"4\": 26.04, \"5\": 24.86, \"6\": 25.98, \"7\": 25.57}, \"feels_like.day\": {\"0\": 26.62, \"1\": 34.99, \"2\": 34.96, \"3\": 32.03, \"4\": 30.67, \"5\": 33.62, \"6\": 29.45, \"7\": 26.36}, \"feels_like.night\": {\"0\": 26.56, \"1\": 30.98, \"2\": 26.24, \"3\": 30.62, \"4\": 26.84, \"5\": 30.16, \"6\": 26.56, \"7\": 26.45}, \"feels_like.eve\": {\"0\": 26.85, \"1\": 32.49, \"2\": 30.94, \"3\": 31.8, \"4\": 31.51, \"5\": 33.17, \"6\": 32.64, \"7\": 31.18}, \"feels_like.morn\": {\"0\": 26.5, \"1\": 25.48, \"2\": 26.13, \"3\": 26.62, \"4\": 26.04, \"5\": 25.73, \"6\": 25.98, \"7\": 26.4}, \"date\": {\"0\": 1685098800000, \"1\": 1685185200000, \"2\": 1685271600000, \"3\": 1685358000000, \"4\": 1685444400000, \"5\": 1685530800000, \"6\": 1685617200000, \"7\": 1685703600000}, \"main\": {\"0\": \"Rain\", \"1\": \"Rain\", \"2\": \"Rain\", \"3\": \"Rain\", \"4\": \"Rain\", \"5\": \"Rain\", \"6\": \"Rain\", \"7\": \"Rain\"}, \"description\": {\"0\": \"lluvia moderada\", \"1\": \"lluvia ligera\", \"2\": \"lluvia moderada\", \"3\": \"lluvia ligera\", \"4\": \"lluvia moderada\", \"5\": \"lluvia ligera\", \"6\": \"lluvia ligera\", \"7\": \"lluvia ligera\"}, \"icono\": {\"0\": \"10d\", \"1\": \"10d\", \"2\": \"10d\", \"3\": \"10d\", \"4\": \"10d\", \"5\": \"10d\", \"6\": \"10d\", \"7\": \"10d\"}, \"alertPrecip\": {\"0\": \"X\", \"1\": \"-\", \"2\": \"-\", \"3\": \"-\", \"4\": \"-\", \"5\": \"-\", \"6\": \"-\", \"7\": \"-\"}, \"alertAlertas\": {\"0\": \"-\", \"1\": \"-\", \"2\": \"-\", \"3\": \"-\", \"4\": \"-\", \"5\": \"-\", \"6\": \"-\", \"7\": \"-\"}, \"alertVelViento\": {\"0\": \"-\", \"1\": \"-\", \"2\": \"X\", \"3\": \"-\", \"4\": \"-\", \"5\": \"-\", \"6\": \"-\", \"7\": \"-\"}, \"alertTmpMax\": {\"0\": \"-\", \"1\": \"-\", \"2\": \"-\", \"3\": \"-\", \"4\": \"-\", \"5\": \"X\", \"6\": \"-\", \"7\": \"-\"}, \"alertTmpMin\": {\"0\": \"-\", \"1\": \"X\", \"2\": \"-\", \"3\": \"-\", \"4\": \"-\", \"5\": \"-\", \"6\": \"-\", \"7\": \"-\"}, \"recomendaciones\": {\"lluvias\": \"Realice una revisi\\u00f3n y limpieza a la red de desague y canales existentes ENTER8 Cuente con una estaci\\u00f3n de bombeo, que debe estar ubicada en el punto m\\u00e1s bajo del predio. Aseg\\u00farese de encender y probar el sistema de bombeo al menos una vez al mes y hacer un mantenimiento mensual al equipo de bombeoENTER8 Los productos alojados en zonas de almacenamiento deben mantenersen sobre estibas - estanterias, con el fin de que no entren en contacto directo con el agua.\", \"vientos\": \"-\", \"temperatura\": \"-\"}}
'''
data = json.loads(jsonString)
```

Revise los campos: 'alertAlertas', 'alertPrecip', 'alertTmpMax', 'alertTmpMin', 'alertVelViento'. Para cada uno identifique si se presentan alertas ({0: x} indica que el día 0 habra un fenomeno de la alerta en cuestión, {1:"-"} indica que no habrá ningun fenomeno climatico). En caso que se presente una alerta obtenga la fecha del campo 'dt' ([aquí](https://stackoverflow.com/questions/3682748/converting-unix-timestamp-string-to-readable-date) pueden revisar como se convierte de UTC a fecha), así como los parametros relevantes del evento (e.g. si es un fenomeno de lluvias, busqye el nivel de lluvia, si es vientos, la velocidad del viuento). Al final deberá imprimir las fechas de alerta, el tipo de alerta y las variables asociadas

*Desarrollo*

```python
import json
from datetime import datetime

# Convertir UTC a fecha legible
def convertir_utc_a_fecha(utc_timestamp):
    return datetime.utcfromtimestamp(utc_timestamp).strftime('%Y-%m-%d')

# Función para revisar alertas y obtener los parámetros relevantes
def revisar_alertas(data):
    # Revisar cada día en los datos
    for i in range(8):  # Son 8 días de pronóstico
        fecha = convertir_utc_a_fecha(data["dt"][str(i)])
        
        # Revisar alertas y obtener parámetros relevantes
        if data["alertPrecip"][str(i)] == "X":
            lluvia = data["prcp"][str(i)]
            print(f"Alerta de lluvia el {fecha}: Precipitación = {lluvia} mm")
        
        if data["alertVelViento"][str(i)] == "X":
            velocidad_viento = data["velViento"][str(i)]
            print(f"Alerta de viento el {fecha}: Velocidad del viento = {velocidad_viento} m/s")
        
        if data["alertTmpMax"][str(i)] == "X":
            temperatura_maxima = data["tmpMax"][str(i)]
            print(f"Alerta de temperatura máxima el {fecha}: Temp. Máx = {temperatura_maxima} °C")
        
        if data["alertTmpMin"][str(i)] == "X":
            temperatura_minima = data["tmpMin"][str(i)]
            print(f"Alerta de temperatura mínima el {fecha}: Temp. Mín = {temperatura_minima} °C")
        
        if data["alertAlertas"][str(i)] == "X":
            print(f"Alerta general el {fecha}: Revisa otros fenómenos climáticos.")

# Cargar archivo JSON (simulación)
jsonString = '''
{
    "dt": {"0": 1685116800, "1": 1685203200, "2": 1685289600, "3": 1685376000, "4": 1685462400, "5": 1685548800, "6": 1685635200, "7": 1685721600},
    "alertPrecip": {"0": "X", "1": "-", "2": "-", "3": "-", "4": "-", "5": "-", "6": "-", "7": "-"},
    "alertVelViento": {"0": "-", "1": "-", "2": "X", "3": "-", "4": "-", "5": "-", "6": "-", "7": "-"},
    "alertTmpMax": {"0": "-", "1": "-", "2": "-", "3": "-", "4": "-", "5": "X", "6": "-", "7": "-"},
    "alertTmpMin": {"0": "-", "1": "X", "2": "-", "3": "-", "4": "-", "5": "-", "6": "-", "7": "-"},
    "alertAlertas": {"0": "-", "1": "-", "2": "-", "3": "-", "4": "-", "5": "-", "6": "-", "7": "-"},
    "prcp": {"0": 40.0, "1": 1.65, "2": 14.01, "3": 5.07, "4": 16.55, "5": 2.17, "6": 2.77, "7": 1.73},
    "velViento": {"0": 3.56, "1": 5.07, "2": 5.38, "3": 3.95, "4": 4.74, "5": 3.75, "6": 4.08, "7": 5.94},
    "tmpMax": {"0": 27.16, "1": 31.1, "2": 30.2, "3": 29.5, "4": 28.87, "5": 29.78, "6": 28.96, "7": 28.25},
    "tmpMin": {"0": 25.64, "1": 24.64, "2": 25.84, "3": 25.56, "4": 25.72, "5": 24.86, "6": 25.96, "7": 25.47}
}
'''

# Cargar el JSON
data = json.loads(jsonString)

# Revisar alertas y obtener la información relevante
revisar_alertas(data)
```







