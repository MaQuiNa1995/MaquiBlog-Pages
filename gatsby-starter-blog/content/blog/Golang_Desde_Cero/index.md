---
title: Golang Desde Cero
date: "2021-12-05T01:33:00.000Z"
description: Guía desde 0 de golang
---

# Tabla de contenidos:
- [Instalación](#instalaci-n)
  * [Descarga](#descarga)
  * [Instalación](#instalaci-n-1)
  * [Verificación de la instalación](#verificaci-n-de-la-instalaci-n)
- [Configuración del entorno](#configuraci-n-del-entorno)
  * [Variables de entorno](#variables-de-entorno)
    + [Windows](#windows)
    + [Linux](#linux)
    + [Verificación](#verificaci-n)
  * [Entorno de desarrollo](#entorno-de-desarrollo)
    + [Hola mundo en Visual studio](#hola-mundo-en-visual-studio)
- [Zonas básicas En un archivo Go](#zonas-b-sicas-en-un-archivo-go)
  * [Paquete](#paquete)
  * [Import](#import)
  * [Función Principal](#funci-n-principal)
- [Variables](#variables)
  * [Scope de variables y convención de nombres](#scope-de-variables-y-convenci-n-de-nombres)
  * [Tipos de datos básicos](#tipos-de-datos-b-sicos)
    + [Enteros](#enteros)
      - [Signed int (Enteros)](#signed-int--enteros-)
      - [Unsigned int (Enteros)](#unsigned-int--enteros-)
    + [Decimales](#decimales)
    + [Números complejos](#n-meros-complejos)
    + [Byte](#byte)
    + [Rune](#rune)
    + [UTF-8](#utf-8)
    + [String](#string)
    + [Booleanos](#booleanos)
      - [Operadores lógicos](#operadores-l-gicos)
  * [Inicializaciones](#inicializaciones)
    + [Inicialización Completa](#inicializaci-n-completa)
    + [Inicialización Tardía](#inicializaci-n-tard-a)
    + [Inicialización Abreviada (Type Inference)](#inicializaci-n-abreviada--type-inference-)
    + [Inicialización múltiple](#inicializaci-n-m-ltiple)
  * [Colecciones](#colecciones)
    + [Arrays](#arrays)
      - [Instanciación](#instanciaci-n)
        * [Forma Completa](#forma-completa)
        * [Forma Elegante](#forma-elegante)
        * [Declaración Tardía](#declaraci-n-tard-a)
      - [Punteros en Arrays](#punteros-en-arrays)
      - [Punteros en Arrays](#punteros-en-arrays-1)
    + [Slices](#slices)
      - [Instanciación](#instanciaci-n-1)
        * [Forma completa](#forma-completa)
        * [Copia de un slice](#copia-de-un-slice)
        * [Copia de un Slice con cortes](#copia-de-un-slice-con-cortes)
        * [Uso de make para la instanciación de slices](#uso-de-make-para-la-instanciaci-n-de-slices)
      - [Funciones de los Slice](#funciones-de-los-slice)
        * [Adición de 1 elemento (append)](#adici-n-de-1-elemento--append-)
        * [Adición de 2 a N elementos (append)](#adici-n-de-2-a-n-elementos--append-)
        * [Fusión de slices](#fusi-n-de-slices)
      - [Eliminación de elementos](#eliminaci-n-de-elementos)
        * [Shift (Eliminación de elementos por los extremos)](#shift--eliminaci-n-de-elementos-por-los-extremos-)
        * [Eliminación de elementos centrales](#eliminaci-n-de-elementos-centrales)
    + [Mapa](#mapa)
      - [Instanciación](#instanciaci-n-2)
        * [Forma completa](#forma-completa-1)
        * [Uso de make()](#uso-de-make--)
      - [Lectura de mapas](#lectura-de-mapas)
      - [Funciones](#funciones)
      - [Adición de valores](#adici-n-de-valores)
      - [Eliminación de elementos por clave](#eliminaci-n-de-elementos-por-clave)
    + [Struct](#struct)
      - [Declaración](#declaraci-n)
        * [Declaración clásica](#declaraci-n-cl-sica)
        * [Struct anónimo](#struct-an-nimo)
      - [Instanciación](#instanciaci-n-3)
        * [Manera normal](#manera-normal)
        * [Sintaxis de posicionamiento](#sintaxis-de-posicionamiento)
      - [Composición](#composici-n)
      - [Tags](#tags)
      - [Convenciones de nombres](#convenciones-de-nombres)
  * [Constantes](#constantes)
    + [Constantes enumerados](#constantes-enumerados)
      - [Declaración completa simple con iota](#declaraci-n-completa-simple-con-iota)
      - [Declaración simple con iota](#declaraci-n-simple-con-iota)
      - [Declaración simple con literales](#declaraci-n-simple-con-literales)
      - [Multiples declaraciones de bloques con iota](#multiples-declaraciones-de-bloques-con-iota)
      - [Usos del valor 0 con iota](#usos-del-valor-0-con-iota)
      - [Descartes de valores con iota](#descartes-de-valores-con-iota)
    + [Convenciones de nombre](#convenciones-de-nombre)
- [Scope de variables y convención de nombres](#scope-de-variables-y-convenci-n-de-nombres-1)
  * [Nivel de paquete](#nivel-de-paquete)
  * [Nivel de función](#nivel-de-funci-n)
  * [Misma variable distintos scope](#misma-variable-distintos-scope)
- [If](#if)
  * [If básico](#if-b-sico)
  * [If avanzado](#if-avanzado)
    + [Comparadores](#comparadores)
    + [Llamadas a funciones](#llamadas-a-funciones)
- [Switch](#switch)
  * [Switch simple](#switch-simple)
  * [Switch multiple](#switch-multiple)
  * [Switch avanzado](#switch-avanzado)
  * [Switch con condiciones complejas](#switch-con-condiciones-complejas)
  * [Switch con fallthrought](#switch-con-fallthrought)
  * [Switch con interfaces](#switch-con-interfaces)
- [For](#for)
- [ForEach](#foreach)
- [Labels](#labels)
  * [Breaks](#breaks)
- [Defer](#defer)
  * [Usos](#usos)
    + [Problemas](#problemas)
    + [Soluciones](#soluciones)
  * [Llamadas a funciones y parámetros](#llamadas-a-funciones-y-par-metros)
- [Panicking](#panicking)
  * [Provocar panics](#provocar-panics)
- [Recover](#recover)
- [Punteros](#punteros)
  * [Creación](#creaci-n)
  * [Deferenciación](#deferenciaci-n)
- [Funciones](#funciones-1)
  * [Convención de nombres](#convenci-n-de-nombres)
  * [Parámetros](#par-metros)
  * [Punteros en parámetros de funciones](#punteros-en-par-metros-de-funciones)
    + [Vararg](#vararg)
  * [Return](#return)
  * [Funciones anónimas](#funciones-an-nimas)
    + [Simple](#simple)
    + [Problema en entornos asincronos](#problema-en-entornos-asincronos)
  * [Funciones como tipos](#funciones-como-tipos)
  * [Métodos](#m-todos)
- [Interfaces](#interfaces)
  * [Convención de nombres](#convenci-n-de-nombres-1)
  * [Interfaces de interfaces](#interfaces-de-interfaces)

# Instalación

## Descarga
https://golang.org/dl/

## Instalación
Ejecuta el msi descargado en el caso de windows o descomprime donde quieras si lo prefieres antes que un instalador, asegurate de que sea el cliente de 64 bits

## Verificación de la instalación
```
go version -> go version go1.17.1 windows/386
where go -> C:\Users\MaQuiNa1995\Herramientas\Go\bin\go.exe
```
# Configuración del entorno

## Variables de entorno

### Windows
1. GOPATH

Es la ruta donde tendrás tu Go descargado
Valor por defecto: %USERPROFILE%\go

2. PATH

PATH -> otrasEntradas;%GOPATH%

### Linux
1. GOPATH

Es la ruta donde tendrás tu Go descargado
Valor por defecto: $HOME/go

### Verificación 
Al ejecutar el siguiente comando deberías de obtener una respuesta parecida

go version -> `go version go1.17.1 windows/386`

## Entorno de desarrollo

Como IDE usaremos Visual studio code en el que al entrar te dará la opción de descargar e instalar módulos que puedan sernos útiles como autocompletado y demás

[Descárgalo aquí desde la página oficial](https://az764295.vo.msecnd.net/stable/83bd43bc519d15e50c4272c6cf5c1479df196a4d/VSCodeUserSetup-x64-1.60.1.exe)

Cuando lo abrais un pop-up os dará la opción de instalar esos módulos que hablé antes cuando estén todos listos os pondrá en la terminal algo parecido a "you are ready to Go :)"

Si habeis instalado el cliente de 32 bits de golang tendreis problemas con el analizador de código y no podreis usarle

### Hola mundo en Visual studio

Crearemos un proyecto Golang y del sistema de archivos que nos creará iremos a la carpeta src y crearemos una carpeta adicional será en esta donde crearemos nuestro archivo Main.go con el siguiente contenido
```
package main

import (
	"fmt"
)

func main() {
	fmt.Println("Hola mundo")
}
```

Para ejecutar el programa iremos a la vista de la terminal en nuestro visual studio y como este estará ya ubicado en la carpeta de nuestro proyecto
solo tendremos que ejecutar el siguiente comando

go run .\src\carpetaCreadaPreviamente\Main.go

Adicionalmente tambien podeis a una [consola online](https://play.golang.org/) y probar allí el mismo código

Deberíamos de poder ver nuestro hola mundo

# Zonas básicas En un archivo Go
## Paquete
`package main`

## Import
Aqui irían todas las declaraciones de importación sobre librerías de sistema por poner un ejemplo
```
import (
	"fmt"
	"strconv"
)
```
## Función Principal
```
func main() {
    // Aqui iría el código de nuestro punto de entrada al proyecto
}
```
# Variables
En go tenemos diferentes formas de declaración de variables

## Scope de variables y convención de nombres
1. Pascal case -> Export variables (Variables Globales)
1. Camel Case -> internal variables (Variables de paquete)

## Tipos de datos básicos
https://golangbyexample.com/all-data-types-in-golang-with-examples/#Basic_Types

### Enteros

#### Signed int (Enteros)

|Tipo|Tamaño|
|:---:|:---:|
| int | Dependiente De Plataforma |
| int8 | 8 bits/1 byte |
| int16 | 16 bits/2 byte |
| int32 | 32 bits/4 byte |
| int64 | 64 bits/8 byte |

#### Unsigned int (Enteros)

|Tipo|Tamaño|
|:---:|:---:|
| uint | Dependiente De Plataforma |
| uint8 | 8 bits/1 byte |
| uint16 | 16 bits/2 byte |
| uint32 | 32 bits/4 byte |
| uint64 | 64 bits/8 byte |

### Decimales
|Tipo|Tamaño|
|:---:|:---:|
| float32 | 32 bits or 4 bytes |
| float64 | 64 bits or 8 bytes |

### Números complejos
|Tipo|Tamaño|
|:---:|:---:|
| complex64 | Parte real e imaginaria son float32 |
| complex128 | Parte real e imaginaria son float64 |

El tipo complejo por defecto es complex128

### Byte
byte es un alias para uint8 vamos que se considera un valor entero de 8 bits y representa un byte (0-255) este a su vez puede representar un caracter ASCII Golang no tiene un tipo char aluso como por ejemplo Java 

### Rune
rune es un alias para int32 por lo tanto se le considera un entero se usa para representar un **Unicode Code Point**

Unicode es un superconjunto de caracteres ASCII que asigna un número único a cada carácter que existe. Este número único se llama **Unicode Code Point**

Algunos ejemplos:
1. El dígito 0 se representa como punto Unicode U+0030 (valor decimal – 48)
1. La letra pequeña b se representa como punto Unicode U+0062 (valor decimal – 98)
1. Un símbolo de libra £ se representa como Punto Unicode U+00A3 (Valor decimal – 163)

Puedes aprender mas sobre esto en: 
[The Absolute Minimum Every Software Developer Absolutely, Positively Must Know About Unicode and Character Sets](http://www.joelonsoftware.com/articles/Unicode.html)

### UTF-8
utf-8 guarda cada Unicode Code Point utilizando 1, 2, 3 o 4 bytes.

Los puntos ASCII se almacenan utilizando 1 byte. Es por eso que rune es un alias para int32 porque un Unicode Code Point puede ser de un máximo de 4 bytes en Go, ya que cada cadena está codificada usando utf-8 cada rune está destinada a referirse a un Unicode Code Point.

Por ejemplo, si imprime una cadena después de encasillarla en una matriz de runes, imprimirá el Unicode Code Point para cada uno de los caracteres.
Para la siguiente cadena "0b£" la salida será – [U+0030 U+0062 U+00A3]

### String 
En go se puede declarar una String con comillas simples y con comillas dobles

### Booleanos
Pueden tomar o true o false
Por defecto su valor es false

#### Operadores lógicos
1. AND –> &&
2. OR  –> ||
3. Negación –> !

## Inicializaciones
### Inicialización Completa
`var numero int = 1`

### Inicialización Tardía
```
var numero3 int
numero3 = 3
```

### Inicialización Abreviada (Type Inference)
`numero2 := 2`

El único problema de esta forma de declaración es que cuando, por ejemplo tenemos `numero2 := 2.` que representaría un número decimal, es que nos inicializa la variable con **float64** no hay ninguna forma de crear un **float32** por esta vía
	
### Inicialización múltiple
Podemos como en otros lenguajes usar la asignación múltiple con cualquier de las 3 formas anteriores
```
var nombre, github string = "MaQuiNa", "https://github.com/MaQuiNa1995"
numero, numero2 := 1, 2
```

## Colecciones

### Arrays

#### Instanciación

##### Forma Completa
`profesiones := [3]string{"Caballero Cebolla", "Ilusionista", "Francotirador"}`

En esta forma se inicializa de manera completa el array declarando el tamaño y los elementos que lo conforman

##### Forma Elegante
`profesiones2 := [...]string{"Caballero Cebolla", "Ilusionista", "Francotirador"}`

Esta forma es equivalente a la anterior solo que omitiendo el tamaño ya que en este caso resulta dedundante ya que tenemos 3 elementos

Hay casos en los que no deberías de utilizar esta forma ya que tendrías que ir 1 a 1 contando manualmente los elementos entre { } entonces solo eligiría esta manera si es visualmente muy fácil saber cuentos elementos conforman el array 

##### Declaración Tardía 
```
var profesiones3 [3]string
profesiones3[0] = "Caballero Cebolla"
profesiones3[1] = "Ilusionista"
profesiones3[2] = "Francotirador"
```
En esta forma dejamos la declaración de los elementos para "mas tarde"

Como dato adicional
1. Aqui no se pueden usar los [...] que utilizamos en la anterior forma
2. Se pueden dejar posiciones vacías en cuyo caso dependiendo del tipo de objeto cogerían el valor por defecto

#### Punteros en Arrays

```
profesiones := [...]string{"Caballero Cebolla", "Ilusionista", "Francotirador"}
profesionesCopia := profesiones
profesionesCopia[0] = "Mago Azul"
fmt.Printf("Profesiones:       %v\nProfesiones Copia: %v\n", profesiones, profesionesCopia)
```
Resultado:
```
Profesiones:       [Caballero Cebolla Ilusionista Francotirador]
Profesiones Copia: [Mago Azul Ilusionista Francotirador]
```
En Go cada "copia" ya sea por asignación o por el envío de estos a una función genera una nueva copia de estos, en otros lenguajes siempre se apunta a la misma dirección de memoria y si modificas uno el otro tambien se ve afectado, en Go no es asi siempre se crea uno nuevo a no ser que hagas lo siguiente
```
profesiones := [...]string{"Caballero Cebolla", "Ilusionista", "Francotirador"}
profesionesCopia := &profesiones
profesionesCopia[0] = "Domador"
fmt.Printf("Profesiones:       %v\nProfesiones Copia: %v\n", profesiones, profesionesCopia)
```
Resultado:
```
Profesiones:       [Domador Ilusionista Francotirador] 
Profesiones Copia: &[Domador Ilusionista Francotirador]
```
Con el modificador & en la asignación le decimos a go que los dos arrays apunten a la misma dirección de memoria por lo tanto si modificas uno, el otro tambien se ve afectado


#### Punteros en Arrays
Si recuerdas de los arrays si no usábamos el operador `&` no provocabamos que 2 variables apuntasen al mismo hueco de memoria en los slice esto siempre es asi de tal manera que si cambiamos una slice el otro tambien se verá afectado, un ejemplo:
```
profesiones := []string{"Caballero Cebolla", "Ilusionista", "Francotirador"}
profesionesCopia := profesiones
profesionesCopia[0] = "Alquimista"
fmt.Printf("Profesiones:       %v\nProfesiones Copia: %v\n", profesiones, profesionesCopia)
```
Resultado:
```
Profesiones:       [Alquimista Ilusionista Francotirador]
Profesiones Copia: [Alquimista Ilusionista Francotirador]
```

### Slices

Los slice son y tienen la misma funcionalidad que un array con alguna que otra excepción que luego veremos

#### Instanciación

##### Forma completa
```
sliceOriginal := []int{1, 2, 3, 4, 5}
fmt.Printf("Slice Original: %v\n", sliceOriginal)
```
##### Copia de un slice
```
slice2 := sliceOriginal[:]
fmt.Printf("Slice Copia de Slice Original: %v\n", slice2)
```
##### Copia de un Slice con cortes

Una regla que siguen las siguientes formas dependiendo donde esté el número a la derecha o izquierda o en ambos de `:` Inclusivo:Exclusivo

Tambien decir que está nomenclatura tambien se aplica a `Arrays`
```
slice3 := sliceOriginal[3:]  //Se descartan los 3 primeros valores de sliceOriginal
slice4 := sliceOriginal[:4]  // Se cogen solo los 4 primeros elementos de sliceOriginal
slice5 := sliceOriginal[2:4] // Se descartan los 2 primeros elementos y se obtienen los siguientes elementos (despues del primer descarte) hasta la posicion X del slice original

fmt.Printf("Slice Cortado con principio definido: %v\n", slice3)
fmt.Printf("Slice Cortado desde el inicio hasta un final definido: %v\n", slice4)
fmt.Printf("Slice Cortado descartando X elementos y seleccionado Y de los primeros restantes: %v", slice5)
```
##### Uso de make para la instanciación de slices

Podemos usar 2 argumentos
1. tipo -> []int
2. Tamaño -> 4
```
slice := make([]int, 4)
fmt.Println(slice)
fmt.Printf("Tamaño: %v\n", len(slice))
fmt.Printf("Capacidad: %v\n", cap(slice))
```
Resultado:
```
[0 0 0 0]
Tamaño: 4
Capacidad: 4
```
Tambien podemos usar 3 argumentos
1. tipo -> []int
2. Tamaño -> 4
3. Capacidad -> 4
```
slice2 := make([]int, 4, 10)
fmt.Println(slice2)
fmt.Printf("Tamaño: %v\n", len(slice2))
fmt.Printf("Capacidad: %v", cap(slice2))
```
Resultado:
```
[0 0 0 0]   
Tamaño: 4   
Capacidad: 10
```

#### Funciones de los Slice

Podemos añadir y quitar elementos de un slice dinámicamente a diferencia de un array no tiene un tamaño predefinido

##### Adición de 1 elemento (append)
```
slice := []string{}
fmt.Println(slice)
fmt.Printf("Tamaño: %v\n", len(slice))
fmt.Printf("Capacidad: %v\n", cap(slice))

slice = append(slice, "Mago del Tiempo") // Tenemos que igualarlo al slice 
fmt.Println(slice)
fmt.Printf("Tamaño: %v\n", len(slice))
fmt.Printf("Capacidad: %v\n", cap(slice))
```
A tener muy en cuenta: cuando un slice tiene capacidad 2 y tamaño 2 (Osea está lleno) y metemos un nuevo elemento la capacidad del slice se doblará en el caso de que el slice fuese su capacidad de 0 pasará a 2 

Con el siguiente ejemplo se ve muy claro:
```
slice := []string{"Mago del Tiempo", "Monje"}
fmt.Println(slice)
fmt.Printf("Tamaño: %v\n", len(slice))
fmt.Printf("Capacidad: %v\n", cap(slice))

slice = append(slice, "Paladín")
fmt.Println(slice)
fmt.Printf("Tamaño: %v\n", len(slice))
fmt.Printf("Capacidad: %v\n", cap(slice))
```
Resultado:
```
[Mago del Tiempo Monje]
Tamaño: 2
Capacidad: 2
[Mago del Tiempo Monje Paladín]
Tamaño: 3
Capacidad: 4 // la capacidad se ha doblado
```

##### Adición de 2 a N elementos (append)

Se pueden añadir de 2 a mas elementos a un slice añadiendo en el append mas argumentos:
```
slice := []string{"Mago del Tiempo", "Monje"}
slice = append(slice, "Paladín","Soldado","Dragontino")
```

##### Fusión de slices

Podemos fusionar slices ya sea por variable o porque se ha instanciado directamente uno en el propio append
```
slice := []string{"Mago del Tiempo", "Monje"}
slice2 := []string{"Paladín", "Soldado", "Dragontino"}

slice = append(slice, slice2...)                         // Fusión por variable
slice = append(slice, []string{"Domador", "Cazador"}...) // fusión por slice instanciado
```

#### Eliminación de elementos
Se pueden elemininar elementos de un slice de distintas maneras

##### Shift (Eliminación de elementos por los extremos)
Con esta técnica crearíamos un nuevo array omitiendo valores del slice original

Cortar por el principio
```
slice := []string{"Mago del Tiempo", "Monje"}
// Crearíamos un nuevo slice omitiendo el primer elemento de "slice"
slice2 := slice[1:]
```
Cortar por el final
```
slice := []string{"Mago del Tiempo", "Monje"}
// Crearíamos un nuevo slice omitiendo el último elemento del original
slice2 := slice[:len(slice)-1]
```

##### Eliminación de elementos centrales

Aqui las cosas se ponen un poco espinosas teniendo que hacer nuevos slices de las partes del slice original, se ve mejor visualmente con un ejemplo: 
```
slice := []string{"Mago del Tiempo", "Monje", "Paladín", "Elementalista", "Esgrimista"}

// Crearíamos un nuevo slice omitiendo el último elemento del original
// slice[:2] -> crea un array con: Mago del Tiempo Monje
// slice[4:]... -> añade a ese array creado los elementos resultantes de descartar 4 elementos del slice original
slice2 := append(slice[:2], slice[4:]...)

// imprime: [Mago del Tiempo Monje Esgrimista]
// se han eliminado los elementos centrales: Paladín y Elementalista
fmt.Print(slice2)
```
### Mapa

Consiste en un par de valores primero la key y luego el value ambos pueden tener cualquier tipo

A tener en cuenta los mapas apuntan siempre a la misma referencia asique si lo pasamos a una función y manipulamosese mapa fuera de la función ese objeto tambien se verá afectado por los cambios

#### Instanciación

##### Forma completa
```
// map[tipo de la key] tipo del value
profesiones := map[int]string{
	1: "Soldado",
	2: "Paladín",
	3: "Dragontino",
	4: "Lancero",
}
fmt.Println(profesiones)
```

##### Uso de make()
```
profesiones2 := make(map[int]string)
fmt.Println(profesiones2)
```

#### Lectura de mapas

Se suelen hacer por key para obtener el value de tal manera:
```
profesiones := map[int]string{
	675: "Soldado",
	432: "Paladín",
	321: "Dragontino",
	968: "Lancero",
}
// no imprimiría nada ya que no existe ninguna key que valga 3
fmt.Println(profesiones[3]) 
// En cambio esto si que imprimiría Dragontino porque el valor 321 existe de key
fmt.Println(profesiones[321])
```
Tenemos otra forma de leer entradas de un mapa leyendo directamente el par o la key del  mismo
```
profesiones := map[int]string{
	675: "Soldado",
	432: "Paladín",
	321: "Dragontino",
	968: "Lancero",
}
trabajo, ok := profesiones[675]
// 	    	Soldado true
fmt.Println(trabajo, ok)
trabajo2, ok2 := profesiones[999]
//                    false
fmt.Println(trabajo2, ok2)
```
trabajo -> value del mapa
ok -> booleano indicando la existencia en el mapa de esa key (`profesiones[key]`)

En el caso de que solo pongamos uno de los 2 sacaríamos el value de esa key
```
trabajo := profesiones[675]
fmt.Println(trabajo)
```
Tambien podemos descartar el valor y quedarnos con el booleano de si existe o no:
```
_ , ok := profesiones[675]
fmt.Println(ok)
```

A tener en cuenta si sacamos algo que no existe:
key -> el valor por defecto (String = " " y numeros = 0)
value -> false

#### Funciones

como en los arrays aqui tambien tenemos la función len() para ver el tamaño del mapa

#### Adición de valores

Podemos añadir valores como se puede observar aqui:
```
profesiones := map[int]string{
	675: "Soldado",
	432: "Paladín",
	321: "Dragontino",
	968: "Lancero",
}
// No sacaría nada
fmt.Println(profesiones[6])
profesiones[6] = "Samurai"
// Imprimiría Samurai ya que ahora si está en el mapa
fmt.Println(profesiones[6])
```
Una cosa al tener en cuenta es que cuando añadimos un elemento el mapa puede cambiar totalmente la ordenación

#### Eliminación de elementos por clave

Podemos usar la funcion delete para eliminar entradas del mapa por id, un ejemplo:
```
profesiones := map[int]string{
	675: "Soldado",
	432: "Paladín",
	321: "Dragontino",
	968: "Lancero",
}
// mapa , id de la entrada a eliminar
delete(profesiones, 432)
fmt.Println(profesiones)
```
### Struct

Viene a referirse a objetos en la vida cotidiana, lo que vendría siendo una clase en java por ejemplo

Copias de ese struct no apuntan a la misma referencia por lo que si cambias una la otra no se ve afectada para que sean iguales debemos usar "&" para indicar que esas 2 variables aputan a la misma referencia, es tal cual se hace en Arrays

#### Declaración
Debemos tener los struct a nivel de paquete

##### Declaración clásica
```
type Tecnica struct {
	nivelRequerido int
	nombre         string
	mana           int
}
```
##### Struct anónimo

Se puede declarar un struct directamente en una función 
```
tecnica := struct{ nivelRequerido int }{nivelRequerido: 50}
fmt.Print(tecnica)
```


#### Instanciación

##### Manera normal 
```
tecnica := Tecnica{
	nivelRequerido: 10,
	nombre:         "Última Pesadilla",
	mana:           40,
}
fmt.Print(tecnica)               // Si queremos consultar todos los valores del struct
fmt.Print("\n" + tecnica.nombre) // Si queremos consultar un valor en específico
```
##### Sintaxis de posicionamiento

Hay otra manera de instanciar un struct eliminando los nombres de los campos en este cada atributo corresponde exactamente a la posicion de los campos del struct a esta técnica se le llama "Positional Syntax"

no es recomendable su uso por razones de mantenibilidad ya que si cambias el orden de los campos o añades otro lo vas a tener dificil para mantenerlo 

un ejemplo:
```
tecnica := Tecnica{
	10,                 // Corresponde con la 1º posición del struct nivelRequerido
	"Última Pesadilla", // nombre
	40,                 //mana
}
```
#### Composición

En go no existe la herencia pero tenemos algo parecido usaremos el "embedding" 
```
type Magia struct {
	mana int
}

type MagiaNegra struct {
	Magia
	danno int
}

func main() {
	magiaNegra := MagiaNegra{}
	magiaNegra.mana = 10
	magiaNegra.danno = 500
	// {{10} 500}
	fmt.Println(magiaNegra)
	// 10
	fmt.Println(magiaNegra.mana)
	// 500
	fmt.Println(magiaNegra.danno)
}
```
En otros lenguajes tradicionales tendríamos una herencia de magia negra con magia, pero en Go tendríamos que embeber Magia dentro de Magia negra

#### Tags

Los tags son usados para añadir constraints o limitaciones esto no actua directamente sobre el struct sino que es usado por frameworks de terceros o uno custom que haga uso de esa información para cierto fin usando el paquete de reflection

Básicamente es añadir metadatos a los campos de un struct para un framework ya sea de terceros o custom use esa información para validar algo o saber como des-serializar un json xml etc
```
type Tecnica struct {
	nivelRequerido int
	nombre         string `required,max:"10"`
	mana           int
}

func main() {
	tecnicaReflection := reflect.TypeOf(Tecnica{})
	campo, _ := tecnicaReflection.FieldByName("nombre")
	// required,max:"10"
	fmt.Print(campo.Tag)
}
```

#### Convenciones de nombres

Al igual que las variables si ponemos mayúscula la primera letra querrá decir que están expuestas a toda la aplicación pero en cambio si está en minúscula estará disponible a nivel de paquete solamente, usaremos pascal naming 

## Constantes

Van precedidas de la palabra const
1. `const constante string = "constante"`
1. `const constante = "constante"`
Como dato curioso en otros lenguajes tipo java puedes tener asignacioens de constantes que dependan en la ejecución de una función por ejemplo es decir que se resuelvan en tiempo de ejecución , en Golang eso no se puede pero sin embargo las operaciones matemáticas entre literales o constantes si que están permitidas 

A nivel de compilador:
1. Son inmutables puede aplicarse el "shadow"
2. Son reemplazadas por el compilador en tiempo de compilación
3. El valor debe poder ser calculado en tiempo de compilación

```
const(
	numero1 = 1
	numero2 = 2
	numero3 = numero1 + numero2 // valdría 3
)
```
Y como último dato importante no se puede hacer una constante de una **colección**, estos **siempre serán variables**

### Constantes enumerados

Suelen ir a nivel de paquete y mas raramente a nivel de función (aunque no deberías)

#### Declaración completa simple con iota
puedes usar a nivel de paquete la siguiente forma de declarar una enumeracion de constantes
```
const (
	constanteEnumerada  = iota // valdría 0
	constanteEnumerada2 = iota // valdría 1
	constanteEnumerada3 = iota // valdría 2
)
```
En este caos al usar iota este actua como un contador que empieza desde 0 y va incrementando su valor en 1

#### Declaración simple con iota
Si quitamos el iota de la constante 2 y 3 tendríamos el mismo resultado ya que el compilador de go asigna a las constantes que no están inicializadas explicitamente el ultimo valor seteado de tal manera 
```
const (
	constanteEnumerada  = iota // valdría 0
	constanteEnumerada2        // valdría 1
	constanteEnumerada3        // valdría 2
)
```
#### Declaración simple con literales
Ahora si en vez de usar iota usamos un literal todas las constantes por debajo de esa tendrán ese valor hasta que se setee otro literal de tal manera

```
const (
	constanteEnumerada = 1  // Valdría 1
	constanteEnumerada2     // Valdría 1
	constanteEnumerada3 = 2 // Valdría 2
	constanteEnumerada4     // Valdría 2
)
```

#### Multiples declaraciones de bloques con iota
Ahora bien si tenemos por ejemplo 2 bloques de constantes y usamos iota en los 2 iota el valor se reiniciara para cada bloque (Osea que el scope de iota esta ligado a cada bloque de constantes ) de tal manera
```
const (
	constanteEnumerada = iota  // valdría 0
	constanteEnumerada2        // valdría 1
)

const (
	constanteEnumerada3 = iota // valdría 0
)
```
Recuerda que las operacioens matemáticas entre constantes o literales están permitidas asique podríamos hacer algo parecido a esto
```
const (
	constanteEnumerada = iota + 5  // valdría 5
	constanteEnumerada2            // valdría 6 
)
```

o algo un poco mas útil sería aprobechar esa funcionlidad para hacer potencias a traves del operador bitwise (<<) como dijimos antes no se pueden llamar a funciones y en Go para hacer el tema de potencias necesitas usar la librería de math por lo tanto para poder hacer potencias tendríamos algo como esto:

```
const (
	_  = iota
	KB = 1 << (10 * iota) // Con esto conseguimos una potencia 10^1
	MB					  // Con esto conseguimos una potencia 10^2 etc
	GB
	TB
	PB
	EB
	ZB
	YB
)

func main() {
	// Aqui tenemos un decimal que representa el peso de un fichero
	fileSize := 4000000000.
	/*
		Con el Printf aplicamos cierto formato
		%.2f -> decimal de precisión 2
		concatenado con " GB"
	*/
	fmt.Printf("%.2f GB", fileSize/GB) // Imprime 3.73 GB
}
```

Tambien podrías usar los operadores Shift (>>)

#### Usos del valor 0 con iota
Un buen caso para usar las constantes enumeradas sería:

```
const (
	especialistaError = iota
	especialistaGato
	especialistaPerro
	especialistaHamster
)

func main() {
	var tipoEspecialista int
	fmt.Println(tipoEspecialista == especialistaError) // True

	tipoEspecialista = 1
	fmt.Println(tipoEspecialista == especialistaGato) // True

}
```

#### Descartes de valores con iota

podemos descartar un valor generado por iota usando `_` un ejemplo:
```
const (
	_ = iota			// Descartamos el valor 0
	especialistaGato	// Valdría 1
	especialistaPerro	// Valdría 2
	especialistaHamster // Valdría 3
)

func main() {
	tipoEspecialista := 1
	fmt.Println(tipoEspecialista == especialistaGato) // True
}
```
Podemos descartar multiples valores
```
const (
	_                = iota // Descartamos el valor 0
	_                = iota // Descartamos el valor 1
	especialistaGato        // Valdría 2
)
```

En el que para verificar que una constante no está inicializada usamos la constante `especialistaError` que vale 0

### Convenciones de nombre
En otros lengajes verías nombres parecido a esto: CONSTANTE_PI sin embargo en go la convención es la misma que con las variables para el mismo caso en go sería constantePi si queremos que solo sea accesible desde ese paquete o ConstantePi para que sea accesible globalmente (esto aplicado a variables a nivel de paquete las de nivel de función serían con minúscula siempre)

# Scope de variables y convención de nombres
1. Pascal case -> Export variables (Variables Globales)
1. Camel Case -> internal variables (Variables de paquete)

## Nivel de paquete
En go las variables que estén a nivel de paquete
1. Si empiezan por mayúscula -> `var Numero int 5` serán accesibles por todos
1. Si empiezan por minúscula -> `var numero int 5` será accesible solo en ese paquete
1. Capitalización de acrónimos -> si usamos algún acrónimo este debe estar en mayúscula var direccionHTTP string = "http://localhost:25565"

## Nivel de función
En go las variables de función solo estarán disponibles para los miembros de la misma función y si una variable se llama de la misma forma que una a nivel de paquete, la que está a nivel de función será la que se use (a esto se le llama Shadow que explicaremos en mas detalle en el siguiente apartado)

Esto no solo aplica a los nombres sino tambien al tipo 

## Misma variable distintos scope
En go se puede tener distintas variables con el mismo nombre siempre que estas estén en distintos scope el orden de preferencia que tiene Go sobre esto cuando por ejemplo lees el valor de una variable es que en este caso concreto la variable mas cercana coge precendencia

Imagínate que tienes:
1. Una variable numero con valor 0 a nivel de paquete
1. Otra que se llame igual con valor 2 a nivel de función

si por ejemplo en esa función lees el valor de numero el orden de preferencia hace que leas el valor 2 ya que está mas cercana (de hecho está en el mismo bloque) a esto se le llama "variable shadowning"

Por resumir y que quede claro el shadowning es cuando tenemos la misma variable en distintos scopes entonces la forma de determinar con cual vamos a interactuar es la que mas cercana esté a donde se está usando por ejemplo un `fmt.Println(numero)`

Con esta técnica tambien se puede hacer "shadow" a un tipo de las variables de distintos scopes de la misma forma que de los valores

# If

## If básico
```
if condicion {
	fmt.Print("La condicion es afirmativa")
} else if condicion && otraCondicion {
	fmt.Print("Las 2 condiciones son afirmativas")
} else {
	fmt.Print("La condicion es negativa")
}
```

## If avanzado
Podemos usar un return de varios valores en la condición y usarlo tanto dentro del if como en la condición como por ejemplo la variable ok que dictamina si la key con valor `675 -> osea la variable id` está en el mapa `profesiones` 

Luego dento del if usamos la variable trabajo que lleva el valor de la key con valor 675 en el mapa 

```
profesiones := map[int]string{
	675: "Soldado",
	432: "Paladín",
	321: "Dragontino",
	968: "Lancero",
}

id := 675
if trabajo, ok := profesiones[id]; ok {
	fmt.Printf("Trabajo con id: %v y value: %v", id, trabajo)
}
```
### Comparadores

En Go se pueden usar todos operadores habituales de la programación `& | < > ==`

### Llamadas a funciones

En go las condiciones tambien pueden ser el return de una función
```
func main() {

	if createCondition() == false {
		fmt.Print("La condición es falsa")
	}
}

func createCondition() bool {
	fmt.Print("Retornando condición")
	return true
}
```

# Switch

Los statements que pueden ir dentro y por lo tanto se ejecutarian en cada case pueden ser de 0 a N de tal manera podríamos tener mas de 1 statement en un case un ejemplo muy simple

Tambien podemos hacer uso de break si por cualquier razón en un caso específico no queremos ejecutar cierta parte del switch poniendo un `break` en el ejemplo no va a tener mucho sentido pero esto junto a un if por ejemplo si que podría llegar a tener sentido
```
switch {
case 1:
	fmt.Print("Puedo tener mas de 1 statement entre cases")
	fmt.Print("Y pertenecerían al mismo case en este caso del valor numero > 0")
	break
	fmt.Print("Esto o se ejecuta ya que esta debajo de un break")
```
## Switch simple

```
numero := 1
switch numero {

case 1:
	fmt.Print("Uno")
case 2:
	fmt.Print("Dos")
default:
	fmt.Print("Ni 1 ni 2")
}
```
## Switch multiple

Podemos concatenar condiciones en un mismo case
```
numero := 1
switch numero {
case 1, 2:
	fmt.Print("Uno o Dos")
default:
	fmt.Print("Ni 1 ni 2")
}
```
A tener en cuenta que en los switch no puede haber valores duplicados es decir que 2 cases distintos tengan el mismo valor te daría un syntax error


## Switch avanzado

Al igual que con los if podemos definir una variable dentro del switch directamente y evaluar ese resultado

```
// Definimos una variable directamente en el switch y calculamos su valor ->  2 + 1 = 3
switch suma := 2 + 1; suma {
case 1, 2:
	fmt.Print("Uno o Dos")
default:
	fmt.Print("Ni 1 ni 2")
}
```

## Switch con condiciones complejas

Podemos usar condiciones complejas en nuestros cases un ejemplo:
```
numero := 0
switch {
case numero > 0:
	fmt.Print("Mayor que cero")
case numero < 0:
	fmt.Print("Menor que cero")
default:
	fmt.Print("Es cero")
}
```
en este tipo de switch los cases pueden hacer overlapping ya que puede que 2 cases sean true para cierta condición en estos casos el que antes de evalúe tiene preferencia sobre el resto 

## Switch con fallthrought

A diferencia de java no hay falltrought de manera por defecto, tenemos que indicarlo a traves de `fallthrough` al final de los statement del case
```
numero := 1

switch {
case numero > 0:
	fmt.Println("Uno")
	// Esto haría que se ejecutase el siguiente case aunque el mismo sea false
	fallthrough
case numero > 5: // Esto es false ya que numero es = 1
	fmt.Println("Cinco")
default:
	fmt.Println("Ni 1 ni 5")
}
```
Pero sin embargo la consola nos muestra:
```
Uno
Cinco
```
## Switch con interfaces

Podemos usar interfaces para por ejemplo saber de que tipo es un valor

```
var condicion interface{} = 1 // podemos asignar cualquier valor de los aprendidos en este tutorial

switch condicion.(type) { // Conseguiríamos el type de la interfaz
case int, int8, int16, int32, int64:
	fmt.Print("Es un entero")  // Se ejecutaría este case
case float32, float64:
	fmt.Print("Es un decimal")
case string:
	fmt.Print("Es una cadena de texto")
}
```
# For
```
for i := 1; i < 6; i++ {
	// Imprimiría en consola 1 2 3 4 5 
	fmt.Print(i)
	fmt.Print(" ")
}
```
# ForEach

podemos manejar individualmente los valores de un slice o array por ejemplo:
```
slice := []int{1, 2, 3}
for index, valor := range slice {
	fmt.Print(index, valor)
}
```
Si queremos omitir el index usaremos el `_`
```
slice := []int{1, 2, 3}
for _, value := range slice {
	fmt.Print(value)
}
```

para mapas podremos obtener tanto el value como la key del mapa aunque siempre podremos omitir alguno de los mismos con `_`
```
profesiones := map[int]string{
	675: "Soldado",
	432: "Paladín",
	321: "Dragontino",
	968: "Lancero",
}

for index, value := range profesiones {
	fmt.Println(index, value)
}
```
tambien podremos usar strings

```
cadena := "HolaMundo"
fmt.Println("Índice | Valor Unicode | Valor en String")
for index, value := range cadena {
	fmt.Println(index, value, string(value))
}
```

en este caso tendremos la siguiente salida (Lo ordeno en una tabla para que se vea mejor)

| Indice | Valor unicode | Valor en String |
|:---:|:---:|:---:|
| 0 | 72  | H |
| 1 | 111 | o |
| 2 | 108 | l |
| 3 | 97  | a |
| 4 | 77  | M |
| 5 | 117 | u |
| 6 | 110 | n |
| 7 | 100 | d |
| 8 | 111 | o |

# Labels 

## Breaks
Al igual que java se pueden hacer uso de las label para por ejemplo en el caso de que tengamos 2 fors 
```
	for i := 1; i < 6; i++ {
		for j := 0; j < 6; j++ {
			break // esto rompería la ejecución del for con la variable j
		}
	}
label2:
	for i := 1; i < 6; i++ {
		for j := 0; j < 6; j++ {
			// en cambio este rompería la ejecución de todo
			// ya que la label "label2" está por encima de los 2 for
			break label2 
		}
	}
```
# Defer

defer es la técnica por la cual el statement que vaya precedido de él se ejecutará el último inmediatamente antes del return de la función (en el caso de que no haya return será el ultimo statement en ejecutarse) un ejemplo:
```
fmt.Println(1)
defer fmt.Println(2) // statement deferido
fmt.Println(3)
```
Resultado:
```
1
3
2
```
Ahora que pasa si tenemos varios statements deferidos
```
defer fmt.Println(1)
defer fmt.Println(2)
defer fmt.Println(3)
```
Resultado:
```
3
2
1
```
El comportamiento que nos vendría a la cabeza que tendría que tener este código debería de ser 1 2 3 ya que se ejecuta todo al final del método, pero en cambio obtenemos justo lo contrario

Esto es debido a que los statements deferidos funcionan por FILO (First In Last Out) imagina una pila de libros y ten presente la regla de que solo puedes coger 1 a la vez si apilas 3 libros libro1 libro2 y libro3 en ese orden concreto cuando quieras coger esos libros el primero que recogerás es el libro3

Ocurre lo mismo con los statements deferidos el ultimo que entra es el primero en salir

## Usos

Los usos de esto podría ser por ejemplo el cierre de recursos , podrías tener al final del método el cierre de los mismos pero podrías olvidarte de todos los recursos que tienes que cerrar haciendo defer asociarías el abrir del recurso con el cerrar del mismo inmediatamente despues (aunque realmente lo ejecutarías al final de la función)

### Problemas

Una cosa a tener en cuenta es que por ejemplo si estás en un for loop y el usar el defer para cerrar un recurso que esté en ese for cuando realmente se va a ejecutar ese statement es al final de la función lo del for loop podrías tener miles de recursos abiertos a la vez así (que luego se cerrarían pero no deberías ya que podría dar lugar a fallos o problemas de rendimiento)

### Soluciones

Una opción sería delegar ese cierre de recurso a una función y hacer ahí el defer

## Llamadas a funciones y parámetros

Según lo que vimos anteriormente podrías pensar que este codigo imprimiría `final`
```
variable := "comienzo"
defer fmt.Print(variable)
variable = "final"
```
Pero la realidad es que imprimiría `comienzo` esto es debido a que en las llamadas a funciones deferidas lo que se va a ejecutar coge los valores de los argumentos que tuviera en ese momento esa variable de tal manera que en nuestro ejemplo cogería el valor `comienzo`

# Panicking

Esto es por ejemplo un erro grave en Go , no hay muchos casos por lo que se pueda dar un error grave del que la aplicación no sepa como seguir por ejemplo el típico caso sería una petición a un servidor remoto en el que no se recibe respuesta alguna , esto no es causa de un panic ya que tendremos un valor de error para interpretar en este caso por ejemplo un 500 o un 404 por decir algunos

Un ejemplo de panic sería que estás intentand leer una plantilla para generar una página web pues bien si no se puede leer esa plantilla no se puede seguir porque sería un error grave del que no puedes recuperarte

por otro lado si vas a abrir un fichero de log y no puedes abrirle ese no es un panic ya que la ejecución puede seguir

En go un error grave es lo que se le llama un panic ya que la aplicación no sabe que hacer despues de eso:
```
	numero1, numero2 := 1, 0
	division := numero1 / numero2
	fmt.Print(division)
```
```
panic: runtime error: integer divide by zero

goroutine 1 [running]:
main.main()
        C:/Users/MaQuiNa1995/workspace/Go_Workspace/HolaMundo/src/maquina1995/hola.mundo/Main.go:11 +0x11
exit status 2
```
## Provocar panics

Podemos probecar errores manualmente gracias a la funcion panic()
```
fmt.Println("Comienzo")
panic("Algo malo ha pasado")
// el IDE nos avisará de que este statement no va a ejecutarse
fmt.Println("Fin") 
```
Resultado:
```
Comienzo
panic: Algo malo ha pasado

goroutine 1 [running]:
main.main()
        C:/Users/MaQuiNa1995/workspace/Go_Workspace/HolaMundo/src/maquina1995/hola.mundo/Main.go:14 +0x65
exit status 2
```
Un tema importante es que el panic será ejecutado justo despues de los statements que hayan sido deferidos asique nuestros posibles cierres de recursos que tengamos deferidos podrán ejecutarse normalmente

# Recover

Es usado para salvar un error grave (panic) , solo es útil en statements que estén deferidos ya que como hablamos anteriormente estos se ejecutan antes del panic por lo tanto podrán arreglar el error

Cuando se produce un error la función que se estuviera ejecutando en ese momento para su ejecución pero si salvas ese error las funciones padre que hayan llamado a esta podrían seguir la ejecución

un ejemplo de un manejo de excepción:
```
func main() {
	fmt.Print("Empieza el main")
	numero := -1
	start(numero)
	fmt.Printf("Acaba el main")
}

func start(numero int) {

	// Requiere que esté deferida para
	// que pueda manejar la excepción
	// tambien puede ser una función anónima
	defer manejarExcepcion()
	if numero == 0 {
		panic("Error: el valor de número no puede ser cero")
	}
	fmt.Printf("El número es %v\n", numero)
}

func manejarExcepcion() {
	if exception := recover(); exception != nil {
		fmt.Println("Manejando la excepción: ", exception)
	}
}
```

# Punteros

```
numero1 := 1
// aunque se asigne a numero2 apuntan
// a distintas direcciones de memoria
numero2 := numero1
fmt.Println(numero1, numero2) // 1 1

// al no apuntar a la misma dirección de memoria
// aunque asignemos el valor 0 numero2 no se ve afectada
numero1 = 8
fmt.Println(numero1, numero2) // 8 1
```

## Creación

```
var numero1 int = 1
// Hemos creado un puntero para indicar
// que numero2 va a tener un puntero de tipo integer
// a la variable numero 2
var numero2 *int = &numero1
fmt.Println(numero1, numero2) // 1 0xc0000aa058

// Ahora al apuntar a la misma referencia de memoria
// Al cambiar uno el otro tambien se ve reflejado
numero1 = 8
fmt.Println(numero1, numero2) // 8 0xc0000aa058
```
Ahora el 0xc0000aa058 representaría la dirección de memoria donde estaría almacenado el valor 8 podemos probar esto convirtiendo la variable numero1 a un puntero añadiendo el siguiente statement al código anterior `fmt.Println(&numero1) // 0xc0000aa058 0xc0000aa058`

## Deferenciación

Podemos recuperar un valor que esté almacenado en un puntero gracias a `*`
```
var numero1 int = 1
var numero2 *int = &numero1
fmt.Println(numero1, numero2) // 1 0xc0000aa058

numero1 = 8
// Al usar el asterisco estamos reemplazando el
// valor de la memoria donde está almacenada por su valor real
fmt.Println(numero1, *numero2) // 8 8
```
# Funciones
Una aplicación siempre debe tener un punto de entrada:

```
// siempre en el paquete main
package main

import "fmt"

// Sin parámetros y llamada main
func main() {
	fmt.Print("Empieza el main")
}
```
## Convención de nombres
Se sigue las reglas normales ya descritas en la guía pascalCase o camelCase con la primera minuscula (solo disponible para ese fichero) y con la primera mayúscula para que pueda ser accedido desde toda la aplicación

## Parámetros 

```
func main() {
	pintarEnConsola("mensaje")
}

// func nombre (nombreVariable tipo, ...) 
func pintarEnConsola(mensaje string) {
	fmt.Print(mensaje)
}
```
Si tienes mas de 1 variable del mismo tipo podrías agruparlas
```
func pintarEnConsola(mensaje, mensaje2 string, numero int) {
	fmt.Print(mensaje, mensaje2, numero)
}
```
## Punteros en parámetros de funciones

```
func main() {
	saludo := "Hola "
	nombre := "MaQuiNa"

	saludarPorConsola(saludo, nombre)

	println("Hemos saludado a", nombre)
}

func saludarPorConsola(saludo, nombre string) {
	fmt.Println(saludo, nombre)
	nombre = "nombreCambiado"
}
```
Resultado:
```
Hola  MaQuiNa
Hemos saludado a MaQuiNa
```
```
func main() {
	saludo := "Hola "
	nombre := "MaQuiNa"

	saludarPorConsola(&saludo, &nombre)

	println("Hemos saludado a", nombre)
}

func saludarPorConsola(saludo, nombre *string) {
	fmt.Println(*saludo, *nombre)
	*nombre = "nombreCambiado"
}
```
Resultado:
```
Hola  MaQuiNa
Hemos saludado a nombreCambiado
```
### Vararg 
Podemos usar esta notación para wrapear un conjunto de variables en un slice y trabajar con una serie de posibles valores indeterminado
```
func main() {
	saludo := "Hola"
	nombre := "MaQuiNa"
	nombre2 := "MaQuina2"

	saludarPorConsola(&saludo, nombre, nombre2)
}

func saludarPorConsola(saludo *string, nombres ...string) {
	for _, nombre := range nombres {
		fmt.Println(*saludo, nombre)
	}
}
```
Puedes incluso no pasar ningun argumento en el parámetro del var arg de modo que en la funcion de antes sería plausible esto: `saludarPorConsola(&saludo)`

De tal manera que entonces el forEach no se ejecutaría ya que nombres estaría vacío

## Return

Podemos retornar mas de 1 valor en go en las funciones esto es util para por ejemplo evitar el uso de panic y controlar el flujo de errores con objetos secundarios un ejemplo:

```
func main() {
	division, error := dividir(5.0, 0.0)

	// Si error no es nulo quiere decir que hubo excepciones
	if error != nil {
		// imprimimos por consola el error
		fmt.Print("Hubo un error mas info: ", error)
		// paramos la ejecución del método
		return
	}
	// Imprimimos el valor de la división
	fmt.Print("El valor de la división es:", division)
}

// En una función podemos retornar mas de un valor
// normalmente el 1º es el resultado de la función
// y los segundos y sucesivos son errores por ejemplo
func dividir(dividendo, divisor float64) (float64, error) {

        // En go usamos las ward clausules en la medida
        // de lo posible para evitar piramides infernales de ifs
	if divisor == 0.0 {
		// En vez de controlar el flujo con panic
		// usamos la String creada a partir de fmt.Errorf
		return 0.0, fmt.Errorf("No se puede dividir entre 0")
	}

	// retornamos el valor de la división y nil
	// que indica que no hubo error
	return dividendo / divisor, nil
}
```

## Funciones anónimas

En go podemos crear funciones dentro de funciones 

### Simple
```
func main() {
        // Declaramos la funcion
	func() {
		fmt.Print("Hola")
        // y con los `()` hacemos la llamada a
        // la misma inmediatamente
	}()
}
```

### Problema en entornos asincronos
```
func main() {

	// podemos usar variables de fuera de la
	// función ya que está en el mismo scope
	// Aqui el problema es que en cuanto vayamos
	// a la programación asincrona vamos a tener problemas
	for i := 0; i < 5; i++ {
		func() {
			fmt.Print(i)
		}()
	}
	// Esto en cambio tiene garantizado el correcto
	//funcionamiento en entornos asincronos
	// ya que se le pasa el valor vada ciclo
	for i := 0; i < 5; i++ {
		func(i int) {
			fmt.Print(i)
		}(i)
	}
}
```
## Funciones como tipos

En go podemos tener funciones como variables un ejemplo

```
func main() {

	// Aqui declararíamos la función
	funcion := func() {
		fmt.Print("saludos desde dentro de una función")
	}

	// Aqui tenemos otra forma de declarar una función
	var funcion2 func() = func() {
		fmt.Print("saludos desde otra función nueva")
	}

	// aqui las ejecutaríamos
	funcion()
	funcion2()

}
```
## Métodos

Son básicamente los mismo que una función solo que le damos un contexto donde ejecutarse para asi por ejemplo de 1 struct podemos definir "métodos" como si por ejemplo en java en una clase metiéramos un método un ejemplo

```
type hechicero struct {
	mana   int
	nombre string
}

func main() {

	mago := hechicero{
		100,
		"MaQuiNa",
	}

	fmt.Println("Maná actual del mago: ", mago.mana)
	// Aunque el struct no tenga este metodo hemos anclado esa función a ese tipo
	mago.lanzarHechizo()
	fmt.Println("Maná actual del mago: ", mago.mana)
}

// en este caso estamos "añadiendo" una función para poder ser invocada desde hechicero
// de tal manera aunque los struct no puedan tener una función dentro como si de una clase
// y un método en java serían podemos vincular una función a cierto struct

// notese que si queremos que los cambios que hagamos a este struct se hagan
// efectivos para en este caso la función main desde donde hemos pasado el struct
// necesitamos marcar el tipo del parámetro con un *
func (mago *hechicero) lanzarHechizo() {
	mago.mana = mago.mana - 10
	fmt.Println(mago.nombre, " Lanza Bola de fuego maná restante: ", mago.mana)
}
```
Resultado:
```
Maná actual del mago:  100
MaQuiNa  Lanza Bola de fuego maná restante:  90
Maná actual del mago:  90
```

# Interfaces

Las interfaces no describen datos como los structs , sino comportamientos un ejemplo del uso de las mismas:
```
/*
 Se define un comportamiento es decir en este caso se va a
 escribir bytes en algun lugar ya sea un fichero una conexión TCP
 solo nos interesa lo que entra y lo que sale de la función
 esto es lo que denominamos "comportamiento"

 Lo que devuelva será (nº de bytes escritos y el posible
	error que pueda producirse) respectivamente
*/
type Escritor interface {
	Write([]byte) (int, error)
}

/*
 Ahora solo necesitamos un struct que implemente esa interfaz
 si vienes de otros lenguajes tipo java esperarías algo tipo
 implements para implementar la interfaz pero en go , eso se hace
 creando un método con la misma firma que el método de la interfaz
 que acepte este struct
*/
type EscritorConsola struct{}

/*
 Aqui definimos la implementación de la interfaz
*/
func (escritorConsola EscritorConsola) Write(bytesEscribir []byte) (int, error) {
	bytesEscritos, error := fmt.Print(string(bytesEscribir))
	return bytesEscritos, error
}

func main() {

	// De tal manera que puedo sustituir EscritorConsola{} por por ejemplo
	// EscritorArchivo{} ya que ese tambien implementaría la interfaz Escritor
	// porque cumple el contrato(método) de la misma
	var escritor Escritor = EscritorConsola{}
	escritor.Write([]byte("Hola mundo"))
}
```

## Convención de nombres

* El nombre de la interfaz debe ser descriptivo de lo que hace
* El nombre de la interfaz debe describir una accion (escribir)
* Si tienes una interfaz con 1 solo método el nombre de la interfaz tendría que ser el nombre del método tambien
* Si tienes mas de un método en la interfaz el nombre debe indicar en conjunto es decir si tienes sumar dividir restar y multiplicar la interfaz se debería de llamar Calcular

## Interfaces de interfaces 

Las interfaces de interfaces se usan principalmente para recolectar una serie de utilidades que son a su vez interfaces como podría ser la conexión a una base de datos tendrías por ejemplo un método para abrir la conexión a la misma y otro para cerrarlo

```

```


