# APUNTE 1 — Introducción a Java y Ciclo de Ejecución

## 1. ¿Qué es un algoritmo?

Un **algoritmo** es una lista finita, ordenada y clara de pasos que permiten resolver un problema.

**Ejemplo:**
Para hacer un mate:

1. Calentar agua.
2. Poner yerba en el mate.
3. Sacudir para acomodar la yerba.
4. Cebar con agua caliente.

Esto también sería un algoritmo porque tiene pasos definidos, ordenados y finitos.

---

## 2. ¿Qué es un programa?

Un **programa** es un conjunto de instrucciones que la computadora interpreta y ejecuta para cumplir una tarea.

En Java, ese programa es un archivo con código fuente que luego se compila y se ejecuta.

---

## 3. El proceso de creación y ejecución en Java

Java sigue una cadena de pasos muy clara:

1. **Escribir código fuente** → archivo `.java`.
2. **Compilar** con `javac` → genera bytecode `.class`.
3. **Ejecutar** con `java` → JVM interpreta el bytecode.

Java permite la filosofía **“Write Once, Run Anywhere”**, es decir, compilar una vez y ejecutar en cualquier plataforma.

---

## 4. Bytecode, JVM, JDK y JRE

### **JDK (Java Development Kit)**

Conjunto de herramientas para desarrollar en Java:

* `javac` (compilador)
* `java` (intérprete/JVM)
* empaquetador `.jar`
* javadoc

### **JRE (Java Runtime Environment)**

Permite **ejecutar** aplicaciones Java. No incluye el compilador.

### **JVM (Java Virtual Machine)**

Es la encargada de interpretar y ejecutar el bytecode.

---

## 5. Ediciones de Java

Java tiene diferentes versiones enfocadas en distintos usos:

* **Java SE**: aplicaciones de escritorio y consola.
* **Java EE / J2EE**: aplicaciones empresariales distribuidas.
* **Java ME / J2ME**: dispositivos embebidos o móviles antiguos.

---

## 6. Características principales del lenguaje Java

* **Orientado a Objetos**
* **Multiplataforma**
* **Arquitectura robusta**
* **Garbage Collector** (manejo automático de memoria)
* **Seguro**

---

## 7. Primer programa en Java

Todo programa Java necesita una **clase pública** y un **método main** para ejecutarse.

```java
public class Primero {
    public static void main(String[] args) {
        System.out.println("Hola mundo");
    }
}
```

### Comentarios:

* El archivo debe llamarse **Primero.java**.
* `main` es el punto de entrada de toda aplicación Java.
* `System.out.println()` imprime texto por consola.

---

## 8. Estructura general de un programa

```java
package org.curso.java;
import javax.swing.JFrame;

public class Primero extends JFrame {
    public static void main(String[] args) {
        Primero p = new Primero();
        p.setSize(200, 200);
        p.setVisible(true);
    }
}
```

### Explicación:

* `package`: indica la carpeta lógica donde vive la clase.
* `import`: permite usar clases externas.
* `extends`: hereda de otra clase.
* `main`: ejecuta el programa.

---

## 9. Entornos de desarrollo

Herramientas comunes:

* **JDK / JVM**
* **NetBeans**
* **Eclipse**
* **IntelliJ**
* **BlueJ** (muy usado en UTN para P2)

---

# PREGUNTAS TIPO PARCIAL (con respuestas)

### **1. Explique la diferencia entre JDK y JRE.**

**Respuesta:** El JDK incluye herramientas para **desarrollar** (compilador, javadoc, jar). El JRE solo permite **ejecutar** aplicaciones y no contiene el compilador.

---

### **2. ¿Qué archivo genera el compilador y quién lo ejecuta?**

**Respuesta:** El compilador `javac` genera archivos `.class` (bytecode). Los ejecuta la JVM mediante el comando `java`.

---

### **3. ¿Por qué Java es multiplataforma?**

**Respuesta:** Porque compila a bytecode, que puede ejecutarse en cualquier sistema que tenga una JVM.

---

### **4. ¿Qué método debe tener toda aplicación Java?**

**Respuesta:** El método `public static void main(String[] args)`.

---

### **5. ¿Qué es Write Once, Run Anywhere?**

**Respuesta:** Es la capacidad de Java de compilar una vez un programa y ejecutarlo en cualquier plataforma sin modificaciones.

---

# APUNTE 2 — Lenguaje Java: APIs, Tipos de Datos, Paquetes y Niveles de Acceso

Este apunte corresponde al contenido del archivo **Introducción a Java.ppt** e incluye explicaciones detalladas, comentarios pedagógicos, ejemplos y preguntas tipo parcial con sus respuestas.

---

# 1. ¿Qué es Java?

Java no es solo un lenguaje. Es un **ecosistema completo** compuesto por:

