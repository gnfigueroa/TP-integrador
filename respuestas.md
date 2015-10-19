
**Análisis Léxico**

**-Investigue sobre *digraphs* y *trigraphs*.**
Los digrafos y trigrafos son secuencias de dos y tres caracteres respectivamente, que aparecen en el código fuente. 
Según la especificación del lenguaje, este es remplazado por un único caracter. Se crearon por el hecho de que algunos teclados no tenian todos 
los caracteres necesarios para cubrir algunos lenguajes, o tambien porque algunos editores tenian caracteres reservados para uso especial, etc.


**-Responda: ¿Cuando se reemplazan  los *trigraphs*? ¿Y los *digraphs*?.**

Los **trigraphs** son reemplazados por el pre-procesador mientras que los **digraphs** son procesados durante el tokenizado.


**-Escriba la secuencia de lexemas a partir de la secuencia de caracteres.**

**Lex 1:** int 
**Lex 2:** _ 
**Lex 3:** [ 
**Lex 4:** :> 
**Lex 5:** = 
**Lex 6:** <% 
**Lex 7:** - 
**Lex 8:** ! 
**Lex 9:** .0 
**Lex 10:** , 
**Lex 11:** } 
**Lex 12:** ;

**- "Tokenize" (i.e. escriba la secuencia de tokens) a partir de la secuencia de lexemas.**

Resultado al utilizar las respectivas equivalencias:

int a[]={-1,}; 
printf("%d%d",sizeof a - sizeof a[0],sizeof(char)+0[a]); 


**-Indique si la UT es lexicamente correcta.**


Efectivamente es correcta, en primer lugar se declara el prototipo de la funcion printf indicando que no tiene un numero fijo de parametros 
de entrada. Luego se desarrolla la funcion main, en la cual se declara una variable array de enteros. 
Una vez que se reemplazan los digrafos podemos ver que los corchetes y llaves son correctos.


**Análisis Sintáctico**

**-Arme el arbol de derivacion, a partir de la secuencia de tokens. Lea sobre BNF y busque el BNF de unidad de traduccion en A.13.** 
**  Las reglas destacadas, inicializador y expresion.**

unidad-de-traduccion:

unidad-de-traduccion declaracion-externa
declaracion-externa definicion-de-funcion
declaracion	definicion-de-funcion 
especificadores-de-declaracion lista-de-declaradores-init; definicion-de-funcion
especificador-de-tipo declarador-init; definicion-de-funcion
int declarador;
int declarador-directo;



 

**-Indique si la UT es sintacticamente correcta.**

Es correcta, ya que es una Unidad de Traduccion + la Declaracion Externa.


**Análisis Semántico**

**-Indique si la UT es lexicamente correcta. ¿Viola alguna restriccion semantica?**

No viola ninguna restriccion semántica ya que declara un arreglo de enteros y define por extensión sus elementos (en este caso el -1 que corresponde a
un int). 
Invoca la funcion printf, utiliza dos expresiones distintas en sus parámetros pero que ambas coinciden con el uso 
de la función sizeof, aunque se usan para diferentes cosas. 
En la primera expresion se utiliza para saber el tamaño del array y en la segunda expresión para saber el tamaño del tipo char. 
Ambos usos están aceptados en la definición  de la función sizeof así que es semánticamente correcto.

**-Si es semanticamente correcto,indique que hace el programa, reponda dos partes:**
** declaraciones,expresiones y sentencias. Temas destacados:arrays,sizeof,incializacion y conversiones automaticas.**

El programa declara el prototipo de la funcion printf, en donde dice que recibe x cantidad de parametros de entrada.
Dentro del main declara e inicializa un array de enteros, en el cual su unico elemento es el -1. 
Se ejecuta la funcion printf, la cual imprime dos enteros decimales. 
En sus argumentos:
El primer argumento es el formato de salida de la consola, que seran dos enteros sin decimales.
En el proximo argumento se hace el sizeof del elemento en la posicion 0 del array,lo cual devuelve 1.
Despues le resta al array el valor obtenido en la anterior expresion, con lo cual se resta una Posicion de memoria al array. 
El resultado es 0. 
El siguiente argumento tiene una expresion suma que por un lado realiza el sizeof del tipo de datos CHAR colocando los parentesis obligatorios 
para este caso. 
En la 2da expresion, se obtiene el elemento que esta en la posicion 0 del arreglo.
Por lo tanto la suma final es 1 + (-1) que da 0.

**Si es semanticamente correcto,indique la salida.justifique.**

El resultado de la salida es 00. 
El primer cero es el resultado de hacer el sizeof de un array vacio (0 elementos). Mientras que el segundo cero es el resultado de la suma 
entre el tamaño del tipo CHAR (igual a 1) con el elemento en la primera posicion del array(igual a -1).

