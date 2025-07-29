# Seguimiento1_Bioinfor


los archivos tipo GFF3 también conocidos como Generic Feature Format Version3
son ficheros de texto separados por tabuación en nueve columnas, cada una aportando información importante sobre caracterísiticas genómicas, si algún campo se desconocoe su lugar se reemplaza por un "." se distinguen 9 tipos de columnas:


1. *seqid:* Es un ID usado para establecer el sitema de coordenadas para la secuencia de referencia, básicamente es usada para identificar la secuencia de referencia sobre la cual está anotada una característica genómica, ya sea un cromosoma completo o un plásmido, un ejemplo es el *"ctg123"* de esta entrada
   
  **ctg123** . gene            1000  9000  .  +  .  ID=gene00001;Name=EDEN

2. *source:* es un calificativo en texto que describe la herramienta o fuente de la que se obtuvo la entrada, por ejemplo, puede ser *"Genescan"* o el nombre de una base de datos como *"Genbank"*; esto se ve reflejado en esta entrada en la cual, según se evidencia, se desconoce la herramienta o base de datos de la que vino la información puesto que tiene un "." en la columna

   
  ctg123 **.** TF_binding_site 1000  1012  .  +  .  ID=tfbs00001;Parent=gene00001


3. *type:*  tipo de característica según la Sequence Ontology (SO), por ejemplo si estamos hablando de un gen, ARN mensajero, exon o CDS

   
  ctg123 . **gene**            1000  9000  .  +  .  ID=gene00001;Name=EDEN
 
4 y 5. *Start y End:* *Start* corresponde a la posición del primer nucleotido donde comienza la estructura en cuestión respecto al *seqid*, basicamente es la posición de inicio de la información de interés en el genoma, el *End* es la posición del ultimo nucleotido de la información de interés incluyendo este último nucleótido, de forma más sencilla:


Posición:  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20


Letra:     A  T  G  C  G  A  A  A  T  G  G  T  A  C  A  A  T  G  C  G


Supongase que el gen empieza en la posición 5 y termina en la 12, eso quiere decir que abarca estos nucleótidos:

G  A  A  A  T  G  G  T  (desde la 5 hasta la 12)

Visto desde un archivo GFF, serían los campos resaltados:

ctg123 . exon            **3000  3902**  .  +  .  lID=exon00003;Parent=mRNA00001,mRNA00003

6. *Score:* Valor numérico asociado a la calidad de la anotación, básicamente mide que tan buena o fuerte es la anotación, usualmente es un P-valor o un E-valor, de no disponerse de estas opsciones, nuevamente se marca al casilla con un ".".

Por ejemplo:

ctg123 . TF_binding_site 1000  1012  **.**  +  .  ID=tfbs00001;Parent=gene00001

 7. *Strand:* indica en qué dirección está hecha la lectura, porque el AFN tiene dos "carriles". puede tomar tres valores +, - o .

    
    + significa "hacia adelante" (5’→3’)
   
      
    - significa “hacia atrás” (3’→5’)
   
      
    . significa "no aplica" (p. ej., para regiones que no tienen hebra)

    

Un ejemplo:

  ctg123 . mRNA            1300 9000  .  **+ ** .  ID=mRNA00003;Parent=gene00001

8. *phase:* solo se usa para CDS (parte que codifica proteína). Este ayuda a determina donde arranca la lecutra de los codones
   
Valores:

0: la codificación comienza justo en la posición start.

1: falta 1 base para completar el primer codón; hay que saltarse 1.

2: faltan 2 bases para el codón completo; hay que saltarse 2.

Ejemplo: 
ctg123 . CDS             7000 7600  .  +  **0**  ID=cds00001;Parent=mRNA00001
  
9. *atributes:* este es un campo de texto que guarda etiquetas y valores separados por ; en el que cada par etiqueta=valor aporta información extra sobre la amnotación. Este permite identifi ar y enlazar elemntos, darles nombre, atribuirles un orden jerarquico y añadir notas y referencias a bases de datos

   Ejemplo:

   chr1 . exon 1200 1500 . + . **ID=exon0001;Parent=mRNA0001;Name=Exón1**
   
Aquí el exón lleva su propio ID, sabe que su “padre” es el mRNA con ID=mRNA0001, y se le ha dado el nombre de Exón1.

*Otras etiquetas:*

Dbxref = enlace a una base de datos externa (por ej. UniProt).

Alias = nombres alternativos.

Ontology_term = referencia a un término de ontología (por ej. GO:0005634).

El propósito de esta columna es concentrar la información que no figura para las otras 8 columnas.

***3. i) ¿Cuantos features contiene el archivo?***


   1521820

***3. ii)  ¿Cuantas regiones de la secuencia (cromosomas) contiene el archivo?***

   127

***3. iii) ¿Cuántos genes están listados en el organismo?***

21411

***3. iv) ¿Cuál es el top 10 de tipo de features (columna 3) más anotados en el genoma?***


 684302 exon

 
 645647 CDS

 
  52215 mRNA

  
  43238 biological_region

  
  37603 five_prime_UTR

  
  30757 three_prime_UTR

  
  21411 gene

  
   2179 ncRNA_gene

   
   1690 lnc_RNA

   
    
   816 pseudogenic_transcript
    
   

   

