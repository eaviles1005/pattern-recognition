### 1. Arquitectura y funcionamiento de LSTM

La arquitectura LSTM (Long Short-Term Memory) es un tipo especial de red neuronal recurrente (RNN) diseñada para abordar el problema de la desaparición del gradiente, que es común en las RNN tradicionales [[1](https://www.notion.so/Challenge-08-6c0a384179b649eeb53f984c955a2866?pvs=21)]. Esto supone una dificultad para que las RNN aprendan dependencias a largo plazo en los datos. Para comprender el concepto de LSTM, es necesario entender qué son las redes neuronales recurrentes y cómo funcionan.

La RNN se basa en el seguimiento secuencial de la información. Por lo tanto, su salida se calcula en función de los cálculos previos. También se pueden considerar como una memoria que recopila y almacena información sobre los cálculos realizados hasta el momento. La RNN puede retroceder algunos pasos para utilizar información previa en los hallazgos actuales [2].

La red LSTM, introducida por Hochreiter y Schmidhuber en 1997 y posteriormente refinada y popularizada, es capaz de aprender dependencias a largo plazo. Esta red está diseñada específicamente para superar el problema de las dependencias a largo plazo. Su capacidad para recordar información durante períodos prolongados es parte de su comportamiento por defecto. Debido a su eficacia en una amplia gama de problemas, la LSTM es ampliamente utilizada [3].

La red LSTM es especialmente útil para el aprendizaje profundo de las máquinas. En ella, se encuentra una conexión de retroalimentación que les permite procesar tanto datos individuales como secuencias completas, como videos. Si bien puede ser usado en diversos campos, su uso más común se da en el desarrollo de procesos de aprendizaje en problemas complejos [4].

Si bien la red LSTM es una forma de RNN, difiere de otras redes en su estructura. Mientras que otras redes repiten el mismo módulo cada vez que reciben nueva información de entrada, la LSTM conserva la información durante períodos más largos y tiene una estructura similar a una cadena para repetir el módulo. Estas redes interactúan de manera especial y constan de cuatro capas de red neuronal [4].

**Arquitectura**

Los componentes principales de una red neuronal de LSTM son una capa de entrada de secuencias y una capa de LSTM. Una capa de entrada de secuencias introduce datos secuenciales o de series de tiempo en la red neuronal. Una capa de LSTM aprende las dependencias a largo plazo entre las unidades de tiempo de los datos secuenciales.

https://lh5.googleusercontent.com/NZuCNOswDdlb0qyw-1kmfblIvjXK_4JQWgxaL50TOmaZuZlEUQUPZL8-SauOg8AaIOY6cu38vULSTfe4YCUxcw6kAuy11x0ROGlPf9RwPnfPQr3aMxcgLdZUPFqpLh0QqNn-k0enhgQusJt_Ze5g0w4

La arquitectura de una LSTM se compone de unidades de memoria llamadas "celdas de memoria" (memory cells) que interactúan entre sí. Cada celda de memoria tiene tres componentes principales: una entrada, una salida y una puerta de olvido (forget gate) [5].

La entrada en una celda de memoria se activa por medio de una función de activación y recibe dos tipos de entradas: la entrada actual y la salida de la celda de memoria anterior en la secuencia. Esto permite a la red LSTM considerar la información previa mientras procesa nuevos datos [5].

La puerta de olvido (forget gate) determina qué información se debe descartar de la celda de memoria. Es un vector de números entre 0 y 1 que se calcula utilizando una función de activación sigmoide. Un valor cercano a 0 indica que la información se olvidará, mientras que un valor cercano a 1 indica que la información se mantendrá [6].

La salida de una celda de memoria también se calcula utilizando una función de activación sigmoide y se filtra mediante otra función de activación, generalmente una tangente hiperbólica (tanh). Esto permite que la red LSTM genere una salida dentro de un rango específico [5].

Además de las celdas de memoria, las redes LSTM también contienen puertas llamadas "puertas de entrada" (input gates) y "puertas de salida" (output gates). Estas puertas controlan el flujo de información hacia y desde las celdas de memoria. Se calculan utilizando funciones de activación sigmoide y permiten a la red LSTM controlar el acceso y la salida de información [6].

El cell state es esencialmente la "memoria" de la celda de memoria en una LSTM. Representa la información que la red LSTM ha acumulado y almacenado de las entradas anteriores. A medida que los datos secuenciales se procesan a través de la red, el cell state se actualiza y se modifica mediante operaciones lineales y no lineales. Las puertas de olvido, entrada y salida de la LSTM controlan cómo se actualiza y se conserva el cell state [4].

El hidden state, por otro lado, es la salida de una celda de memoria específica en un momento dado. Contiene información que se considera relevante y útil para el siguiente paso en la secuencia. El hidden state se calcula a partir del cell state y se filtra mediante la puerta de salida de la celda de memoria. Luego, el hidden state se pasa a la siguiente celda de memoria en la secuencia o se utiliza como salida final de la red LSTM [4].

El uso de LSTM para la generación de moléculas en formato SMILES puede ser muy beneficioso debido a varias razones:

1. **Secuencialidad**: SMILES (Simplified Molecular Input Line Entry System) es una notación que representa moléculas y reacciones químicas en forma de cadenas de caracteres. Al ser una representación en forma de secuencia, las redes neuronales recurrentes, como LSTM, son naturalmente adecuadas para manejar este tipo de datos [7].
2. **Complejidad y Variabilidad**: La generación de moléculas puede ser un proceso complejo y variable. Las LSTM tienen la capacidad de modelar diferentes patrones y estructuras en los datos, lo que es beneficioso para generar una variedad de moléculas [7].
3. **Memoria**: Las LSTM tienen celdas de memoria que pueden almacenar información a lo largo de la secuencia. Esto es útil en la notación SMILES, donde ciertos caracteres pueden afectar la interpretación de caracteres posteriores (por ejemplo, la apertura y cierre de anillos en la estructura de la molécula) [7].

Con el objetivo específico de encontrar moléculas que sirvan como inhibidores de la proteasa principal del SARS-CoV-2, el uso de LSTM también es relevante por los siguientes aspectos:

1. **Aprendizaje de Transferencia**: Es posible utilizar aprendizaje de transferencia con LSTM, lo que significa que se puede comenzar con un modelo preentrenado en un conjunto de datos más grande y luego afinarlo en un conjunto de datos más específico de inhibidores de la proteasa principal del COVID-19. Esto puede mejorar la eficacia de la generación al aprovechar el conocimiento adquirido de datos relacionados.
2. **Aceleración de la Investigación**: El proceso de descubrimiento de fármacos es generalmente largo y costoso. Utilizando LSTM para la generación dirigida de moléculas, se puede acelerar significativamente la fase de identificación de candidatos potenciales, lo que es especialmente crítico en el contexto de una pandemia.
3. **Exploración de Espacio Químico**: Las LSTM pueden ayudar a explorar un espacio químico más amplio y generar estructuras novedosas que podrían no ser identificadas mediante enfoques de descubrimiento de fármacos más tradicionales. Esto es valioso en el contexto de una enfermedad emergente como el COVID-19, donde hay una necesidad de identificar rápidamente nuevos compuestos efectivos.

Las otras metodologías que podrían ser abordadas en vez de la arquitectura LSTM, son las siguientes:

1. **Redes Neuronales Convolucionales (CNN):** Las CNN utilizan la convolución para procesar datos con una topología de cuadrícula. Las CNN pueden capturar características espaciales y temporales en los datos, lo que las hace especialmente útiles para tareas tales como la detección de objetos y el reconocimiento facial, sin importar la ubicación de la información en el espacio [8].
2. **Redes Neuronales Recurrentes (RNN):** Las RNN son bastante útiles para el procesamiento de secuencias de datos, como series temporales o cadenas de texto. Las RNN poseen conexiones de retroalimentación que permiten el procesamiento de secuencias de cualquier longitud. Desafortunadamente, las RNN tienen ciertas dificultades para el manejo de dependencias a largo plazo en los datos debido al desvanecimiento del gradiente [9].
3. **Unidades Recurrentes Cerradas (GRU):** Las GRU son una variante de las RNN que modifican la estructura de la red para poder así facilitar el manejo de las dependencias a largo plazo. Las GRU también tienen una estructura más simple que las LSTM, ya que combinan las puertas de entrada y olvido en una única puerta de actualización [9].
4. **Transformers:** Son una arquitectura de red neuronal que utiliza mecanismos de atención para así obtener una mayor eficiencia del procesamiento de secuencias de datos. Los transformers han demostrado ser bastante efectivos en tareas relacionadas al procesamiento del lenguaje natural, como la traducción automática y la generación de texto [10].
5. **Autoencoders:** Los autoencoders son redes neuronales que se utilizan para la compresión y descompresión de datos. Estos están compuestos por dos partes: un codificador que comprime los datos de entrada en una representación de menor dimensionalidad, y un decodificador que reconstruye los datos a partir de esta representación comprimida [10].
6. **Redes Neuronales de Retroalimentación (FNN):** Estas redes permiten que las señales fluyan en ambas direcciones mediante el uso de bucles de retroalimentación. Esto les permite mantener una “memoria” de las entradas anteriores, lo que puede ser útil para tareas que requieren tener en consideración el contexto o la historia de los datos [9].
