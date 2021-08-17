# movilidad-bogota


### Configuración de entorno de desarrollo
Para poder ejecutar el código es necesario instalar Python (>=3.6) y las siguientes dependencias:
* `geopandas`
* `notebook`
* `numpy`
* `pandas`

La manera más sencilla de realizar esta instalación es a través de Conda. Para esto descargue [Miniconda][1] o [Anaconda][2]. [Acá][3] puede encontrar más información sobre la diferencia entre estas y una guía detallada sobre su intalación.

Una vez tenga instalado Conda en su equipo, vaya a la raíz de este proyecto en una terminal y ejecute el siguiente comando para crear un entorno con las dependencias necesarias:

```
conda env create -f environment.yml
```

Una vez creado el entorno `movilidad-bogota`, actívelo ejecutando:

```
conda activate movilidad-bogota
```

Para abrir Jupyter Notebook utilizando el intérprete de Python recién instalado ejecute:

```
jupyter notebook
```

### Descarga de datos
Los links de descarga de los datos originales utilizados en este proyecto se encuentran en la sección **Fuentes de datos**. Sin embargo, una carpeta con todos los datos (de los cuales algunos han sido reestructurados para disminuir espacio de almacenamiento y cumplir con los fines del proyecto) está disponible [acá][4] para su descarga de forma manual. También es posible descargar esta carpeta desde una terminal ejecutando el siguiente comando (desde la raíz del proyecto):

```
curl -L -o ./data.zip "https://drive.google.com/uc?export=download&id=1He-R_menD5nHA-IQXx7jrhIIi-biFhA9"
```

Asegurese que una vez descargados los datos, la estructura de las carpetas del proyecto sea la siguiente:

```
.
├── data
│   └── csv
│       └── ...
│   └── shp
│       └── ...
└── notebooks
    └── ...
```

### Fuentes de datos
* csv
    - CNPV2018_5PER_A2_11.csv<sup>1</sup>
    - CNPV2018_MGN_A2_11.csv<sup>1</sup>
    - ViajesEODH_2019<sup>2</sup>
* shp
    - CICLOPARQUEADEROS<sup></sup>
    - MANZANA<sup>4,5</sup>
    - MGN_URB_MANZANA<sup>6</sup>
    - PARQUEADEROS<sup>7</sup>
    - ZAT<sup>2</sup>

<sup>1</sup> [DANE - Censo Nacional de Población y Vivienda 2018][5]. El link de descarga se encuenta dentro de la pestaña *Obtener Microdatos* en la fila *11Bogota*. 

<sup>2</sup> [Prudencia Bogotá - Encuestas de movilidad][6]. Los datos corresponden a la Encuesta de movilidad 2019.

<sup>3</sup> [Catastro Bogotá - Cicloparqueadero][7]

<sup>4</sup> [Ideca - Manzana Estratificación Bogotá D.C.][8]. Los datos fueron exportados accediendo al servicio desde QGIS.

<sup>5</sup> [Ideca - Usos por manzana Bogotá D.C.][9]

<sup>6</sup> [Geoportal DANE - Descarga del Marco Geoestadistico Nacional (MGN)][10]. El archivo corresponde a *Nivel Geográfico Manzana Censal*, ubicado en la pestaña *Año 2018*.

<sup>7</sup> OpenStreetMap. Para descargar los parqueaderos se utilizó la interfaz de [Overpass Turbo][11] con la siguiente consulta:

```
[out:json][timeout:25];
{{geocodeArea:Bogotá}}->.searchArea;
(
  node["amenity"="parking"](area.searchArea);
);
out body;
```




[1]: https://docs.conda.io/en/latest/miniconda.html
[2]: https://www.anaconda.com/products/individual
[3]: https://docs.conda.io/projects/conda/en/latest/user-guide/install/download.html
[4]: https://drive.google.com/open?id=1QLCakladzBUmSZAg6qA5UQ9u8e0pjRiz
[5]: http://microdatos.dane.gov.co/index.php/catalog/643/get_microdata
[6]: https://www.simur.gov.co/portal-simur/datos-del-sector/encuestas-de-movilidad/
[7]: http://serviciosgis.catastrobogota.gov.co/arcgis/rest/services/movilidad/cicloparqueadero/MapServer
[8]: https://www.ideca.gov.co/recursos/mapas/manzana-estratificacion-bogota-dc
[9]: https://www.ideca.gov.co/recursos/mapas/usos-por-manzana-bogota-dc
[10]: https://geoportal.dane.gov.co/servicios/descarga-y-metadatos/descarga-mgn-marco-geoestadistico-nacional/
[11]: https://overpass-turbo.eu/
