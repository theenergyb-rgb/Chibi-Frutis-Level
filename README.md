# Chibi Frutis - Configuración de Niveles

Este repositorio contiene la configuración de niveles y reglas para el juego **Chibi Frutis**.

## Estructura

- `levels/` - Bloques de 100 niveles en formato JSON (101-200, 201-300, etc.)
- `generator/` - Reglas del generador de niveles procedurales
- `notifications/` - Configuración del sistema de notificaciones
- `version.json` - Control de versión global

## Niveles

### Niveles 1-100
Permanecen en el APK (archivo XML local) y no se modifican.

### Niveles 101+
Se descargan dinámicamente desde este repositorio en bloques de 100:
- Al completar nivel 100 → Se descargan niveles 101-200
- Al completar nivel 200 → Se descargan niveles 201-300
- Y así sucesivamente...

## Formato de Niveles

Cada nivel puede ser de dos tipos:

### 1. Generado (Procedimental)
```json
{
  "type": "generated",
  "templateFrom": 15,
  "theme": "auto",
  "moves": 25,
  "hardLevel": false
}
```

### 2. Fijo (Custom)
```json
{
  "type": "fixed",
  "row": 7,
  "column": 7,
  "move": 25,
  "fruitCount": 4,
  "grid": "...",
  "tile": "...",
  "targets": [
    {"type": "strawberry", "count": 30}
  ]
}
```

## Editar Niveles

Para modificar niveles existentes o agregar nuevos:

1. Edita el archivo JSON correspondiente en `levels/`
2. Haz commit y push a la rama `main`
3. Los usuarios descargarán la nueva versión automáticamente

**Nota:** No es necesario subir una nueva versión a Google Play.

## Generator Rules

Las reglas en `generator/rules.json` controlan:
- Frutas permitidas
- Temas y combinaciones de obstáculos
- Formulas de dificultad
- Intervalo de niveles difíciles

## Notificaciones

La configuración en `notifications/config.json` controla:
- Mensajes motivacionales
- Frecuencia de notificaciones
- Enable/disable por tipo

---

**Versión actual:** 1.0.0  
**Última actualización:** 2026-01-31
