# InputsMapper - Tia Portal V16 or later -

Este bloque de función (FB) permite mapear, normalizar entradas digitales en un sistema de automatización industrial programado en Structured Text (ST). Está diseñado para ser **modular, configurable** y compatible con arquitecturas escalables.

## 🧩 ¿Qué hace?

- Mapea dinámicamente señales digitales desde un `BYTE` de entrada.
- Permite configurar el tipo de contacto (NA/NC) para cada entrada.
- Proporciona salidas limpias y filtradas (`SignalIn0..SignalIn7`) para el resto del programa.

## ⚙️ Parámetros

### Entrada (`inRawByte`):
- `inRawByte` → Byte de entrada con las señales digitales reales

### Entrada (`cfgSignalData`):
- `nSignalIndex[0..7]        ` → Mapeo de señal a índice interno
- `bSignalNormallyOpen[0..7]`  → Tipo de contacto (TRUE = NA, FALSE = NC)

### Salidas:
- `SignalIn0..SignalIn7` → Señales digitales filtradas y confiables

## 🛠️ Cómo se usa

1. Asigna los valores de configuración al bloque (`bSignalNormallyOpen`, `nSignalIndex`).
2. Asigna el byte de entrada (`inRawByte`).
3. Llama al FB cíclicamente.
4. Lee las salidas `INx` de señal según necesites.

### Ejemplo de integración
```pascal
InputsMapper(
  inRawByte := %IB10
  cfgSignalData.nSignalIndex := Config.Index,
  cfgSignalData.bSignalNormallyOpen:= Config.Type,
  SignalIn0=> (Señal filtrada) //Ejemplo Pulsador Start
  SignalIn1=> (Señal filtrada) //Ejemplo Pulsador Stop
  SignalIn2=> (Señal filtrada) //Ejemplo Pulsador Sensor S1
  SignalIn3=> (Señal filtrada) //Ejemplo Pulsador Sensor S2
  SignalIn4=> (Señal filtrada) //Ejemplo Pulsador Sensor S3
  SignalIn5=> (Señal filtrada) //Ejemplo Pulsador Sensor S4
  SignalIn6=> (Señal filtrada) //Ejemplo Pulsador Sensor S5
  SignalIn7=> (Señal filtrada) //Ejemplo Pulsador Sensor S6
);
