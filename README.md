# jrnl
# Ag LC. 
# location: 

Jrnl: cifrado AES

/home/XXX/.local/share/jrnl/journal.txt


pip install jrnl

o si lo preferimos tener cifrado desde el principio con AES-256 ejecutaríamos:
1
	
pip install jrnl [encrypted]

En mi caso me dió error en la instalación en openSUSE (un tema de permisos), así que lo volví a intentar esta vez como root, ejecutando:
1
	
sudo !!

Y de paso hago offtopic, y aprovecho para explicar este comando que junto con «..» es el favorito de los linuxeros que somos algo vaguetes 😉

El comando !! lo que hace es repetir la sentencia anterior, y en este caso concreto, lo que hago es añadirle sudo para que me pida la contraseña y ejecutarlo como administrador, es decir es lo mismo que poner:
1
	
sudo pip install jrnl

Una vez instalado jrnl, ya sea por lo civil o lo criminal, podemos empezar con las anotaciones, la sintaxis básica es esta
1
	
jrnl "texto"

le damos a intro y ya tenemos guardada esa entrada

Pero si lo queremos es tener un diario curioso con sus fechas y anotaciones, lo mejor es utilizar las timestamp o marcas de tiempo inteligentes, tenemos de los siguientes tipos:

    at 11am
    yesterday
    last monday
    sunday at noon
    5 april 2014
    30 apr
    6/24/2014 at 23:42

Y la sintaxis del comando sería esta:
1
	
jrnl [timestamp]: [texto]

aquí algunos ejemplos similares a los que podéis ver en la imágen de cabecera:
1
	
jrnl yesterday: noche de San Juan y lloviendo a mares...
1
	
jrnl 6/24/2014 14:05: ya queda menos para @openSUSE 13.2 con el sistema de archivos @Btrfs

Os habréis fijado que he incluido el signo de la arroba, en un par de palabras, eso lo que hace es marcar unas etiquetas, en este caso openSUSE y Btfrs, lo que en un futuro nos permitirá filtrar los resultados, por ej:
1
	
jrnl @openSUSE @Btrfs @linux

jrnl-5

Ahora para ver las últimas entradas (he elegido 4) de nuestro diario podemos hacer:
1
	
jrnl -4

jrnl-2

Algo que podemos combinar con las diferentes etiquetas que hayamos creado, para hacer la búsqueda todavía más facil
1
	
jrnl -10 @linux

Si queremos listar todas las entradas del diario, el comando a usar será:
1
	
jrnl --short

jrnl-3

En caso de que queramos acotarlas en el tiempo, podemos ver las entradas desde una fecha determinadas
1
	
jrnl -from 6/01/2014

o bien las anteriores a dicha fecha
1
	
jrnl -until 6/01/2014

También podemos marcar una anotación o evento como importante, para ello tiramos de asterisco, y la señalamos como favorita:
1
	
jrnl cita *: darle el toque a Kate Upton, para ir a tomar algo

Al principio del post os comenté la posibilidad de instalar jrnl con cifrado AES para proteger nuestros datos…en caso de que no lo hayáis hecho y el FBI esté llamando a vuestra puerta, lo podéis implementar en cualquier momento ejecutando (es preciso tener instalado el paquete PyCrypto):
1
	
jrnl --encrypt

y para descifrarlo:
1
	
jrnl --decrypt

jrnl-4

Como veis nos da la opción de guardar la clave en nuestro anillo de llaves, para no tener que andar cifrando y descifrando cada vez que lancemos el programa.

Jrnl permite muchas más opciones, entre ellas editar entradas, o exportar la agenda en diferentes formatos como markdown, texto, json; todas ellas las podéis consultar en la web del proyecto.
