# Módulo Hechos — Guía de instalación

## 1. Dónde colocar cada archivo

Copia cada archivo a la misma ruta relativa dentro de tu proyecto Next.js existente:

```
tu-proyecto/
  db/
    connection.js          <- ya lo tienes de la guía original, no lo dupliques
  models/
    hechosModel.js          <- NUEVO
  app/
    api/
      hechos/
        route.js             <- NUEVO
        [id]/
          route.js            <- NUEVO
    hechos/
      page.js                <- NUEVO
      styles.module.css       <- NUEVO
```

Si ya tienes `db/connection.js` de tu CRUD de `localidad`, NO lo reemplaces — es el mismo archivo y ya funciona.

## 2. ⚠️ VERIFICAR ANTES DE PROBAR

El modelo (`hechosModel.js`) y la vista (`page.js`) asumen estos nombres de columna que NO confirmamos con captura de pantalla:

| Tabla | Columna asumida | Verifica con |
|---|---|---|
| `Convocatoria` | `Convocatoria` (nombre) | `DESCRIBE Convocatoria;` |
| `Institucion` | `NOMBRE_INSTITUCION` | `DESCRIBE Institucion;` |
| `Nucleo_Basico` | `Nucleo_Basico` | `DESCRIBE Nucleo_Basico;` |
| `Sexo` | `Id_Sexo`, `Sexo` | `DESCRIBE Sexo;` |

Si alguno de estos nombres no coincide exactamente (mayúsculas, guiones bajos, espacios), tendrás un error tipo `Unknown column 'X' in 'field list'`. En ese caso, solo necesitas:
1. Abrir `models/hechosModel.js`
2. Buscar el nombre incorrecto en el `SELECT` del método `getAll` y en `getCatalogos`
3. Reemplazarlo por el nombre real

También revisa la tabla `Hechos`: confirmamos que tiene `Id_Sector`, `Id_Zona`, `Id_Saber11`, `Id_Sexo`, `Id_Edad`, `Id_Grupo_Etnico`, `Id_Victima`, `Id_Discapacidad`, `Id_Sisben`, `Id_Convocatoria`, `Id_Localidad`, `Id_Institucion`, `Id_Nucleo`, `Cant_beneficiarios` — estos SÍ están confirmados con tu captura de DBeaver.

## 3. Probar

```bash
npm run dev
```

Visita: `http://localhost:3000/hechos`

Deberías ver:
- Un formulario arriba con 14 dropdowns + 1 campo numérico
- Una tabla abajo con todos los registros de `Hechos`, mostrando nombres legibles (no IDs)
- Botones "Editar" y "Borrar" en cada fila

## 4. Si algo falla

- **Error 500 al cargar la página**: revisa la consola del servidor (terminal donde corre `npm run dev`) — ahí verás el mensaje SQL exacto, probablemente un nombre de columna incorrecto.
- **Los `<select>` aparecen vacíos**: el catálogo correspondiente puede tener otro nombre de tabla o columna distinto al asumido.
- **El formulario no guarda**: abre la consola del navegador (F12) y revisa la pestaña Network al hacer submit, para ver el error que devuelve la API.

---

Cuando confirmes que esto funciona, seguimos con los siguientes módulos: `Localidad` (READ, UPDATE, DELETE) y `Discapacidad` (READ, INSERT), que son mucho más simples porque no tienen FKs.
