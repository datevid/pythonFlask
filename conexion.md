test de conexión con la DB en mysql
```python
from flask import Flask
from flask_sqlalchemy import SQLAlchemy
from sqlalchemy.sql import text
from sqlalchemy.exc import SQLAlchemyError
from flask import jsonify
from flask import Response

import codecs

app = Flask(__name__)
app.config['SQLALCHEMY_DATABASE_URI'] = 'mysql+pymysql://user:password@localhost/databasename'  # Actualiza con tu configuraci��n
db = SQLAlchemy(app)



def check_db_connection():
    try:
        db.session.execute(text("SELECT 1"))  # Ejecuta una consulta de prueba
        return 'Exito a la base de datos á.'
    except SQLAlchemyError as e:
        return 'error a la base de datos: ' + str(e)


def get_personas_as_json():
    try:
        sql_query = text('SELECT * FROM `persona`')
        results = db.session.execute(sql_query)
        
        personas = []
        for row in results:
            persona = {
                'id': row.id,
                'nombre': row.nombre,
                'apellidos': row.apellidos
            }
            personas.append(persona)
        
        return jsonify(personas)
    except Exception as e:
        return jsonify({'error': 'Error base de datos: ' + str(e)})

    
@app.route('/')
def index():
    result= get_personas_as_json()
    return result
    
@app.route('/check')
def check():
    result=check_db_connection()
    return result

if __name__ == '__main__':
    app.run()
```
