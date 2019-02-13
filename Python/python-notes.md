# Notas de Python

## Comprensión de Listas

Las comprensiones de listas proporcionan una alternativa al uso de las funciones integradas `maps()` y `filter()` y se prefieren en el uso a éstas últimas.

La función `maps(f, S)` es equivalente a `[f(x) for x in S]`, mientras que `filter(P, S)` es equivalente a `[x for x in S if P(x)]`.
