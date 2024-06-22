Lo consideraría sistema distribuido.

La sincronziación entre sistemas distribuidos conlleva un reto mayor que los sistemas paralelos. En particular, en este caso se tiene una memoria compartida rapida equiparable a la local, pero no tenemos una sincronización del clock. Que es el principal problema en la sincronización de asignación exclusiva de recursos en sistemas distribuidos.
Los sistemas paralelos como todos los procesos viven en la misma computadora, se tiene el mismo clock y los mecanismos de exclusión mutua son más faciles de coordinar entre los procesos.

Por lo tanto aunque se tenga una memoria distribuida que sea indistinguible a la memoria local, si no tengo un mecanismo de sincronización de procesos semejante a los sistemas paralelos, entonces dicho sistema lo considero distribuido.

