# **Laboratorio 2.  Marget Martínez y Daniela Amador**

## Análisis de resultados
| Combinación de bandas | Descripción |
| ------------------ | -------------- |
| imagen 1 | 1 |
| imagen 2 | 2 |
| imagen 3 | 3 |
| imagen 4 | 4 |
| imagen 5 | 5 |

## Preguntas
### 1. ¿Cuáles son las ventajas de las características multiespectrales de los datos de teledetección digital?

R/

### 2. ¿Qué fecha tiene la imagen que corresponde a la que menor nubosidad?

R/ 01-04 de abril del 2018

### 3. ¿Qué combinaciones espectrales de bandas y colores considera útil para comprender las características del paisaje de su interés?

R/ Características de interés pueden ser uso del suelo (deforestación), cuerpos de agua (son solo opciones)

### 4. Compartir en este documento el link con el código que realizó.
(no sé si hay que compartir el código directamente o el link, porque no sé si con el link la profe tenga acceso)

//Cargar imagen de landsat8

var image = ee.Image((landsat8collection)

//Filtrar para obtener imágenes de la región de interés

  .filterBounds(cuenca)
  
  //Filtrar para obtener el periodo de análisis de interés
  
  .filterDate("2018-04-01" , "2018-04-04")
  
  //Seleccionar solo las bandas del espectro óptico
  
  .select(["B[1-7]"])
  
  //Organizar las escenas de menor a mayor nubosidad, ascendente
  
  .sort("CLOUD_COVER")
  
  //Despliegue la primer imagen con menor nubosidad, primer imagen
  
  .first());
  
  
var bands = ["B7", "B3", "B1"]  

  Map.addLayer(image,{},"L8 Image");
  
  Map.addLayer(cuenca,{color:"2bbc69"},"Damas");
  
  Map.addLayer(image.select(bands).clip(cuenca));
