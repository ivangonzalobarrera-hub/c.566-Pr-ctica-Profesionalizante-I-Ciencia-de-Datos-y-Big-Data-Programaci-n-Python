# Brecha digital en los hogares

Práctica Profesionalizante I
Barrera Ivan Gonzalo
ivangonzalobarrera@gmail.com

Soy estudiante de primer año de la Tecnicatura Superior en Ciencia de Datos e Inteligencia Artificial. Este repositorio es el trabajo de la práctica: un diagnóstico de acceso a computadora y a internet fija, con la base de 1000 hogares que pasó la cátedra.

La base usa nombres de variables de la EPH. No es el operativo completo del INDEC, así que los porcentajes son de esta muestra.

## Qué hay

- `data/eph_tecnologia_microdatos.csv`: base original.
- `data/df_clean.csv`: la misma base después de la limpieza.
- `notebooks/analisis_brecha_digital.ipynb`: carga, limpieza, descriptivas, cruces, gráficos y una regresión lineal simple.
- `figuras/`: los gráficos que guarda el notebook.
- `informe/Informe_Barrera_Ivan.docx`: informe técnico.
- `presentacion/Pitch_brecha_digital.pptx`: pitch de 7 diapositivas.

## Cómo correrlo

Hace falta Python con pandas, numpy y matplotlib. En Google Colab ya están.

1. Abrir `notebooks/analisis_brecha_digital.ipynb`.
2. Si lo corro desde esa carpeta, el notebook busca el csv en `../data`.
3. Si lo subo a Colab, subo también `eph_tecnologia_microdatos.csv`. Si queda suelto al lado del notebook, igual lo encuentra.
4. Ejecutar todas las celdas en orden. La de región usa una función que se define en la celda de los cruces.

La base original se puede volver a armar con el script de la cátedra. Tiene `np.random.seed(42)`, así que da el mismo archivo.

## Diccionario corto

- `CODUSU`: código del hogar. No hay nombre ni dirección.
- `REGION`: 1 GBA, 40 NOA, 41 NEA, 42 Cuyo, 43 Pampeana, 44 Patagonia.
- `IX_TOT`: cantidad de integrantes.
- `NIVEL_ED`: nivel educativo del jefe de hogar. 1 primaria incompleta, 2 primaria completa, 3 secundaria incompleta, 4 secundaria completa, 5 superior o universitaria completa. El 9 es sin respuesta y lo pasé a nulo.
- `ITF`: ingreso total familiar.
- `DECIFR`: decil de ese ingreso, de 1 a 10. Si falta el ingreso, también falta el decil.
- `IV12_3`: tiene computadora. 1 sí, 2 no. En la guía figuraba II8 como ejemplo. En esta base la PC está en IV12_3.
- `II7`: tiene internet fija. 1 sí, 2 no.
- `ipcf`: lo calculé yo. Es ITF dividido por IX_TOT.
- `tiene_pc` y `tiene_internet`: 1 y 0, para poder sacar porcentajes. El 9 y los nulos quedan afuera.

El 9 no lo reemplacé en todo el archivo. En el decil, 9 es un decil real, y hay un hogar con 9 integrantes.

## Qué encontré

De los que contestaron, 63,9% tiene PC y 73,5% tiene internet fija.

La brecha fuerte es por educación y por decil de ingreso. En primaria incompleta, 29,9% tiene PC. En superior completa, 91,5%. En el decil 1, 40,7%. En el decil 10, 91,3%.

Entre regiones la diferencia es chica, alrededor de 6 puntos en PC. En esta base NOA y NEA no quedan abajo de GBA.

El detalle, los gráficos y las recomendaciones están en el informe.
