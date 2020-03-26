# Django Tips

## Sesiones, Usuarios e Inscripciones

Averiguar los permisos definidos que existen en la base de datos del proyecto.

```py
>> permisos = list(request.user.get_all_permissions())
>> print(permisos)
```