* Un **lenguaje de programación**
* Un **entorno de desarrollo** (IDE)
* Un **entorno de ejecución** (JRE)
* Una **máquina virtual** (JVM)
* Herramientas como compilador, documentación, empaquetador, etc.

Java se utiliza para aplicaciones de escritorio, móviles, web, empresariales, IoT y sistemas distribuidos.

---

# 2. Características del Lenguaje Java

Java tiene una serie de características que definen su filosofía:

### ✔ **1. Orientado a Objetos**

Todo en Java es un objeto o forma parte de un objeto.

* Herencia
* Encapsulación
* Polimorfismo
* Abstracción

### ✔ **2. Portabilidad / Multiplataforma**

Gracias al bytecode y la JVM, Java funciona en cualquier sistema operativo.

### ✔ **3. Lenguaje Híbrido: Compilado + Interpretado**

* Se **compila** a bytecode
* Se **interpreta** o JIT-compila en la JVM

### ✔ **4. Garbage Collector**

Java libera memoria automáticamente.
Evita fugas de memoria comunes en C/C++.

### ✔ **5. Seguro**

Java corre dentro de una “máquina virtual” que protege al sistema operativo.

---

# 3. Herramientas del Entorno Java

### **JAVAC (compilador)**

Convierte código fuente `.java` en bytecode `.class`.

### **JAVA (intérprete/JVM)**

Ejecuta el bytecode.

### **JAVADOC**

Genera documentación HTML basada en comentarios especiales.

### **JAR**

Crea archivos comprimidos `.jar` con clases y recursos.
Se usan para distribuir aplicaciones.

---

# 4. Java APIs (Application Programming Interface)

Una **API** es un conjunto de clases, funciones y métodos que el programador puede usar sin implementarlas.

Java provee **tres tipos de API**:

### ✔ API **oficial** (incluida en el JRE)

Ejemplo:

* `java.lang`
* `java.util`
* `java.io`

### ✔ API **opcional**

Descargables aparte.
Ejemplo: Java 3D.

### ✔ API **de terceros**

Desarrolladas por empresas o programadores.
Ejemplo: SWT (GUI alternativa a Swing).

---

# 5. Los Tipos de Datos Primitivos en Java

| Tipo    | Tamaño  | Equivalente Clase |
| ------- | ------- | ----------------- |
| boolean | 1 bit   | Boolean           |
| char    | 16 bits | Character         |
| byte    | 8 bits  | Byte              |
| short   | 16 bits | Short             |
| int     | 32 bits | Integer           |
| long    | 64 bits | Long              |
| float   | 32 bits | Float             |
| double  | 64 bits | Double            |

### Comentarios claves:

* Los tipos primitivos **no son objetos**.
* Sus clases envolventes (Wrapper Classes) permiten tratarlos como objetos.

### Ejemplo:

```java
int edad = 20;
Integer edadObj = edad; // Autoboxing
```

---

# 6. Paquetes en Java

Un paquete es una **agrupación lógica de clases**.

### Definición:

```java
package net.programacion.ejemplos;
```

### Uso de import:

```java
import net.programacion.ejemplos.MiClase;
```

### Import masivo:

```java
import net.programacion.ejemplos.*;
```

### ¿Para qué sirven los paquetes?

* Ordenar el código
* Evitar nombres repetidos
* Estructurar proyectos grandes

---

# 7. Modificadores de Acceso

Controlan qué clases pueden acceder a atributos y métodos.

| Modificador            | Misma clase | Mismo paquete | Subclases | Otros paquetes |
| ---------------------- | ----------- | ------------- | --------- | -------------- |
| public                 | ✔           | ✔             | ✔         | ✔              |
| protected              | ✔           | ✔             | ✔         | ✘              |
| default (sin escribir) | ✔           | ✔             | ✘         | ✘              |
| private                | ✔           | ✘             | ✘         | ✘              |

---

## Ejemplos prácticos

### **public**

```java
public class Persona {
    public String nombre;
}
```

Accesible desde cualquier parte del programa.

### **private**

```java
public class Persona {
    private int dni;
}
```

Solo la clase Persona puede usar `dni`.

### **protected**

Ideal para herencia.

```java
protected int velocidad;
```

### **default**

El más restrictivo después de private.

---

# PREGUNTAS TIPO PARCIAL

### **1. ¿Qué es una API? Dé un ejemplo.**

**Respuesta:** Es un conjunto de clases y métodos listos para usar. Ej: `java.util.ArrayList`.

---

### **2. ¿Cuál es la diferencia entre un tipo primitivo y su clase envolvente?**

**Respuesta:** El tipo primitivo almacena valores simples. La clase envolvente es un objeto que encapsula ese valor (ej: `int` vs `Integer`).

