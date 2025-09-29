# Twitter-Crypto-Impact
Repositorio del Trabajo de Fin de Grado sobre Finanzas Conductuales: análisis del impacto de los tweets de Elon Musk (2020-2025) en la volatilidad de Bitcoin y Dogecoin. Incluye la memoria completa, hojas de cálculo en Excel, gráficos y materiales de apoyo.

## Trabajo de Fin de Grado — Finanzas Conductuales

Este repositorio contiene mi TFG sobre **la influencia de los tweets de Elon Musk (2020–2025) en la volatilidad de Bitcoin y Dogecoin**, realizado en el Grado en Administración y Dirección de Empresas (Universidad Rey Juan Carlos).

## Contenido
- `docs/` → Documento final del TFG 
- `data/` → Datos de precios (muestras, no originales completos)
- `excel/` → Hojas de cálculo con fórmulas y análisis

##Formulas
1. Cálculo de rentabilidades
=SI(C3="";"";C3/C2-1)
Objetivo: calcular la rentabilidad diaria de un activo.
Explicación: compara el precio actual con el anterior y devuelve la variación porcentual.
Si la celda está vacía → no devuelve nada.

2. Cálculo de volatilidad en ventanas temporales
=SI.ERROR(
   DESVEST.M(
      FILTRAR(Diario!$J:$J;
         (Diario!$A:$A>=Tweets!A3-3)*(Diario!$A:$A<=Tweets!A3-1)
      )
   );
   ""
)
Objetivo: calcular la desviación estándar muestral (volatilidad) de las rentabilidades en la hoja Diario, durante los 3 días previos a un tweet.
Explicación:
  FILTRAR selecciona los valores de la columna J según el rango de fechas.
  DESVEST.M calcula la desviación estándar.
  SI.ERROR evita errores si no hay datos, devolviendo celda vacía.
3. Clasificación por percentiles (cuartiles)
=SI(G2<=PERCENTIL.INC($G:$G;0,25);"Bajo";
   SI(G2<=PERCENTIL.INC($G:$G;0,5);"Medio";
      SI(G2<=PERCENTIL.INC($G:$G;0,75);"Alto";"Muy alto")
   )
)
Objetivo: clasificar los valores en cuartiles.
Explicación:
Percentil 25 → "Bajo".
Percentil 50 → "Medio".
Percentil 75 → "Alto".
Más allá → "Muy alto".
4. Gestión de errores y valores vacíos
Muy usada en tu Excel:
SI.ERROR(...; "") → devuelve celda vacía si hay error.
SI(celda="";""; cálculo ) → evita operaciones sobre celdas vacías.

## Cómo citar
> Aileni, R. A. (2025). *La influencia de las redes sociales en la volatilidad de las criptomonedas: un análisis de sentimiento basado en los tweets de Elon Musk*. Trabajo de Fin de Grado, URJC.
