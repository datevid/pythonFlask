
Ejemplo e autenticación básica para proteger urls:
```java

# Función de autenticación básica
def basic_auth(username, password):
    # Verificar las credenciales del usuario
    # Esto es solo un ejemplo, debes implementar tu propio mecanismo de verificación
    if username == 'usuario' and password == 'contrasena':
        return True
    else:
        return False

# Decorador para requerir autenticación básica
def require_basic_auth(f):
    def decorated(*args, **kwargs):
        auth = request.authorization
        if not auth or not basic_auth(auth.username, auth.password):
            # Si las credenciales no son válidas, retorna una respuesta de error
            return jsonify({'error': 'Autenticación fallida'}), 401
        return f(*args, **kwargs)
    return decorated

# Ruta protegida que requiere autenticación básica
@app.route('/api/secure')
@require_basic_auth
def secure_endpoint():
    return jsonify({'message': 'Acceso permitido'})
    
# Ruta pública sin autenticación
@contacts.route('/')
def public_endpoint():
    return jsonify({'message': 'Hola, mundo'})
```