---

### **3. ¿Qué modificador permite acceso desde cualquier paquete?**

**Respuesta:** `public`.

---

### **4. ¿Para qué sirve un paquete en Java?**

**Respuesta:** Para organizar clases y evitar conflictos de nombres.

---

### **5. ¿Qué tipo de datos usarías para:**

* Edad → `int`
* Bandera verdadero/falso → `boolean`
* Valor con decimales → `float` o `double`

---

# APUNTE 3 — Introducción a la Programación Orientada a Objetos (POO)

Este apunte corresponde al archivo **Intro Conceptos POO.pptx** e incluye explicaciones claras, ejemplos prácticos y preguntas tipo parcial con respuestas.

---

# 1. ¿Qué es la Programación Orientada a Objetos?

La **POO** es un paradigma donde los programas se estructuran en torno a **objetos**, que representan entidades del mundo real.

### En POO trabajamos con:

* **Clases** → Plantillas
* **Objetos** → Instancias reales
* **Atributos** → Datos del objeto
* **Métodos** → Comportamientos

La POO busca reflejar situaciones reales dentro del software.

---

# 2. Clase

Una **clase** es un modelo o plantilla que describe cómo serán los objetos.

### Ejemplo:

```java
public class Auto {
    String marca;
    int modelo;

    void acelerar() {
        System.out.println("El auto está acelerando");
    }
}
```

---

# 3. Objeto

Un **objeto** es una instancia concreta creada a partir de una clase.

### Ejemplo:

```java
Auto miAuto = new Auto();
miAuto.marca = "Toyota";
miAuto.modelo = 2020;
miAuto.acelerar();
```

---

# 4. Atributos

Son **características** del objeto.

Ejemplo en la clase Auto:

* marca
* modelo
* color

Los atributos se comportan como variables dentro de la clase.

---

# 5. Métodos

Representan las **acciones** o comportamientos.

```java
void frenar() {
    System.out.println("El auto frenó");
}
```

---

# 6. Los 4 pilares de la POO

La POO se apoya en cuatro conceptos fundamentales:

---

## 6.1. Encapsulamiento

Consiste en **ocultar los datos** del objeto y exponer solo lo necesario.

```java
public class Cuenta {
    private double saldo;

    public void depositar(double monto) {
        saldo += monto;
    }

    public double getSaldo() {
        return saldo;
    }
}
```

Beneficios:

* Seguridad
* Control del acceso
* Evitar inconsistencias

---

## 6.2. Abstracción

Consiste en **modelar lo esencial**, dejando fuera lo irrelevante.

Ejemplo:
"Auto" como concepto general sin detallar cada pieza interna.

---

## 6.3. Herencia

Permite crear clases nuevas basadas en otras.

```java
public class Vehiculo {
    int ruedas;
}

public class Moto extends Vehiculo {
    boolean tieneCasco;
}
```

La subclase hereda atributos y métodos.

---

## 6.4. Polimorfismo

Significa "muchas formas". Permite cambiar el comportamiento según el objeto.

```java
public class Animal {
    void hablar() { System.out.println("..." ); }
}

public class Perro extends Animal {
    void hablar() { System.out.println("Guau!"); }
}

public class Gato extends Animal {
    void hablar() { System.out.println("Miau!"); }
}
```

---

# 7. Constructores

Son métodos especiales que inicializan objetos.

```java
public class Persona {
    String nombre;

    public Persona(String nombre) {
        this.nombre = nombre;
    }
}
```

### Uso:

```java
Persona p = new Persona("Carlos");
```

---

# 8. this

`this` refiere al **objeto actual**.
Se usa para diferenciar atributos de parámetros.

---

# 9. Ejemplo completo

```java
public class Alumno {
    private String nombre;
    private int legajo;

    public Alumno(String nombre, int legajo) {
        this.nombre = nombre;
        this.legajo = legajo;
    }

    public void mostrar() {
        System.out.println(nombre + " (" + legajo + ")");
    }
}
```

---

# 10. PREGUNTAS TIPO PARCIAL

### **1. Defina clase y objeto.**

**Respuesta:** Una clase es un molde; un objeto es una instancia concreta creada a partir de ese molde.

---

### **2. ¿Qué es la encapsulación?**

**Respuesta:** Es ocultar los datos internos de un objeto permitiendo acceso solo mediante métodos públicos.

---

### **3. Indique las diferencias entre herencia y polimorfismo.**

**Respuesta:** La herencia crea nuevas clases basadas en otras; el polimorfismo permite redefinir comportamientos.

---

### **4. ¿Qué es un constructor y para qué sirve?**

**Respuesta:** Es un método especial que inicializa objetos.

---

### **5. ¿Qué representa la palabra clave this?**

