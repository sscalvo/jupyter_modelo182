## Generador del Modelo 182 a partir de CSV

El Modelo 182 de la AE (Agencia Tributaria) es una _declaración informativa en la que se relacionan los donativos, donaciones y aportaciones recibidas que den derecho a deducción por el Impuesto sobre la Renta de las Personas Físicas, por el Impuesto sobre Sociedades o por el Impuesto sobre la Renta de no Residentes._

En este repositorio *jupyter_modelo182* contiene un Cuaderno Jupyter (Jupyter Notebook) con el que poder transformar un CSV (con datos de donantes, cantidades, etc) en su  correspondiente **Modelo 182**, tal y como está definido en el documento de la Agencia Tributaria [DR182_2016.pdf](https://www.agenciatributaria.es/static_files/Sede/Disenyo_registro/DR_100_199/archivos/DR182_2016.pdf)

### Como ejecutarlo

Si no te preocupa la privacidad de tus datos, puedes abrir y ejecutar este *Jupyter notebook* en Google Colab (un entorno de ejecución online). Para ello, haz click en este enlace: [jupyter_modelo182 en colab](https://colab.research.google.com/github/sscalvo/jupyter_modelo182/blob/master/modelo182.ipynb). Deberás subir tu fichero CSV y en el código, actualizar el nuevo nombre del fichero subido:

```markdown
#LOAD CSV:
df = pd.read_csv(r".\modelo182\Reporte_279_1579686916.csv") 

```

Si los datos de tu CSV son sensibles, necesitarás instalarte un kernel IPython (capaz de ejecutar el código Python de tu cuaderno Jupyter) en tu máquina local. La opción mas sencilla es usar [Anaconda](https://docs.anaconda.com/anaconda/install/).


### Estructura del CSV

Los nombres de las columnas son: 

- **National Id"** El documento de identificación. Cualquier dato que no pase la validación de DNI o NIE será exportado como 9 caracteres en blanco
- **Family Name** Apellidos. Serán exportados en MAYUSCULAS
- **Given Name** Nombre. Será exportado en MAYUSCULAS
- **Tax State** Ciudad. Serán exportados de acuerdo a la tabla de la pág.12 del documento [DR182_2016.pdf](https://www.agenciatributaria.es/static_files/Sede/Disenyo_registro/DR_100_199/archivos/DR182_2016.pdf)
- **Donation Amount** Cantidad donada. 
- **Currency** Moneda usada en la donación

### Cálculo de la recurrencia de las donaciones

Para poder calcular el campo **RECURRENCIA DONATIVOS** (pág. 19 [DR182_2016.pdf](https://www.agenciatributaria.es/static_files/Sede/Disenyo_registro/DR_100_199/archivos/DR182_2016.pdf) ) se deberán aportar los ficheros entregados a la Agencia Tributaria en el ejercicio del año anterior, y el de hace 2 años.

