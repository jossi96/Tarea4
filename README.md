# Tarea4
Orquídeas y Áreas Silvestres Protegidas de Costa Rica

# Preparativos

## Carga de los paquetes

library(sf)
library(leaflet)
library(leaflet.extras)
library(leafem)
library(dplyr)
library(raster)
library(rmapshaper)
library(spData)

## Carga de los datos

### Carga de la capa de cantones
cantones <-
  st_read(
    "https://raw.githubusercontent.com/gf0604-procesamientodatosgeograficos/2021i-datos/main/ign/delimitacion-territorial-administrativa/cr_cantones_simp_wgs84.geojson",
    quiet = TRUE
  )
  
### Carga de la capa de provincias
provincias <-
  st_read(
    "https://raw.githubusercontent.com/gf0604-procesamientodatosgeograficos/2021i-datos/main/ign/delimitacion-territorial-administrativa/cr_provincias_simp_wgs84.geojson",
    quiet = TRUE
  )
  
### Carga de la capa de Áreas Silvestres Protegidas
asp <-
  st_read(
    "https://raw.githubusercontent.com/gf0604-procesamientodatosgeograficos/2021i-datos/main/sinac/asp/asp-wgs84.geojson",
    quiet = TRUE
  ) 
  
### Carga de los datos de orquídeas
orquideas <-
  st_read(
    "https://raw.githubusercontent.com/gf0604-procesamientodatosgeograficos/2021i-datos/main/gbif/orchidaceae-cr-registros.csv",
    options = c(
      "X_POSSIBLE_NAMES=decimalLongitude",
      "Y_POSSIBLE_NAMES=decimalLatitude"
    ),
    quiet = TRUE
  )

### Asignación del Sistema de coordenadas
st_crs(orquideas) = 4326
  
