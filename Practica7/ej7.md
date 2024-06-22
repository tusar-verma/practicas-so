### 1

Como todos los nodos estan conectados entre sí, el nodo inicial efectivamente obtiene el máx ID entre los nodos en la red y puede anunciar al nuevo lider.

### 2

Este algoritmo se asemeja al algoritmo bully visto en clase. La diferencia es que este es solo una iteración del mismo. Es decir, el nodo inicial pregunta a los nodos con ID mayores si estan vivos, y este proceso no se replica para dichos nodos (como pasa en bully). La información que recibe el nodo inicial es la que usa para ver cual es el nodo con mayor ID vivo. Como todos los nodos estan conectados entre sí, efectivamente lo va a conseguir (asumiendo que no hay fallas por perdida de mensajes).

[Paper con comparativas](https://citeseerx.ist.psu.edu/document?repid=rep1&type=pdf&doi=2af4ac7a14293766ed4a4fb97a0d6d573c27d934)