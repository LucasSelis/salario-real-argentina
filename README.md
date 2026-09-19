# Salario real en Argentina, 2016-2026

Análisis económico con datos públicos: cuánto poder de compra perdió y recuperó el salario registrado del sector privado frente a la inflación, de diciembre de 2016 a hoy.

**Dashboard interactivo:** https://lucasselis.github.io/salario-real-argentina/

## Qué responde

- ¿Cuánto compra hoy un salario respecto de diciembre de 2016?
- ¿Cuál fue el mejor momento y cuál el peor de la serie?
- ¿Qué años le ganó la inflación al salario y cuáles no (variación de diciembre a diciembre)?

## Datos

Dos series del INDEC publicadas en [datos.gob.ar](https://datos.gob.ar/) (API de Series de Tiempo):

| Serie | ID | Descripción |
|---|---|---|
| IPC | `148.3_INIVELNAL_DICI_M_26` | Nivel general nacional, base dic-2016 = 100, mensual |
| Salarios | `149.1_SOR_PRIADO_OCTU_0_25` | Índice de salarios, empleo registrado del sector privado, base oct-2016 = 100, mensual |

`data.csv` es una copia de los datos procesados (base dic-2016 = 100 para las tres columnas).

## Método

1. Se piden las dos series a la API en vivo desde el navegador (con una copia de respaldo incluida en `index.html`).
2. Se descartan los meses en que falta alguno de los dos datos (el INDEC publica salarios con más rezago que precios).
3. Se lleva el salario a base dic-2016 = 100 dividiéndolo por su valor de diciembre de 2016.
4. Salario real = `salario / IPC x 100`.
5. Variación anual = de diciembre a diciembre; la ganancia o pérdida real es `(1 + salario) / (1 + inflación) - 1`.

## Resultado (con los datos hasta jun-2026)

- Salario real hoy: **79,4** (dic-2016 = 100), es decir, 20,6% por debajo.
- Pico: **104,9** en ago-2017. Piso: **72,3** en mar-2024, una caída de 31,0% desde el pico.
- Desde el piso se recuperó 9,8%, pero sigue 24,3% por debajo del pico.
- Peor año: 2023 (inflación 211,4% vs. salario 165,8%, pérdida real de 14,7%). Mejor año: 2024 (ganancia real de 13,7%).

## Límites

- El índice cubre solo empleo registrado privado, sin informales ni sector público.
- Es un promedio: no describe la situación de una persona en particular.
- Si el INDEC revisa las series, los números del dashboard cambian; los de este README corresponden a la fecha de la última actualización.

## Stack

HTML, CSS y JavaScript sin dependencias. Gráficos en SVG dibujados a mano. Datos por API REST.

---

Lucas Selis · Data Analyst & BI · [LinkedIn](https://www.linkedin.com/in/lucas-selis/)
