Podemos utilizar FloodMin (FloodMax pero en cada iteración se guarda y envia el mínimo ID que le llegó a un nodo)

Si tenenmos una malla de n x m, el camino más largo es de una esquina a otra: n+m. Y la cantidad de aristas es de $O(nm)$
Complejidad $O((n+m)*nm)$