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
