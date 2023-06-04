# Introducción:
Si te da pereza puedes ver el video de la configuración de un proyecto en Flask y Cpanel

https://www.youtube.com/watch?v=260eDcsUheE

https://www.youtube.com/watch?v=xFxL7Mvut6g

# Pasos:
1. Crear la aplicación Setup Python App 
  - Configuracion: Aplication root: es el path de tu directorio creao
  - Application URL: backperulia01
  - Application startup file: siempre será app.py
  - Aplication Entry point: siempre será app
  
2.  Instalar flask
Ingresar a la terminal
Enter to the virtual environment.To enter to virtual environment, run the command: 
```
source /home/peruwezw/virtualenv/backperulia01/3.9/bin/activate && cd /home/peruwezw/backperulia01
```
Instalar flask
```
pip install flask
```
    
4.  ir al file manager o gestor de archivos del cpanel y ubicar el proyecto. En este ejemplo backperulia01. Editar archivo app.py
Copiar el código de testeo
Test de configuración de un proyecto en Flask y Cpanel

```
from flask import Flask

app = Flask(__name__)

@app.route('/')
def index():
    return "hola mundo"
    
if __name__ == '__main__':
    app.run()
```

5.  Probar

http://domain.com/backperulia01/
