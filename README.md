# instalacion-blender-primer-programa-poligono-2d
Nos dirigimos al buscador de su preferencia y buscamos "Blender"
<img width="1075" height="493" alt="image" src="https://github.com/user-attachments/assets/7b85b506-16ac-43c1-9bf9-ab9504eea9c8" />
Entramos al primer resultado de la busqueda
<img width="1606" height="409" alt="image" src="https://github.com/user-attachments/assets/fd9547ad-d850-4733-b3d6-9208d62a470d" />
Tenemos que entrar al apartado de "DOWNLOAD"
<img width="1919" height="1028" alt="image" src="https://github.com/user-attachments/assets/349e3683-603b-4932-9f5e-e9057c040919" />
Procedemos a descargar la version adecuada para tu sistema operativo 
Al terminar la descarga, procedemos a la instalacion, no se requiere ninguana configuracion extra asi que solo ejecutamos el instalador de damos a todo "SIGUIENTE" Y FINALIZAMOS.
Posteriormente abrimos nuestro programa
<img width="1919" height="1134" alt="image" src="https://github.com/user-attachments/assets/aa110ffe-82fc-4d49-bf29-f9a5c11815b4" />
Nos diriguimos en el menu al apartado de "SCRIPTING"
<img width="1918" height="1137" alt="image" src="https://github.com/user-attachments/assets/801c4f98-87e2-4c3c-8fb4-b03cbf8e486e" />
Una vez dentro del menú nos dirigimos al apartado de "NEW", como se muestra en la siguiente imagen
<img width="1918" height="1141" alt="image" src="https://github.com/user-attachments/assets/de4fdbae-8b89-4e4e-a944-f00fbe5d9f39" />
Se nos habilitará una sección para ingresar codigo, donde posteriormente ingresaremos el siguiente codigo
<img width="1919" height="1137" alt="image" src="https://github.com/user-attachments/assets/624d1dc9-7953-4a64-8024-222621ee5b70" />
El codigo a ingresar es el siguiente:
import bpy
import math

def crear_poligono_2d(nombre, lados, radio):
    """
    Genera un polígono regular en 2D dentro del entorno de Blender.
    Aplica conceptos de trigonometría para el cálculo de vértices.
    """
    malla = bpy.data.meshes.new(nombre)
    objeto = bpy.data.objects.new(nombre, malla)

### 🐍 Script para Generación de Polígono 2D en Blender

Copia y pega el siguiente código en el editor de texto de Blender:

```python
import bpy
import math

def crear_poligono_2d(nombre, lados, radio):
    malla = bpy.data.meshes.new(nombre)
    objeto = bpy.data.objects.new(nombre, malla)

    bpy.context.collection.objects.link(objeto)

    vertices = []
    aristas = []

    for i in range(lados):
        angulo = 2 * math.pi * i / lados 
        x = radio * math.cos(angulo)
        y = radio * math.sin(angulo)
        vertices.append((x, y, 0))

    for i in range(lados):
        aristas.append((i, (i + 1) % lados))
    
    malla.from_pydata(vertices, aristas, [])
    malla.update()

bpy.ops.object.select_all(action="SELECT")
bpy.ops.object.delete()
    
crear_poligono_2d("poligono 2d", lados=6, radio=3)
```
Ya escrito el codigo en la aplicación se visualiza de la siguiente manera
<img width="1919" height="1137" alt="image" src="https://github.com/user-attachments/assets/daa47fda-2e1f-4d69-ab9c-f714c5c79ff2" />
Para ejecutar el codigo nos dirigimos al triangulito señalado en la imagem y en la esquina superior derecha veremos el poligono generado por el codigo
<img width="1918" height="1142" alt="image" src="https://github.com/user-attachments/assets/474b1215-c904-4779-bffc-f5585cf300f5" />
Con esto concluimos que hemos terminado nuestra práctica de manera exitosa

REPORTE: Creación de una Flor con Círculos en Blender usando Python
1. Introducción

El presente reporte describe el procedimiento para crear una figura con forma de flor mediante el uso de círculos generados con un script en Python dentro de Blender.

