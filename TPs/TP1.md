# TCVP 2024 - TP N° 1 #

_Maquinas de Turing. Jerarquía de la Computabilidad._

1. **Ejercicio 1**:
    1. Un problema computacional de decisión es un problema que simplifica el estudio de la
    computabilidad y la complejidad computacional. Mediante los problemas de decisión logramos
    trabajar directamente con lenguajes, estos al ser conjuntos de strings hace todo mas sencillo. Los problemas de decisión siempre tendran como salida un "si" o "no".\
    Los de decisión y los de búsqueda son los mas generales.

    2.  Ʃ = {a, b, c} y L = {$a^n$ $b^n$ $c^n$ | n ≥ 0} 

        Ʃ* ⋂ L = {$a^n$ $b^n$ $c^n$ | n ≥ 0} \
        Ʃ* ⋃ L = {Ʃ*} \
        $L^C$ =  {Ʃ* - L}

    3.  MT Calculadora: Esta simplemente deberá recibir una entrada para cumplir con su función
        calculadora, lo demas lo rechazara, los números estaran representados en una notación
        adecuada para la MT, la salida sera el resultado.

        MT Aceptadora: En este caso dependera de la fórmula booleana que reciba en la entrada,
        depende si la satisface o no se obtendra una respuesta positiva o negativa.

        MT Generadora: En si la MT generadora no acepta ninguna entrada, solamente genera una 
        salida. No tiene niguna formula booleana asociada.

    4. La tesis de Church-Turing formula que "todo algoritmo es equivalente a una máquina de
        Turing". O sea que todo problema que pueda ser expresado en un algortimo puede ser
        resuelto por una máquina de Turing. \
        Se asume como cierta, pero aun asi no puede ser probada ya que no se poseen los medios
        para desmentirla, por eso es una tesis.

    5.  Dos MT son equivalentes cuando aceptan el mismo lenguaje.

        Dos Modelos de MT son equivalentes si dada una MT son equivalentes si dada una
        MT de un modelo existe una MT equivalente del otro.

    6.  -Un lenguaje L es **R** (Recursivos) sii existe una MT M<sub>L</sub> que lo **acepte y 
        pare siempre**.

        -Un lengauje L es **RE** (Recursivo Enumerable) sii existe una MT M<sub>L</sub> que lo
        **acepta**. Depende de la entrada:
        - Si w ∈ L, entonces M<sub>L</sub> para en q<sub>A</sub>.
        - Si w ∉ L, entonces M<sub>L</sub> para en q<sub>R</sub> o loopeara. 

        -Un lenguaje L es **NO recursivamente numerable** (Indecidible) cuando no existe 
        una MT que se detenga y conduzca a **q<sub>A</sub>** o a **q<sub>R</sub>**. \
        Un ejemplo conocido es Halting Problem para el cual no existe un algoritmo que determine si el programa se detendrá, una vez sea ejecutado...

    7. A partir de la jerarquía de la computabilidad se puede demostrar que  R ⊆ RE ⊆ L* \
        - *𝔏* son los lenguajes para los cuales no existen una MT que, al recibir una entrada, siempre se detenga y acepte la cadena.
        - *RE* son los lenguajes para los cuales existe una MT que eventualmente se detiene y acepta o no la cadena.
        - *R* son los lengaujes para los cuales existe una MT que siempre se detiene y decide si acepta o no la cadena.

        - La jerarquia aqui comienza con los lenguajes para los cuales existe una MT que siempre se detiene, luego nos encontramos con los lenguajes para los cuales tambien existe una MT pero no siempre se detendra segun la entrada y finalizamos con lenguajes para los cuales no existe una MT.
    
    8. Los lenguajes pertenecientes a la clase **CO-RE** no poseen una MT que los acepte, ya que es imposible definir un algoritmo para aceptar esa clase de lenguaje. Para que sea posible aceptar **CO-RE**, la maquina al parar debe entrar en estado de rechazo y al loopear debe entrar en estado de aceptación, pero es muy complicado/imposible realizar esa transición ya que la maquina estara loopeando. 
    Es simplemente aplicarle tambien el complemento a la MT que lo debe aceptar.

    9. Para ambos es necesario justificar con una MT que acepte ese lenguaje. 

    10. Un lenguaje finito es recursivo porque es posible decidir si la entrada pertenece o no al lenguaje que acepta la MT.

    11. L<sub>1</sub> ∈ CO-RE y L<sub>2</sub> ∈ CO-RE. Entonces (L<sub>1</sub> ⋂ L<sub>2</sub>) ∈ CO-RE. \
    Si usamos la Ley de Morgan tenemos que:  (L<sub>1</sub> ⋂ L<sub>2</sub>)C = L<sub>1</sub>^C ⋃ L<sub>2</sub>^C = RE.\
    L<sub>1</sub>^C = RE \
    L<sub>2</sub>^C = RE 
    


