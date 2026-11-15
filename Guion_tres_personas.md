# Guion de grabación para tres integrantes
Duración máxima prevista: 8 minutos y 25 segundos. Mostrar la presentación en pantalla completa.

## Diapositiva 1: Predicción de retrasos Olist | Persona 1 | 35 s
**Mostrar:** Proyecto Final de Analítica de Negocios
**Decir:** Buenos días. Analizamos cómo anticipar entregas que pueden llegar después de la fecha prometida en un comercio electrónico. También exploramos tipos de pedidos para orientar preguntas de logística.

## Diapositiva 2: Pregunta de negocio | Persona 1 | 40 s
**Mostrar:** ¿Podemos anticipar incumplimientos con información conocida al comprar?
**Decir:** Nuestra pregunta es si, con datos que ya se conocen al comprar, podemos identificar pedidos con riesgo de incumplir la promesa de entrega. La respuesta serviría para priorizar revisiones preventivas.

## Diapositiva 3: Datos | Persona 1 | 35 s
**Mostrar:** Olist: nueve tablas, unas 100.000 órdenes de 2016 a 2018. Fuente: Kaggle.
**Decir:** Usamos el conjunto público de Olist, disponible en Kaggle, con alrededor de cien mil órdenes y varias tablas relacionadas. El proyecto parte de la presentación preliminar, pero ahora define un flujo reproducible.

## Diapositiva 4: Unidad y etiqueta | Persona 1 | 35 s
**Mostrar:** Una fila por order_id. Tardía = entrega real posterior a fecha estimada.
**Decir:** Cada fila final corresponde a un pedido. La variable objetivo vale uno cuando la fecha real supera la estimada y cero cuando llega ese día o antes. Solo se puede calcular para pedidos efectivamente entregados.

## Diapositiva 5: Preparación | Persona 2 | 45 s
**Mostrar:** Ítems agregados antes del cruce. Órdenes entregadas y fechas válidas. Imputación en entrenamiento.
**Decir:** Antes de unir tablas, resumimos los artículos por pedido para no multiplicar registros. Luego revisamos fechas, faltantes y órdenes excluidas. Las transformaciones se ajustan con los datos de entrenamiento.

## Diapositiva 6: Predictores sin fuga | Persona 2 | 45 s
**Mostrar:** Estado de cliente y vendedor, precio, flete, peso, número de ítems, día de compra y plazo prometido.
**Decir:** El modelo usa características conocidas al comprar: estados, número de artículos, precio, flete, peso y plazo prometido. Quitamos despacho, entrega real y reseñas porque ocurren después y causarían fuga de información.

## Diapositiva 7: Modelo 1: árbol | Persona 2 | 45 s
**Mostrar:** Corte temporal 80/20. Profundidad 5, hoja mínima 200, clases balanceadas.
**Decir:** El primer modelo es un árbol de decisión. Entrena con el ochenta por ciento más antiguo y se prueba con el veinte por ciento posterior. Su tamaño se limita para que las reglas no dependan de unos pocos casos.

## Diapositiva 8: Validación | Persona 2 | 50 s
**Mostrar:** Precisión, sensibilidad, F1, PR-AUC y matriz de confusión. Comparación con “siempre a tiempo”.
**Decir:** No basta con la exactitud si los retrasos son poco frecuentes. Por eso revisamos precisión y sensibilidad de la clase tardía, F1, PR-AUC y la matriz de confusión. También comparamos contra predecir siempre puntualidad.

## Diapositiva 9: Modelo 2: K-Means | Persona 3 | 45 s
**Mostrar:** Segmenta por cantidad, precio, flete, peso y plazo. k elegido por silueta.
**Decir:** El segundo modelo, K-Means, agrupa pedidos por cantidad, precio, flete, peso y plazo. Elegimos el número de grupos usando silueta. La tasa de retraso se compara después, sin usarla para crear los grupos.

## Diapositiva 10: Resultados | Persona 3 | 50 s
**Mostrar:** La diapositiva 10 y la matriz de confusión en Colab.
**Decir:** Analizamos más de noventa y seis mil órdenes elegibles. En prueba, el árbol detectó 339 de los 1.021 retrasos, pero generó 3.332 falsas alarmas. K-Means separó un grupo de pedidos típicamente livianos y otro de pedidos más pesados, con mayor flete y una tasa de retraso de aproximadamente nueve por ciento.

## Diapositiva 11: Límites y ética | Persona 3 | 40 s
**Mostrar:** Solo entregas observadas. Posible cambio temporal. Revisar errores por región y evitar usos discriminatorios.
**Decir:** Hay límites importantes: analizamos entregas observadas y datos históricos brasileños. Las diferencias entre regiones pueden reflejar condiciones logísticas; no deben usarse para perjudicar a clientes o vendedores.

## Diapositiva 12: Conclusión y siguiente paso | Persona 3 | 40 s
**Mostrar:** La recomendación final y el notebook de Colab.
**Decir:** Con tantas falsas alarmas, no recomendamos automatizar alertas con este árbol. Los segmentos sí pueden orientar una revisión de pedidos pesados y de mayor flete. Si se prueba otro modelo, conviene medir primero cuánto cuesta revisar cada alerta y qué retrasos se pueden evitar. Gracias.
