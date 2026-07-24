1. Nombre del Space

Nombre: Whisper

Enlace: https://huggingface.co/spaces/openai/whisper


2. ¿Qué hace el agente?

El agente toma como entrada un archivo de audio, en el cual luego de analizarlo por medio de sus actuadores internos, es capaz de traducirlo a formato texto, es decir, es un traductor de audio a texto.


3. Análisis PEAS

Performance El agente hace bien su trabajo cuando es capaz de darle al usuario un texto con alta precisión, siendo la precisión en este caso el error entre las palabras dichas en forma oral, y las palabras dadas por el agente, buscando minimizar siempre la diferencia entre lo dicho, y lo escrito. 

Environment El agente está hecho en hugging face, corriendo este en la web y siendo opensource, pudiendo analizar todo su codigo y su environment en general.

Actuators Tras hacer el proceso interno, el agente actua dando al usuario un archivo en texto, la cual es la traducción del formato audio que se le dio.

Sensors Recibe como entrada un archivo en formato audio.


4. Clasificación del entorno

Propiedad Clasificación Justificación

Observable Parcial Esto debido a que el unico sensor que posee es la entrada de audio, no conoce el contexto de la conversación, quien habla, cuando fue grabado, donde fue grabado, solo se limita al audio dado por el usuario.

Determinista Sí En mismas condiciones del agente, y el mismo audio dado, genera la misma transcipción, no posee estocasticidad dentro de el.

Episódico Sí Puesto que el agente puede procesar cada audio de manera independiente, cada transcripción no depende de la anterior, no necesita recordar, por lo tanto es episodica, no es secuencial.

Estático Sí Ya que el audio ya se le introdujo, y mientras lo analiza el audio no cambia, es completamente el mismo, si fuera transcripción en tiempo real seria dinamico, pero el audio ya está ahí y el modelo no cambia mientras lo analiza.

Discreto No Hablamos de un audio, el cual está compuesto por ondas y frecuencias, siendo estas continuas, y matematicamente la voz tiene infinitas variaciones por esto, pero se podria decir que al momento de que la maquina lo analice digitalmente, todo está dado en 0s y 1s, pero el problema en si es continuo.

Conocido Sí El agente ya sabe que acciones puede realizar (transcribir y como interpretar), no está explorando ni aprendiendo en medio de la ejecución.


5. ¿Qué tipo de programa de agente creen que es?

Diria que agente basado en modelo, puesto que no responde unicamente a palabra por palabra, sino que analiza las frases enteras para tener una mayor capacidad de analisis, así pudiendo analizar mas palabras y pudiendo dar la transcripción correcta al no ver palabra por palabra sino el todo, el contexto de la frase. El modelo también diria que fue entrenado en su fase de entrenamiento, pero durante ya su uso no continua aprendiendo ni se modifica mediante el uso, entonces diria que se descartaria completamente el agente de aprendizaje, que seria el que uno podria llegar a pensar que podria ser.


Discusión en clase

¿Dos Spaces diferentes pueden compartir el mismo tipo de entorno?
Si nos referimos a la clasificación del entorno y que posean toda las mismas caracteristicas, diria que si, puesto que dos modelos pueden ser observables, deterministas, episodicos, estaticos, discretos y conocidos, pero con objetivos, sensores, actuadores diferentes, siendo esto lo que el agente aportará al usuario lo diferente, mas sin embargo el entorno si podria ser el mismo.

¿Es posible saber con certeza qué tipo de agente implementa un Space únicamente observándolo?
Es dificil afirmar que si, puesto que se tendria que testear y ver la funcionalidad interna de este, por ejemplo, cosas como la estocasticidad del modelo se podrian reconocer al ver como está implementado, puesto que si se testea muchas veces con ciertos test-cases especificos o no se usan edge-cases para ponerlo al limite, podriamos pasar por alto este tipo de cosas.

¿Qué diferencia existe entre el comportamiento observable de un agente y su implementación interna?
Diria que la diferencia varia como mencioné en la anterior pregunta en cosas como la estocasticidad, pudiendo estas ayudar a que el modelo sea mas versatil para diferentes situaciones, mas sin embargo si esto el usuario no lo conoce al no haber visto su implementación, puede pasar desapercibido en el modelo, por ejemplo, si se ven algoritmos como el descenso de gradiente estocastico, y se ve simplemente funcionando con ciertos ejemplos en optimización, se puede llegar a confundir con otros algoritmos de descenso de gradiente, puesto que su funcionalidad para ciertos test-cases, hace que la observabilidad haga "invisible" estos aspectos de la implementación interna.