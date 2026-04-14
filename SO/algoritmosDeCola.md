# Algoritmos de cola

- [Algoritmos de cola](#algoritmos-de-cola)
  - [Ejemplo base (para TODOS los algoritmos)](#ejemplo-base-para-todos-los-algoritmos)
  - [FIFO](#fifo)
    - [Definición](#definición)
    - [Observaciones](#observaciones)
    - [Gráfico](#gráfico)
  - [Round Robin (RR)](#round-robin-rr)
    - [Definición](#definición-1)
    - [Observaciones](#observaciones-1)
    - [Gráfico](#gráfico-1)
  - [Round Robin Virtual (VRR)](#round-robin-virtual-vrr)
    - [Definición](#definición-2)
    - [Observaciones](#observaciones-2)
    - [Gráfico](#gráfico-2)
  - [SJF](#sjf)
    - [Sin desalojo](#sin-desalojo)
      - [Definición](#definición-3)
      - [Desempate](#desempate)
      - [Observaciones](#observaciones-3)
      - [Gráfico](#gráfico-3)
    - [Con desalojo (SRTF)](#con-desalojo-srtf)
      - [Definición](#definición-4)
      - [Desempate](#desempate-1)
      - [Observaciones](#observaciones-4)
      - [Gráfico](#gráfico-4)
  - [Prioridades](#prioridades)
    - [Apropiativas (con desalojo)](#apropiativas-con-desalojo)
      - [Definición](#definición-5)
      - [Observaciones](#observaciones-5)
    - [No apropiativas (sin desalojo)](#no-apropiativas-sin-desalojo)
      - [Definición](#definición-6)
      - [Observaciones](#observaciones-6)
    - [Gráfico](#gráfico-5)
  - [HRRN](#hrrn)
    - [Sin desalojo](#sin-desalojo-1)
      - [Definición](#definición-7)
      - [Observaciones](#observaciones-7)
    - [Con desalojo](#con-desalojo)
      - [Definición](#definición-8)
    - [Gráfico](#gráfico-6)
  - [Multicolas](#multicolas)
    - [Definición](#definición-9)
    - [Observaciones](#observaciones-8)
    - [Gráfico](#gráfico-7)
  - [CONCEPTO: INANICIÓN](#concepto-inanición)
    - [Definición](#definición-10)
    - [Ejemplos](#ejemplos)
  - [Resumen](#resumen)


> [!NOTE]
> **Criterio general de desempate (cátedra):**  
> 1) Syscall  
> 2) I/O  
> 3) Proceso nuevo  
>
> Si empatan dentro de la misma categoría → **orden alfabético**

---

## Ejemplo base (para TODOS los algoritmos)

| P | Arr | CPU | I/O | CPU | I/O | CPU |
|--|--|--|--|--|--|--|
| A | 1 | 4 | 1 | 2 | 1 | 3 |
| B | 0 | 2 | 1 | 4 | 1 | 3 |
| C | 2 | 3 | 1 | 4 | 1 | 2 |

> [!NOTE]
> Cada proceso alterna entre ráfagas de **CPU** e **I/O**.  
> Cuando termina CPU → pasa a I/O.  
> Cuando termina I/O → vuelve a la cola de listos.

---

## FIFO

### Definición

**First In, First Out**:

- El primer proceso en llegar es el primero en ejecutarse.
- **No hay desalojo**.
- La cola se ordena estrictamente por llegada.

### Observaciones

- Muy simple de implementar.
- Puede generar ****convoy effect****: un proceso largo bloquea a los demás.
- Respeta completamente el orden de llegada.

### Gráfico

> [!WARNING]
> Falta gráfico

---

## Round Robin (RR)

### Definición

Se define un quantum $Q$:

- Cada proceso ejecuta como máximo ****$Q$ unidades de tiempo****.
- Si no termina → es desalojado y vuelve al final de la cola.
- Si termina antes → libera CPU y sigue su flujo (I/O o fin).

### Observaciones

- Mejora la **equidad** entre procesos.
- ****$Q \to \infty$**** ⇒ se comporta como FIFO.  
- ****$Q \to 0$**** ⇒ alto overhead por cambios de contexto.

### Gráfico

> [!WARNING]
> Falta gráfico

---

## Round Robin Virtual (VRR)

### Definición

Extensión de RR:

- También usa quantum $Q$.
- Si un proceso **se bloquea antes de consumir todo su quantum**:
  - Al volver de I/O entra en una ****cola prioritaria****.
  - Ejecuta el ****resto del quantum**** pendiente.
- Luego vuelve a la cola normal.

### Observaciones

- Favorece procesos **interactivos** (mucho I/O).
- Reduce penalización por bloqueos tempranos.

### Gráfico

> [!WARNING]
> Falta gráfico

---

## SJF

### Sin desalojo

#### Definición

**Shortest Job First**:

- Se elige el proceso con ****menor ráfaga de CPU****.
- Una vez que comienza, ****no se interrumpe****.

#### Desempate

> [!IMPORTANT]
> Igual ráfaga → **FIFO**

#### Observaciones

- Minimiza el tiempo de espera promedio (teóricamente).
- Puede generar [****inanición****](conceptos.md#inanición) de procesos largos.

#### Gráfico

> [!WARNING]
> Falta gráfico

---

### Con desalojo (SRTF)

#### Definición

**Shortest Remaining Time First**:

- Se ejecuta siempre el proceso con ****menor tiempo restante****.
- Si llega uno más corto → ****desaloja**** al actual.

#### Desempate

1. Menor ráfaga restante  
2. FIFO  
3. Criterio cátedra (**syscall > I/O > nuevo**)

#### Observaciones

- Óptimo en tiempo de espera promedio.
- Requiere estimar ráfagas (no trivial).

#### Gráfico

> [!WARNING]
> Falta gráfico

---

## Prioridades

### Apropiativas (con desalojo)

#### Definición

- Cada proceso tiene una ****prioridad****.
- Se ejecuta el de mayor prioridad (menor valor).
- Si llega uno con mayor prioridad → ****desaloja****.

#### Observaciones

- Generaliza SJF (si prioridad = duración).
- Puede producir ****inanición****.

---

### No apropiativas (sin desalojo)

#### Definición

- Igual que el anterior pero ****sin desalojo****.
- El proceso actual termina su ráfaga antes de cambiar.

#### Observaciones

- Más simple pero menos reactivo.

### Gráfico

> [!WARNING]
> Falta gráfico

---

## HRRN

### Sin desalojo

#### Definición

**Highest Response Ratio Next**:

Se calcula:

$$
R = \frac{w + s}{s}
$$

Donde:

- $w$ = tiempo de espera  
- $s$ = tiempo de servicio (ráfaga)

Se elige el proceso con ****mayor $R$****.

#### Observaciones

- Evita inanición (aumenta prioridad con espera).
- Balance entre FIFO y SJF.

---

### Con desalojo

#### Definición

- Variante menos común.
- Recalcula continuamente $R$ y puede desalojar.

### Gráfico

> [!WARNING]
> Falta gráfico

---

## Multicolas

### Definición

- Existen múltiples colas de listos.
- Cada cola puede tener:
  - Su propio algoritmo (FIFO, RR, etc.)
  - Su propia política de desalojo

Se define además:

- ****Política ENTRE colas**** (prioridades entre colas)

### Observaciones

- Muy flexible.
- Usado en sistemas reales.

### Gráfico

> [!WARNING]
> Falta gráfico

---

## CONCEPTO: INANICIÓN

### Definición

Un proceso puede no ejecutarse nunca si:

- Siempre hay otros con mayor prioridad.

### Ejemplos

- SJF
- Prioridades

> [!WARNING]
> Problema crítico en sistemas reales

---

## Resumen

| Algoritmo | Desalojo | Ventaja | Problema |
|----------|--------|--------|---------|
| FIFO     | ❌     | Simple | Convoy |
| RR       | ✅     | Justo  | Overhead |
| VRR      | ✅     | Mejor I/O | Complejo |
| SJF      | ❌     | Óptimo | Inanición |
| SRTF     | ✅     | Más óptimo | Complejo |

---

> [!TIP]
> En parciales:
> - Revisar ****desempates****
> - Identificar ****desalojo****
> - Ver cuándo se ****reordena la cola****
> - Controlar eventos: llegada, fin CPU, fin I/O