---
description: Aprende como realizar una benchmark a TF2 y medir FPS científicamente.
...

# Benchmarks

Benchmarking es el proceso en el que tú puedes científicamente medir el impacto de los cambios en tu sistema.

Una gran cantidad de datos de benchmarks es crucial para asegurar que mastercomfig funciona en una variedad de sistemas.

Por lo tanto, es muy importante realizar una benchmark a mastercomfig y cualquier cambio a tu sistema, para que entendamos mejor el impacto de estos.

## Como realizar una benchmark

1. Descarga [el archivo de benchmark](https://mega.nz/#!f8tlhDhR!nYgghqybOK15ObUykEczewB3242XHb_bJ4JP0rv1q6k).
2. Muevelo a la carpeta `tf/`.
3. Abre el juego.
4. Entra a `timedemo benchmark_test`
5. Graba el  `X frames X seconds X fps (X ms/f) X fps variability`.
6. Repite `timedemo benchmark_test` todas las veces que quieras para minimizar los efectos de variación sistemática.

## Datos de la benchmark

mastercomfig provee un servicio para registrar datos de benchmark, para que podamos mejorar basados en estos datos.

[**Formulario (En inglés)**](https://airtable.com/shrckjh0jqeZdeIYN)

[**Resultados**](https://airtable.com/shrxpulcQulOi16Wm)