La figura se compone de:

Un círculo central.

Doce círculos distribuidos uniformemente alrededor del centro.

La distribución se realiza utilizando coordenadas polares convertidas a coordenadas cartesianas mediante funciones trigonométricas.

<img width="1890" height="1130" alt="image" src="https://github.com/user-attachments/assets/65353978-2c02-49a9-9c26-4673787a7134" />


2. Objetivo

Generar una figura geométrica tipo flor utilizando programación en Blender, aplicando cálculos matemáticos para posicionar los círculos de manera simétrica.

3. Desarrollo del Código
3.1 Limpieza de la escena
bpy.ops.object.select_all(action='SELECT')
bpy.ops.object.delete()

Esta sección selecciona todos los objetos presentes en la escena y los elimina.
El propósito es iniciar el proyecto en un entorno vacío para evitar interferencias con objetos previos.

<img width="506" height="674" alt="image" src="https://github.com/user-attachments/assets/181e054e-2b1b-46ae-88b8-898fcd8837b2" />
<img width="462" height="675" alt="image" src="https://github.com/user-attachments/assets/c57e1f10-bb10-4efa-8ba0-4bc7f9a11527" />


3.2 Definición de parámetros
radio = 3
angulo_actual = 0
paso_angular = 30

Se establecen los valores principales:

radio: tamaño de cada círculo.

angulo_actual: ángulo inicial en grados.

paso_angular: incremento angular entre cada círculo.

Dado que 360° dividido entre 30° es igual a 12, el programa generará 12 círculos alrededor del centro.

3.3 Creación del círculo central
bpy.ops.mesh.primitive_circle_add(radius=radio, location=(0, 0, 0), vertices=64)

Se crea un círculo en el origen (0, 0, 0).
El parámetro vertices=64 permite que el círculo tenga mayor suavidad visual.

Este círculo representa el centro de la flor.

<img width="1666" height="972" alt="image" src="https://github.com/user-attachments/assets/4f2ae02c-a262-4c09-8944-f08c15ce1045" />


3.4 Creación de los círculos periféricos
while angulo_actual < 360:

Se utiliza un ciclo while que se ejecuta hasta completar 360 grados.

Dentro del ciclo se calculan las coordenadas utilizando fórmulas trigonométricas:

x = radio * math.cos(math.radians(angulo_actual))
y = radio * math.sin(math.radians(angulo_actual))

Estas fórmulas convierten el ángulo en coordenadas cartesianas:

x = r cos(θ)

y = r sin(θ)

De esta manera se posiciona cada círculo alrededor del centro.

Posteriormente se crea el círculo:

bpy.ops.mesh.primitive_circle_add(radius=radio, location=(x, y, 0), vertices=64)

Finalmente, el ángulo se incrementa:

angulo_actual += paso_angular

Este proceso se repite hasta completar los 360 grados.

<img width="1856" height="1058" alt="image" src="https://github.com/user-attachments/assets/d269d571-2b35-4e33-a5a6-37a001b9fcf1" />


4. Resultado

El resultado es una figura simétrica compuesta por:

1 círculo central.

12 círculos externos.

Distribución uniforme.

Simetría radial completa.

La superposición parcial de los círculos produce la forma similar a una flor.

<img width="1340" height="928" alt="image" src="https://github.com/user-attachments/assets/78c7ae22-8e64-4776-bed9-5c8aa56e1f95" />


5. Fundamento Matemático

El diseño se basa en:

División del círculo completo (360°).

Uso de coordenadas polares.

Conversión a coordenadas cartesianas.

Aplicación de funciones seno y coseno.

Simetría radial.

Estos conceptos permiten crear patrones geométricos de manera automatizada.

6. Conclusión

El script demuestra cómo es posible combinar programación y matemáticas para generar modelos geométricos en Blender.

Se aplican conceptos de:

Automatización mediante Python.

Uso de la API bpy.

Trigonometría aplicada al modelado 3D.

Estructuras de control (bucle while).

El ejercicio permite comprender cómo crear patrones simétricos a partir de formas simples.
