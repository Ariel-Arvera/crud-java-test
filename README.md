# CRUD Test

Esto es un proyecto medio boludo pero funcional, un API REST basica hecho con Spring Boot.
Hecho a mano con documentacion de sitios como stackoverflow y otros, la IA solo se uso para corregir errores especificos.

## Que hace

Bue, basicamente hace las operationes clasicas de toda la vida:
- Ver todos los usuarios
- Ver un usuario por ID
- Guardar un usuario nuevo
- Actualizar un usuario
- Borrar un usuario

Eso nomas, un CRUD basico de usuarios.

## Tecnologia

- Java 17
- Spring Boot
- Maven
- H2 para desarrollo, MySQL para production

## Como levantarlo

Si tenes Maven instalado, hace:

```bash
./mvnw spring-boot:run
```

Despues podes probar los endpoints con Postman o lo que sea:

- GET /user - lista todos los users
- GET /user/{id} - busca un user por id
- POST /user - crea un user nuevo
- PUT /user/{id} - actualiza un user
- DELETE /user/{id} - borra un user

## Testing

Para correr los tests:

```bash
./mvnw test
```

Y si queres compilar todo:

```bash
./mvnw clean install
```

## Estructura

El proyecto esta dividido en:
- models - las entidades
- repositories - para interacting con la base de datos
- services - la logica de negocio
- controllers - los endpoints

Bue, nada del otro mundo, es un proyecto simple para probar cosas.
