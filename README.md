# Mi Carrito TECSUP

**Autor:** Luis Cucho

## Descripción
Aplicación de carrito de compras desarrollada en Jetpack Compose que integra 
modelado de datos con Kotlin, un formulario de entrada, y una lista dinámica 
con LazyColumn. Permite agregar productos, eliminarlos y calcula 
automáticamente subtotal, IGV (18%) y total.

## Capturas

### Carrito vacío
<img width="251" height="553" alt="Captura de pantalla 2026-09-16 a las 5 24 53 p  m" src="https://github.com/user-attachments/assets/a8f7f6b0-a922-4704-a31c-dbabeb09a297" />


### Carrito con productos

<img width="245" height="543" alt="Captura de pantalla 2026-09-16 a las 5 24 44 p  m" src="https://github.com/user-attachments/assets/fee6783b-a494-4ba7-b6e5-2ca6d75e56e0" />

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
