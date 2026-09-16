# Mi Carrito TECSUP

**Autor:** Luis Cucho

## Descripción
Aplicación de carrito de compras desarrollada en Jetpack Compose que integra 
modelado de datos con Kotlin, un formulario de entrada, y una lista dinámica 
con LazyColumn. Permite agregar productos, eliminarlos y calcula 
automáticamente subtotal, IGV (18%) y total.

## Capturas

### Carrito vacío
<img width="246" height="536" alt="Captura de pantalla 2026-09-16 a las 4 53 55 p  m" src="https://github.com/user-attachments/assets/51f3389b-6b1b-4fa7-8ae9-4f65af6742fb" />


### Carrito con productos

<img width="245" height="539" alt="Captura de pantalla 2026-09-16 a las 4 56 34 p  m" src="https://github.com/user-attachments/assets/52748e99-26ed-40e1-90ff-fdbc7faa0511" />

## Respuestas conceptuales

**¿Por qué se usa `mutableStateListOf` y no una `MutableList` normal?**

A diferencia de una MutableList normal, mutableStateListOf crea una lista que 
Compose puede observar (o rastrear). Por eso cuando hago .add() o .remove(), 
la pantalla se recompone (o actualiza) sola. Con una MutableList normal, aunque 
también pueda cambiar, Compose no se entera (o no detecta el cambio) y la 
pantalla no se actualiza.

**¿Por qué la lista se declara con `val` y aún así podemos agregarle elementos?**

val no impide modificar el contenido de la lista, solo impide reasignar la variable. 
Es decir, no puedo hacer productos = otraLista, pero sí puedo hacer productos.add(...) 
porque estoy modificando el objeto, no la referencia

**¿Qué hace `weight(1f)` en la LazyColumn?**

weight(1f) hace que la LazyColumn ocupe todo el espacio disponible. Esto es necesario 
porque abajo tengo el panel de resumen (o total), que necesita quedarse fijo sin que la 
lista lo empuje o lo tape
