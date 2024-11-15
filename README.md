# Endpoints de la API

A continuación se describen los principales endpoints de la API con ejemplos de solicitud y respuesta.

## Autenticación

### Obtener token de autenticación

- **Método**: POST
- **Endpoint**: `/login`
- **Encabezado de la solicitud**:
  - `Authorization`: Credenciales en formato básico (`username:password` codificados en base64).

#### Cuerpo de la solicitud

```json
{
    "username": "tu_usuario",
    "password": "tu_contraseña"
}


Ejemplo de respuesta

{
    "Token": "Bearer tu_token_de_autenticacion"
}



## **POST /users**

### **Método:**  
`POST`

### **Endpoint:**  
`/users`

### **Cabecera de la Solicitud:**  
Para acceder a este endpoint, se requiere un token de autorización JWT:  

Authorization: Bearer <token>
Descripción:
Crea un nuevo usuario. Solo los usuarios administradores pueden realizar esta acción.

Cuerpo de la Solicitud:
Debe enviarse un JSON con los siguientes campos:


{
  "usuario": "nuevo_usuario",
  "contrasenia": "123456"
}

Si el administrador crea el usuario correctamente, la respuesta será la siguiente:

{
  "Mensaje": "Usuario creado correctamente",
  "Usuario": {
    "id": 3,
    "usuario": "nuevo_usuario",
    "is_admin": false
  }
}

Si el usuario que realiza la solicitud no es un administrador, la respuesta será:

{
  "Mensaje": "Solo el admin puede crear nuevos usuarios"
}

Si ocurre un error al crear el usuario, la respuesta será:

{
  "Mensaje": "Fallo la creacion del nuevo usuario"
}
