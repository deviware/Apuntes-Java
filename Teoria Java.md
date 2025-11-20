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



