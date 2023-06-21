install.packages("quantmod")
library(quantmod)

# Descargar datos de MO desde Yahoo Finance
getSymbols("MO", src = "yahoo")

# Crear un gráfico de velas japonesas que muestra el precio de las acciones de MO
chartSeries(MO, type = "candlesticks", theme = "white")

# Agregar una línea de tendencia en rojo
addTA(EMA(Cl(MO), n = 20), on = 1, col = "red")

# Calcular el índice de fuerza relativa (RSI)
MO$RSI <- RSI(Cl(MO), n = 14)

# Crear un gráfico que muestra el RSI y el precio de cierre de las acciones de MO
chartSeries(MO, type = "line", theme = "white")
addRSI(n = 14, on = 1)
