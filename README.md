# InputsMapper - Tia Portal V16 or later -

Este bloque de función (FB) permite mapear, normalizar entradas digitales en un sistema de automatización industrial programado en Structured Text (ST). Está diseñado para ser **modular, configurable** y compatible con arquitecturas escalables.

## 🧩 ¿Qué hace?

- Mapea dinámicamente señales digitales desde un `BYTE` de entrada.
- Permite configurar el tipo de contacto (NA/NC) para cada entrada.
- Proporciona salidas limpias y filtradas (`IN0..IN7`) para el resto del programa.

## ⚙️ Parámetros

### Entrada (`InputByte`):
- `InputByte` → Byte de entrada con las señales digitales reales

### Entrada (`InputData`):
- `Index[0..7]` → Mapeo de señal a índice interno
- `Type[0..7]`  → Tipo de contacto (TRUE = NA, FALSE = NC)

### Salidas:
- `IN0..IN7` → Señales digitales filtradas y confiables

## 🛠️ Cómo se usa

1. Asigna los valores de configuración al bloque (`Type`, `Index`).
2. Asigna el byte de entrada (`InputByte`).
3. Llama al FB cíclicamente.
4. Lee las salidas `INx`, alarmas y estado de señal según necesites.

### Ejemplo de integración
```pascal
InputsMapper(
  InputData.Type := Config.Type,
  InputData.Index := Config.Index,
  InputByte := %IB10
);
