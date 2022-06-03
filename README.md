# Proyecto-IA Clasificación binaria - pacientes con riesgo de enfermedad cardiaca - PCA e IPCA
Desarrollo del método de clasificación PCA e IPCA a un dataset de pacientes con riesgo de enfermedad cardiaca

Fredy Alexander Garcia Cardozo

# Introducción
Al trabajar en inteligencia artificial (IA), analizando buenas cantidades de datos, es normal encontrar problemas donde hay una gran cantidad de features con relaciones complejas entre ellas y con la variable que se busca predecir, por esta razón es útil encontrar los métodos adecuados para analizar estos datos. Un método muy útil para tratar este tipo de situaciones es PCA, el cual es un algoritmo complejo que busca reducir la complejidad del problema, esto lo hace seleccionando solamente las variables relevantes que combina en nuevas variables que mantienen la información mas importante. Puede ser múy útil cuando el dataset tiene gran cantidad de features y no se está seguro de que todos pueden ser útiles para predecir la variable, también cuando existe una alta correlación entre los features, si tenemos Overfitting con el fin de reducir la complejidad del modelo extrayendo la información importante o cuando realizar el manejo de los datos nos representa un alto coste computacional.

Para implementar éste método, se trabajó con un dataset de pacientes con riesgo de una enfermedad cardiaca, el cual contiene un subconjunto de 14 atributos (etiquetas)
  1. age: Edad en años del paciente
  2. sex: 1 - Hombre, 2 - Mujer
  3. cp: Tipo de valor en el pecho entre 4 posibles valores. ( 1 - Angina típica, 2 - Angina atípica, 3 - Dolor no-anginoso, 4 - Dolor asintomático)
  4. trestbps: Presión sanguínea en reposo
  5. chol: Medición del colesterol
  6. fbs: Azúcar en la sangre en ayunas
  7. restcg: Resultados electrocardiográficos en reposo
  8. thalach: Frecuencia cardiaca máxima alcanzada
  9. exang: ¿Se presentó angina de pecho después de hacer ejercicio?
  10. oldpeak: Depresión ST inducida por ejercicio respecto al reposo
  11. slope: Pendiente del pico del segmento ST
  12. ca: Número de vasos sanguíneos mayores coloreados por la fluoroscopia
  13. thal: Talasemia: 1 - Normal, 2 - Defecto fijo, 3 - Defecto reversible
  14. target: Presencia de patología cardiaca 1 o 0.

y 1025 muestras, datos con los cuales se busca una relación entre diferentes variables medidas sobre el estado de salud en pacientes con la presencia o ausencia de una patología cardiaca para identificar los factores mas incidentes en la aparición de estas.

La idea es utilizar ciertas variables de los pacientes para hacer una clasificación binaria entre si el paciente tiene o no una enfermedad cardiaca,de esta manera utilizar una clasificación básica para obtener la información relevante.

# Desarrollo
Lo principal para poder analizar cualquier tipo de datos es prepararlos y organizarlos, por lo tanto los datos del dataset se normalizaron y también se dividió una cantidad para prueba y otra para entrenamiento. Los métodos que se implementaron para resolver este problema fueron PCA e IPCA y se realizó una prueba para comprobar el rendimiento de los dos clasificadores mediante una regresión logística. Por último se realizó Cross-Validation usando K-folds con 5 splits

Se adquirieron y cargaron los datos a un dataframe de pandas
Luego se partieron los datos entre los features y el target que se va a entrenar
Se normalizaron los datos ya que es necesario para PCA
Partir el conjunto de entrenamiento
Se llamó y se configuró el algoritmo PCA, pasando el número de componentes que se esperaban (opcional)
Se aplicó PCA a los datos de entrenamiento
Se realizó el mismo procedimiento para aplicar IPCA a los datos de entrenamiento, a diferencia de PCA, se tiene un parámetro adicional (tamaño de batch o de bloque), ya que en este caso no se mandan todos los datos a entrenar al mismo tiempo
Se configuró la regresión logística para evaluar la precisión de los métodos aplicados para el conjunto de entrenamiento y prueba .
Se midió la varianza de los componentes que se extrayeron.
Se compararon los resultados obtenidos en el modelo inicial, en el cross validation para observar las similitudes y finalmente se hizo predict sobre el Conjunto de Test para ver si se obtuvo buena precisión.

# Resultados

![image](https://user-images.githubusercontent.com/81457647/171962941-d36aef45-9d08-43ee-a9e0-79b0047a2bdf.png)

En la imagen se observan los valores entre cero y dos que se refieren a las tres componentes en (0 1 y 2), en el eje y se puede observar la importancia de esas componentes, se puede ver que la mayoría de la información la aportan las dos primeras componentes.


![image](https://user-images.githubusercontent.com/81457647/171963109-e2a31658-21d9-4559-841b-9bb87ed4bfbb.png)

En la imagen anterior se puede observar la precisión para PCA e IPCA.

![image](https://user-images.githubusercontent.com/81457647/171967293-e88d872f-dc77-4084-ad05-256925c4306a.png)

Se observan los resultados obtenidos para la validación cruzada.

# Conclusiones

Al observar el resultado de nuestro entrenamiento con PCA e IPCA, donde se observa un puntaje levemente mayor (78% vs 80) para entrenamiento con IPCA, tienen casi el mismo rendimiento.

Por lo tanto se logró pasar de inicialmente 13 features a 3 features artificiales que PCA retorna para poder llegar a un resultado bastante bueno y clasificar entre si tiene o no una enfermedad cardiaca, de esta manera se logra ahorrar costo computacional y utilizar solo información que es realmente importante.
Al comparar los resultados obtenidos en el modelo inicial, en el cross validation se puede ver que son similares, haciendo predict sobre el Conjunto de Test y se observa que también se obtiene buena precisión.

# Link de vídeo

https://youtu.be/si4_fd38U3M 