2. **Ejercicio 2**: Construir una MT, con cualquier cantidad de cintas, que acepte de la manera más 
eficiente posible el lenguaje L = {$a^n$ $b^n$ $c^n$ | n≥0}. Comentario: Plantear primero la idea general. 
    - La MT debera tener un lenguaje que contenga a, b y c. Ʃ = {a,b,c}
    MT M = (Q, Ʃ, δ, q<sub>0</sub>, q<sub>A</sub>, q<sub>R</sub>)\
    La maquina va a primero verificar con su estado inicial sí es cadena vacia, si la cadena posee **a**, **b** o **c** como primer simbolo en la cinta. Segun el simbolo el estado inicial cambiara a uno de los 4 estados posibles: q<sub>1</sub>(Si comienza con a), q<sub>2</sub>(Si comienza con b), q<sub>3</sub>(Si comienza con c) o q<sub>A</sub>(Si es λ). Cabe recalcar que del estado q<sub>1</sub> se puede ir al q<sub>2</sub> o q<sub>3</sub> o q<sub>A</sub>, para el q<sub>2</sub> puede ir al q<sub>3</sub> o al q<sub>A</sub> y q<sub>3</sub> a q<sub>A</sub>. No olvidemos que las demas transciones terminaran en q<sub>R</sub>
    

3. **Ejercicio 3**: Explicar (informal pero claramente) cómo simular una MT por otra que en un paso no pueda simultáneamente modificar un símbolo y moverse
    - Para simular ese tipo de maquina de MT, se debera separar la escritura del desplazamiento, primero se debera realizar la escritura y una vez se escribe se realizara el movimiento del cabezal en la cinta sin ninguna modificación en la cinta, el desplazmiento y la modificación seran segun el algoritmo a resolver. 

4. **Ejercicio 4**. Probar: 
    1. La clase R es cerrada con respecto a la operación de unión. Ayuda: la prueba es similar a la desarrollada para la intersección. 
    - Segun el Lema 2(Teoria N°2) Si L<sub>1</sub> ∈ R y L<sub>2</sub> ∈ R, entonces L<sub>1</sub> ⋂ L<sub>2</sub> ∈ R. \
    Entonces Si L<sub>1</sub> ∈ R y L<sub>2</sub> ∈ R, entonces L<sub>1</sub> U L<sub>2</sub> ∈ R.
    2. La  clase  RE es cerrada con respecto  a  la operación  de  intersección.  Ayuda: la  prueba es similar a la desarrollada para la clase R.
    - Nuevamente si es necesario la demostración mediante la clase R, es posible expresar que si L<sub>1</sub> ∈ R y L<sub>2</sub> ∈ R, entonces L<sub>1</sub> ⋂ L<sub>2</sub> ∈ R. \
    Entonces Si L<sub>1</sub> ∈ RE y L<sub>2</sub> ∈ RE, entonces L<sub>1</sub> ⋂ L<sub>2</sub> ∈ RE. No hay que olvidar que R ⊆ RE. 

5. **Ejercicio 5**.  Sean  L1  y  L2  dos  lenguajes  recursivamente  numerables  de  números  naturales codificados en unario (por ejemplo, el número 5 se representa con 11111). Probar que también es recursivamente numerable el lenguaje L = {x | x es un número natural codificado en unario, y existen y, z, tales que y + z = x, con y ∈ L1, z ∈ L2}.  
Ayuda: la prueba es similar a la vista en clase, de la propiedad de clausura de la clase RE con respecto a la operación de concatenación.

    -A partir del Lema 3 de las propiedades de la clase RE, Si L<sub>1</sub> ∈ RE y L<sub>2</sub> ∈ RE, entonces L<sub>1</sub> U L<sub>2</sub> ∈ RE, en este caso L es un lenguaje que expresa sun número natural codificado en binario compuesto por la suma de ***y*** y ***z***, respectivamente ***y*** ∈ L<sub>1</sub> y ***z*** ∈ L<sub>2</sub>. L en este caso es el producto de la únion entre L<sub>1</sub> y L<sub>2</sub>.

6. **Ejercicio 6**. Dada una MT M1 con alfabeto Ʃ = {0, 1}: 
    1. Construir una MT M2 que determine si L(M1) tiene al menos una cadena.
    
        - Sera necesario que M2 posea un contador auxiliar **i** el cual iniciara en 1. 
        - M2 debera ejecutar **i** pasos de M sobre todas las cadenas de a lo sumo **i**.
        - Si M acepta en algun caso, M2 acepta. 
        - Si no es el caso, el contador **i** se incrementara y se volvera a ejecutar los **i** pasos.

    2. ¿Se  puede  construir  además  una  MT  M3  para  determinar  si  L(M1)  tiene  a  lo  sumo  una cadena? Justificar.
        - Sera casi similar al comportamiento de M2 solo que M3 tendra un contador en el cual contara el número de veces que M1 se detiene aceptando una cadena.