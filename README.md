# Categorizar Elementos A Partir De Una Propiedad.
Los estilos de un mapa son una parte fundamental, sobre todo si se trata de un mapa temático, debido a que cada uno representará información particular manifestada a través de un color, textura o símbolo. Cuando queremos representar una capa vectorial en particular, a partir de la cual se usarán diferentes estilos basados en una o más propiedades, hablaremos de categorías. Es decir, cada categoría tendrá un estilo diferente según una propiedad.
## En el ambiente de Leaflet, y más específicamente con los formatos GeoJson y Json, es muy sencillo reconocer cuales son las propiedades a partir de las cuales podemos trabajar, ya que son heredadas de la tabla de atributos que existía o construiste cuando se le dio tratamiento a la capa vectorial en un SIG.
### A continuación, veremos una comparación.
![screenshot](https://raw.githubusercontent.com/sampach95/CategorizarElementosAPartirDeUnaPropiedad./master/img/Imagen1.png )
## Por el momento, solamente echemos un vistazo a las columnas y como las puedes encontrar en el código.
Si te das cuenta las clases del código siguen el mismo orden que las columnas en la tabla de atributos, la sintaxis es muy sencilla:
- “CLASE o PROPIEDAD”: “VALOR DE LA PROPIEDAD”,
- “CLASE o PROPIEDAD 2”: “VALOR DE LA PROPIEDAD”, ….
- “CLASE o PROPIEDAD N”: “VALOR DE LA PROPIEDAD”
## Ya que te has familiarizado con los nombres de las clases y sus valores, podemos generar estilos a partir de los valores de una propiedad, en este caso escogimos la Clave cuyos valores son los siguientes:
- Qhoal
- Qhoco
- TplQptB
- plQptCgp-Ar
- TeGd-D
- TeoCgp
- TmplA-B
- TplA-Da
- TplR-TR
- TplTR-TDa
- ToR-TR
- KapceCz-Bro
- KiCz-Lu
- KsLu-Cz
- JtKvLu-Cz


Como recomendación, es muy útil buscar y escribir todos los valores que existan de la propiedad, de esta manera llevarás un control, y notar cuando alguna te haga falta mientras vas trabajando en el mapa. 

## ¿Recuerdas esta sección del código?, aquí es donde haremos los cambios para representar cada categoría
``` html
<script>
<!-- ----- CAPAS VECTORIALES------	 -->
	var geology = L.geoJson(geology).addTo(map);
	
	var contact = L.geoJson(contact,{
		style: contact_style
		}).addTo (map);
  
  
</script>
```



## Dentro del paréntesis de (geology), se alojará toda la información de los estilos para esta capa. Escribimos una coma, para comenxar a declararlos, abrimos un cochete para poder agrupar la sección de estilos y pulsamos un enter para separar la información de la capa de la de los estilos.

``` html
<script>
<!-- ----- CAPAS VECTORIALES------	 -->
	var geology = L.geoJson(geology, {
  
  
</script>
```

## Escribimos la palabra style, esto le indica al programa que vamos a modificar solamente características referentes a color, opacidad, etc. Seguido de dos puntos escribimos function y entre paréntesis (feature), esto indica que vamos a utilizar las propiedades de la capa para definir el estilo, abrimos un corchete y pulsamos enter.

``` html
<script>
<!-- ----- CAPAS VECTORIALES------	 -->
	var geology = L.geoJson(geology, {
  style:function(feature){
  
</script>
```
## Escribimos la palabra switch, esto indica que iremos cambiando de propiedad o de valor, según lo que indiquemos entre paréntesis, para nuestro caso particular escribimos los tres niveles, feature.properties, al último se escribe el nombre de la categoría que vamos a estar variando según el caso. Para este ejemplo usamos CLAVE.

``` html
<script>
<!-- ----- CAPAS VECTORIALES------	 -->
	var geology = L.geoJson(geology, {
  style:function(feature){
    switch (feature.properties.CLAVE){
  
</script>
```

## Finalmente, para cada categoría usaremos la sintaxis de la siguiente línea, 
``` html
<script>
case 'Qhoal': return {color:'#fff5dd',fillOpacity: .5};
</script>
```
## Se cierran todos los corchetes abiertos y nos aseguraamos qe esté el comando .addTo(map);

``` html
<script>
<!-- ----- CAPAS VECTORIALES------	 -->
	var geology = L.geoJson(geology, {
  style:function(feature){
    switch (feature.properties.CLAVE){
				case 'Qhoal': return {color:'#fff5dd',fillOpacity: .5};
			}}
			}).addTo(map);
</script>
```
## Si ejecutamos en el navegador, este seria el resultado.
![screenshot](https://raw.githubusercontent.com/sampach95/CategorizarElementosAPartirDeUnaPropiedad./master/img/Imagen2.png )

## Lo siguiente sería encontrar los colores adecuados para el mapa y terminar de declarar los casos, para cada valor de la propiedad clave.  pero eso será en la siguiente parte. 

Siguiente Tutorial https://github.com/IngGeolAsist/EstilosParaCadaCategoria

Haz click en el siguiente enlace para volver a la pagina inicial https://github.com/IngGeolAsist/ComoCrearMapasEnLaWebConLeaflet


