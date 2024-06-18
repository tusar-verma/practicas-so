a- Un drivers es un módulo de software que se puede acoplar al SO para controlar la comunicación con dispositivos de E/S
b- No, es un software.
c- Algunos drivers ya vienen compilados en el SO y se cargan cuando arranca el sistema. Otros se instalan con módulos.
d- No. Los drivers corren a nivel kernel de privilegio porque tienen que tener acceso al hardware. Un programa de usuario no tiene (ni debe) este nivel de privilegios
e- No, pero se puede agregar la funcionalidad de interrupciones para que el hardware le notifique al driver de algún evento. Es decir, algunos drivers pueden soportar insterrupciones como comunicación con los dispositivos.
f- El driver como se encarga de controlar la comunicación con un dispositivo, conoce detalles muy especificos del mismo. Con respecto al sistema operativo, el driver conoce al menos la API que el SO le provee para que aplicaciones puedan comunicarse con él.
g- Hay drivers genericos y especificos. Es decir, podemos tener drivers que son especificos para un dispositivo particular y entonces conoce las particularidades del modelo en específico, y hay drivers genéricos que varios dispositivos pueden usar. Por ejemplo, podríamos tener un driver generico que implemente las funciones de un teclado y usarlo para distintos modelos de teclado. Cada hardware tendría que seguir un estandar para comunicarse con ese driver genérico.

