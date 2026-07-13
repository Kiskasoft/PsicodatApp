# Spec: [Nombre del Módulo o Endpoint]

## Descripción
Define en 1 o 2 oraciones máximo qué hace esta pieza de software y cuál es su propósito en el sistema.

## Entradas

## Salidas

## Reglas de negocio

El corazón de la especificación. Usa viñetas claras y lenguaje imperativo "Debe", "Requiere", "Calcula".

Ejemplo:
- La contraseña debe ser encriptada usando [Algoritmo] antes de guardarse.
    
- El campo `fecha` se debe guardar en formato UTC.
    
- Si el usuario no tiene rol de admin, el sistema debe ignorar el campo `privilegios`.

## Criterios de aceptación

Condiciones exactas que determinan si la tarea está terminada.

## Casos límite (Edge cases)

Qué pasa cuando las cosas salen mal. El agente usará esto para generar los `try/catch` y las pruebas unitarias

## Dependencias

Servicios externos, bases de datos o funciones auxiliares que esta pieza necesita llamar

- Base de datos: Tabla `Usuarios`.
    
- Servicio externo: API de envío de correos (Módulo `EmailSender`).