**Respuesta:** Referencia al objeto actual dentro de la clase.

---

# APUNTE — Java 2: Wrappers, Strings, StringBuffer/StringBuilder

Este apunte corresponde al archivo **java 2.ppt** e incluye explicaciones claras, ejemplos prácticos, comparaciones y preguntas tipo parcial.

---

# 1. WRAPPERS (Clases Envolventes)

Los **Wrappers** son clases que representan a los **tipos primitivos** como objetos. Permiten:

* Convertir primitivos ↔ objetos
* Usar métodos para transformar datos
* Utilizar colecciones que aceptan solo objetos (ej: ArrayList)

### Tabla de equivalencias

| Primitivo | Clase Wrapper |
| --------- | ------------- |
| int       | Integer       |
| byte      | Byte          |
| short     | Short         |
| long      | Long          |
| float     | Float         |
| double    | Double        |
| boolean   | Boolean       |
| char      | Character     |

---

## 1.1. Constructores de Wrappers

Ejemplos:

```java
Integer i1 = new Integer(42);
Integer i2 = new Integer("42");

Float f1 = new Float(3.14f);
Float f2 = new Float("3.14f");

Character c1 = new Character('c');
```

> Notar que crear wrappers con `new` está deprecado desde Java moderno (se usa `valueOf`).

---

## 1.2. Métodos xxxValue()

Permiten obtener el valor primitivo desde un wrapper.

```java
Integer i = new Integer(42);
byte b = i.byteValue();
short s = i.shortValue();
double d = i.doubleValue();
```

### Ejemplo con truncamiento:

```java
Float f = new Float(3.14f);
short s = f.shortValue(); // resultado: 3
```

---

## 1.3. parseXxx() y valueOf()

Ambos toman un `String`.

| Método     | Devuelve       |
| ---------- | -------------- |
| parseXxx() | primitivo      |
| valueOf()  | objeto wrapper |

Ejemplo:

```java
double d4 = Double.parseDouble("3.14");
Double d5 = Double.valueOf("3.14");
```

### Conversión con bases:

```java
long L2 = Long.parseLong("101010", 2); // binario → primitivo
Long L3 = Long.valueOf("101010", 2);   // binario → wrapper
```

---

# 2. STRINGS

Las cadenas de texto en Java son **inmutables**. Cada modificación crea un nuevo objeto.

### Ejemplos:

```java
String x = "Java";
x.concat(" Rules!");
System.out.println(x); // sigue siendo "Java"

x.toUpperCase();
System.out.println(x); // aún "Java"
```

> Los métodos devuelven **nuevos Strings**, no modifican el original.

---

## 2.1. Métodos más importantes de String

* `charAt()` → obtiene carácter por índice
* `concat()` → concatena cadenas
* `equalsIgnoreCase()` → compara ignorando mayúsc/minúsc
* `length()` → cantidad de caracteres
* `replace()` → reemplaza caracteres
* `substring()` → extrae parte de un string
* `toLowerCase()` / `toUpperCase()`
* `trim()` → elimina espacios al inicio/final

---

# 3. StringBuffer y StringBuilder

### ¿Por qué existen?

Porque **String es inmutable**, lo que es ineficiente cuando se modifica muchas veces.

### Características:

| Clase         | Mutable | Rápida         | Sincronizada    |
| ------------- | ------- | -------------- | --------------- |
| String        | ❌       | —              | —               |
| StringBuffer  | ✔       | Medio          | ✔ (thread-safe) |
| StringBuilder | ✔       | ✔ (más rápida) | ❌               |

### Ejemplos:

```java
StringBuffer sb = new StringBuffer("abc");
sb.append("def");
System.out.println(sb); // abcdef
```

```java
StringBuilder sb2 = new StringBuilder("abc");
sb2.append("def").reverse().insert(3, "---");
System.out.println(sb2);
// salida: fed---cba
```

---

# 4. PREGUNTAS TIPO PARCIAL

### **1. ¿Qué diferencia existe entre parseInt() y valueOf()?**

**Respuesta:** `parseInt()` devuelve un primitivo. `valueOf()` devuelve un wrapper Integer.

---

### **2. ¿Por qué los Strings son inmutables?**

**Respuesta:** Por seguridad, caching interno y eficiencia del pool de Strings.

---

### **3. ¿Cuál es la diferencia entre StringBuilder y StringBuffer?**

**Respuesta:** StringBuilder es más rápido pero no sincronizado; StringBuffer es thread-safe.

---

### **4. ¿Qué imprime este código?**

```java
String x = "Hola";
x.concat(" Mundo");
System.out.println(x);
```

**Respuesta:** Imprime `Hola`.

---

### **5. ¿Qué método usarías para convertir un String a double?**

**Respuesta:** `Double.parseDouble(String)`.

---






