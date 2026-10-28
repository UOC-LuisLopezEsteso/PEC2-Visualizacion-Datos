# Bump Chart — Evolución de posiciones de series de anime

Esta carpeta reúne el material del bump chart de la PEC 2 de Visualización de Datos.

El objetivo es comparar cómo cambia la posición relativa de las series de anime a lo largo del tiempo.

## Datos

El archivo [anime.csv](data/anime.csv) conserva sin modificaciones el CSV aportado: `time_series_Worldwide_20040101-0100_20261028-0922_transpuesta.csv`.

El archivo está transpuesto: cada fila corresponde a una serie, identificada en `Time`; incluye una columna `logo` y columnas mensuales entre enero de 2004 y diciembre de 2025. Los valores originales son índices de interés relativo; las posiciones se calculan por mes. No representan cifras de audiencia ni volúmenes absolutos de búsquedas.

## Cálculo de posiciones

[anime-posiciones.csv](data/anime-posiciones.csv) contiene la clasificación derivada del CSV original: cinco series y 264 meses, de enero de 2004 a diciembre de 2025. Mantiene las columnas `Time`, `logo` y los meses para facilitar la comparación o importación en Flourish.

Para cada mes se ordenan los índices de mayor a menor. Se utiliza **ranking de competición**: `puesto = 1 + número de series con un índice estrictamente mayor`. Por ejemplo, los valores 10, 10 y 5 producen los puestos 1, 1 y 3. Los empates comparten puesto y se dejan los saltos correspondientes; no se desempata por nombre ni por orden de fila.

Los ceros del archivo original se mantienen como valores de entrada. Un dato vacío se dejaría sin posición y no se convertiría en cero. La columna `logo` no interviene en el cálculo. El eje de posiciones se interpreta con 1 en la parte superior.

En una hoja de cálculo, para cinco valores numéricos de un mismo mes en B2:B6, se puede reproducir con `=RANK.EQ(B2,B$2:B$6,0)` (o la función equivalente en el idioma de la aplicación) y copiar hacia abajo y a los demás meses.

## Fuente e interpretación

La visualización publicada cita Google Trends y compara el interés de búsqueda mundial de Dragon Ball Z, Naruto: Shippuden, One Piece, Attack on Titan y Demon Slayer. El ranking se limita a estas cinco series. Los índices se utilizan tal como aparecen en el CSV aportado, sin recalibrarlos ni reconstruir su consulta de extracción.

La comparación presupone una escala común entre series. El CSV por sí solo no documenta todos los parámetros de la consulta de Google Trends, por lo que no permite verificar de forma independiente esa condición. Los resultados deben presentarse como posiciones derivadas de los índices aportados, sin inferir cifras de audiencia o una clasificación de todos los animes.

## Visualización

[Ver la visualización interactiva en Flourish](https://public.flourish.studio/visualisation/30718545/).

También está integrada en la [página principal del proyecto](https://uoc-luislopezesteso.github.io/PEC2-Visualizacion-Datos/#bump-chart) mediante el código responsive de Flourish. La visualización interactiva requiere conexión a Internet.

[Volver al repositorio](../README.md)
