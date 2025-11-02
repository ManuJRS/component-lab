01/11/2025
Cree una coleccion de botones para practicar, vue te permite crear componentes que luego puedes reutilizar en otras partes pero te deja cambiar los estilos de manera individual.

uso un callback a la funcion reservada computed para acceder a los valores y en el return se arman las clases que aparecen luego en el navegador

Errores: 

#al parecer el btn base en el event litsener del click debe tener un nombre diferente al del event litsener del btn que vas a usar porque si no se activa dos veces el mismo evento (sumaba de 2 en 2).

#creo que el callback de computed puede usar funcion flecha
