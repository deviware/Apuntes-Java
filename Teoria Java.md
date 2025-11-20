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

# APUNTE — Java 3: Clases, Objetos, Modificadores, Herencia, Interfaces y Excepciones

Basado en **java 3.ppt**. Incluye explicaciones detalladas, ejemplos comentados y preguntas tipo parcial con sus respuestas.

---

# 1. Clases y Objetos

* Una **clase** es una **plantilla** que define:

  * **Estado** → variables de instancia (atributos).
  * **Comportamiento** → métodos.
* Un **objeto** es una **instancia concreta** de una clase.

### Ejemplo básico

```java
public class Persona {
    private String nombre;
    private String apellido;

    public String getNombre() {
        return nombre;
    }

    public void setNombre(String n) {
        this.nombre = n;
    }

    public String getApellido() {
        return apellido;
    }

    public void setApellido(String ap) {
        this.apellido = ap;
    }
}

public class Primero {
    public static void main(String[] args) {
        Persona p = new Persona();
        p.setNombre("Juan");
        p.setApellido("Perez");
        System.out.println(p.getNombre());
    }
}
```

* `Persona` = clase
* `p` = objeto/instancia
* `nombre`, `apellido` = atributos
* `get/set` = métodos de acceso (encapsulamiento)

---

# 2. Encapsulamiento y Cohesión

## Encapsulamiento

Consiste en **ocultar los datos internos** de un objeto y exponerlos mediante métodos controlados (`get`/`set`).

Beneficios:

* Protege la integridad de los datos.
* Permite cambiar la implementación sin afectar a quien usa la clase.

## Cohesión

Una clase debe ser un **paquete coherente** de responsabilidades.

* Alta cohesión → clase hace cosas relacionadas.
* Baja cohesión → clase "Dios" que hace de todo.

Esto mejora:

* Mantenibilidad
* Reutilización
* Claridad del diseño

---

# 3. Herencia

La **herencia** permite que una clase (subclase) reutilice y extienda la funcionalidad de otra (superclase).

```java
public class Persona {
    private String nombre;
}

public class Alumno extends Persona {
    private int legajo;
}
```

* `extends` indica herencia.
* `Alumno` hereda los miembros `public` y `protected` de `Persona`.

Reglas:

* No hereda miembros `private`.
* Solo hay **herencia simple** (una sola superclase).

---

# 4. Paquetes

Un **paquete** es una organización lógica de clases bajo un mismo espacio de nombres.

```java
package org.com.curso;

import java.io.*;

public class Programa {
    public static void main(String[] args) {
        System.out.println("Hola mundo");
    }
}
```

Reglas:

* `package` **siempre va primero** en el archivo.
* Luego `import`.
* Después la definición de la/s clase/s.

---

# 5. Modificadores de Acceso (clases)

Para clases **top-level** (las que no están dentro de otras clases):

* `public` → se puede usar desde cualquier paquete.
* `default` (sin poner nada) → solo visible en el mismo paquete.

```java
package org.curso.ejemplo;

public class Ejemplo { }

// En otro paquete
package otro.paquete;
import org.curso.ejemplo.*;

public class OtraClase extends Ejemplo {  // OK
}
```

```java
// En cambio:
package org.curso.ejemplo;
class Ejemplo { }  // default

package otro.paquete;
import org.curso.ejemplo.*;

public class OtraClase extends Ejemplo {  // ERROR
}
```

---

# 6. Modificadores `final` y `abstract` (clases y métodos)

## `final` en clases

```java
public final class Persona { }

public class Juan extends Persona { } // ERROR
```

* Una clase `final` **no puede ser extendida**.

## `abstract` en clases

```java
public abstract class Prueba {
    // puede tener métodos abstractos o concretos
}
```

* No se puede instanciar.
* Se usa como **base de diseño**.

## Métodos `final`

```java
class SuperClass {
    public final void showEjemplo() {
        System.out.println("método final");
    }
}

class SubClass extends SuperClass {
    // ERROR si intentamos override:
    // public void showEjemplo() { ... }
}
```

* No pueden ser sobreescritos.

## Métodos `abstract`

```java
public abstract class Persona {
    public void correr() {
        // implementación concreta
    }

    public abstract void comer();
}
```

* Obligan a las subclases concretas a implementar el método.

---

# 7. Acceso a Miembros de Clase (atributos y métodos)

Modificadores para miembros:

* `public`
* `private`
* `protected`
* `default` (sin palabra clave)

### Reglas básicas

* `public`: accesible desde cualquier clase.
* `private`: solo dentro de la misma clase (no heredable directamente).
* `protected`: accesible por herencia, incluso en otros paquetes.
* `default`: accesible solo desde el mismo paquete.

Ejemplo con `protected`:

```java
package cert;

public class Parent {
    protected int x = 9;
}

package other;

class Child extends Parent {
    public void testIt() {
        System.out.println("x is " + x); // OK: acceso por herencia

        Parent p = new Parent();
        // p.x; // ERROR: no acceso por referencia, solo por herencia
    }
}
```

---

# 8. Overriding (Sobrescritura) vs Overloading (Sobrecarga)

## Overriding

Una subclase **redefine** un método de la superclase con **misma firma**.

```java
public class Animal {
    public void comer() {
        System.out.println("Comiendo en forma genérica");
    }
}

public class Caballo extends Animal {
    @Override
    public void comer() {
        System.out.println("Comiendo como caballo");
    }
}
```

Reglas:

* Misma firma (nombre + parámetros).
* Tipo de retorno igual o más específico.
* No puede tener un modificador de acceso **más restrictivo**.
* Métodos `static` **no se overridean**, se ocultan.

## Overloading

Mismo nombre de método, **distintos parámetros**.

```java
public void changeSize(int size, String name, float pattern) { }
public void changeSize(int size, String name) { }
public int changeSize(int size, float pattern) { return 0; }
public void changeSize(float pattern, String name) throws IOException { }
```

Se puede cambiar:

* Número de parámetros
* Tipo de parámetros
* Orden de parámetros
* Tipo de retorno
* Modificador de acceso

---

# 9. `this` y `super`

## `this`

Se refiere al **objeto actual**.

```java
public class Persona {
    private String nombre;

    public void setNombre(String nombre) {
        this.nombre = nombre; // diferencia entre atributo y parámetro
    }
}
```

## `super`

Hace referencia a la **superclase**.

```java
public class Persona {
    public void comer() { /* ... */ }
}

public class Alumno extends Persona {
    public void comer(String comida) { // overloading
        // lógica de Alumno
        super.comer(); // llama al método de Persona
    }
}
```

---

# 10. JavaBeans

Un **JavaBean** es una clase que cumple ciertas reglas:

* Atributos `private`.
* Métodos `getX()/setX()` públicos para cada atributo.
* Constructor público sin parámetros.
* Implementa `Serializable` (en contexto completo).

```java
public class Persona {
    private String nombre;
    private String apellido;
    private boolean soltero;

    public Persona() {
        this.nombre = "John";
        this.apellido = "Q";
    }

    public String getNombre() { return nombre; }
    public void setNombre(String nombre) { this.nombre = nombre; }

    public String getApellido() { return apellido; }
    public void setApellido(String apellido) { this.apellido = apellido; }

    public boolean isSoltero() { return soltero; }
    public void setSoltero(boolean soltero) { this.soltero = soltero; }
}
```

---

# 11. `instanceof` y Casting de Referencias

## `instanceof`

Permite preguntar si un objeto es instancia de una clase.

```java
Perro p = new Perro();
if (p instanceof Animal) {
    // true si Perro hereda de Animal
}
```

## Casting

```java
class Animal { }
class Dog extends Animal { }

Dog d = new Dog();
Animal a1 = d;          // upcast implícito
Animal a2 = (Animal) d; // upcast explícito
```

Ejemplo con `instanceof` antes de downcast:

```java
Animal[] a = { new Animal(), new Dog(), new Animal() };

for (Animal animal : a) {
    if (animal instanceof Dog) {
        Dog dog = (Dog) animal; // downcast seguro
        // dog.playDead();
    }
}
```

---

# 12. `enum`

`enum` define un conjunto fijo de constantes.

```java
enum CoffeeSize { BIG, HUGE, OVERWHELMING }

class Coffee {
    CoffeeSize size;
}

public class CoffeeTest1 {
    public static void main(String[] args) {
        Coffee drink = new Coffee();
        drink.size = CoffeeSize.BIG;
    }
}
```

Reglas:

* Solo `public` o `default`.
* **No** se puede declarar un `enum` dentro de un método.

---

# 13. Constructores

* Se ejecutan al instanciar un objeto.
* No tienen tipo de retorno (ni `void`).
* Deben llamarse igual que la clase.

```java
class Foo {
    Foo() { } // constructor por defecto
}
```

Si definís un constructor **propio**, el compilador ya **no** genera el constructor por defecto.

```java
class Foo {
    int size;
    String name;

    Foo(String name, int size) {
        this.name = name;
        this.size = size;
    }
}

Foo f = new Foo(); // ERROR: no hay constructor sin parámetros
```

### Constructores y `super`

```java
class Animal {
    Animal(String name) { }
}

class Horse extends Animal {
    Horse() {
        super(); // ERROR: falta el String del constructor de Animal
    }
}
```

---

# 14. `static` (miembros de clase)

Miembros `static` pertenecen a la **clase**, no al objeto.

```java
class Frog {
    static int frogCount = 0;

    public Frog() {
        frogCount++;
    }
}

class TestFrog {
    public static void main(String[] args) {
        new Frog();
        new Frog();
        System.out.println("frogCount: " + Frog.frogCount); // 2
    }
}
```

* Métodos `static` se invocan con `NombreClase.metodo()`.
* No se pueden overridear (se **ocultan**).

---

# 15. Interfaces

Una **interfaz** es un contrato.

```java
public interface Bounceable {
    void bounce();
    void setBounceFactor(int bf);
}

public class Ball implements Bounceable {
    public void bounce() { }
    public void setBounceFactor(int bf) { }
}
```

Reglas:

* Una clase **implementa** interfaces (`implements`).
* Una interfaz **extiende** otras interfaces (`extends`).
* Interfaces no pueden `implement` ni `extend` clases.
* Una clase puede implementar **múltiples interfaces**.

Ejemplo:

```java
interface Moveable { void moveIt(); }
interface Spherical { void doSphericalThing(); }

interface Bounceable extends Moveable, Spherical {
    void bounce();
    void setBounceFactor(int bf);
}
```

---

# 16. Excepciones (Introducción)

Una **excepción** es un problema que ocurre en tiempo de ejecución.

```java
class NPE {
    static String s;

    public static void main(String[] args) {
        System.out.println(s.length()); // NullPointerException
    }
}
```

## Origen

* JVM (ej: `NullPointerException`, `ArrayIndexOutOfBoundsException`).
* Código del programador (excepciones propias).

## Jerarquía (idea general)

* `Throwable`

  * `Error` (problemas graves)
  * `Exception`

    * Checked
    * Unchecked (RuntimeException)

## Checked vs Unchecked

* **Checked:** el compilador obliga a manejar o declarar (`IOException`).
* **Unchecked:** errores de programación (`NullPointerException`, `ArithmeticException`).

## Manejo con try–catch–finally

```java
try {
    // código que puede lanzar excepción
} catch (Exception e) {
    // manejo de error
} finally {
    // se ejecuta siempre (haya o no excepción)
}
```

Ejemplo con `throws`:

```java
public class Parser {
    public String parsear(int i) throws Exception {
        if (i < 10) {
            return "si es menor a diez";
        }
        throw new Exception();
    }
}
```

---

# PREGUNTAS TIPO PARCIAL (con respuestas)

### 1. Defina Overriding y Overloading.

**Respuesta:** Overriding es redefinir un método heredado manteniendo la misma firma. Overloading es definir métodos con el mismo nombre pero distinta lista de parámetros.

---

### 2. ¿Qué diferencia hay entre `private` y `protected` en un atributo?

**Respuesta:** `private` solo es accesible dentro de la misma clase. `protected` es accesible por herencia, incluso desde otros paquetes.

---

### 3. ¿Qué pasa si una clase tiene un constructor con parámetros y no se define el constructor por defecto?

**Respuesta:** El compilador **no** genera el constructor sin parámetros y no podrá instanciarse la clase con `new Clase()`.

---

### 4. ¿Puede una clase extender dos clases a la vez? ¿Puede implementar dos interfaces?

**Respuesta:** No puede extender dos clases (no hay herencia múltiple de clases). Sí puede implementar múltiples interfaces.

---

### 5. Explique la diferencia entre una excepción checked y una unchecked.

**Respuesta:** Las checked deben ser declaradas o capturadas (`throws` o `try-catch`). Las unchecked derivan de `RuntimeException` y suelen ser errores de lógica, el compilador no obliga a manejarlas.

---

# APUNTE — Java 4: Sintaxis Básica, Operadores, Control de Flujo y Arreglos

Basado en **java 4.ppt**. Incluye teoría explicada, ejemplos simples y preguntas tipo parcial con sus respuestas.

---

## 1. Primer programa en Java

```java
public class Primero {
    public static void main(String[] args) {
        System.out.println("Hola mundo");
    }
}
```

Puntos clave:

* Solo puede haber **una clase pública** por archivo.
* El archivo debe llamarse **Primero.java** (igual que la clase pública).
* `main` es el punto de entrada de la aplicación.

---

## 2. Comentarios en Java

Sirven para documentar el código y no son ejecutados.

```java
// Comentario de una sola línea

/*
 * Comentario de varias líneas
 */

/**
 * Comentario de documentación (Javadoc)
 */
```

---

## 3. Identificadores

Los **identificadores** nombran variables, métodos, clases, etc.

Reglas:

* Deben comenzar con: **letra**, `_` o `$`.
* No pueden comenzar con número.
* Después del primer carácter, pueden tener letras, números y otros caracteres Unicode.
* Son **case-sensitive**: `Foo` ≠ `foo`.
* No se pueden usar **palabras reservadas** del lenguaje.

Ejemplos válidos:

```java
int edad;
String _nombre;
double $saldo;
```

Ejemplos inválidos:

```java
int 2cosas;    // empieza con número
int class;     // palabra reservada
```

---

## 4. Palabras reservadas (algunas)

`public`, `class`, `static`, `void`, `if`, `else`, `while`, `for`, `switch`, `case`, `break`, `default`, `int`, `double`, `boolean`, `char`, `return`, `try`, `catch`, `finally`, `new`, `this`, `super`, `extends`, `implements`, `interface`.

No se pueden usar como nombres de variables o métodos.

---

## 5. Tipos de variables

### 5.1. Variables primitivas

* `char`
* `boolean`
* `byte`
* `short`
* `int`
* `long`
* `float`
* `double`

### 5.2. Variables de referencia

* Referencian **objetos** (ej: `String`, `Persona`, `Scanner`).

```java
int numero = 10;         // primitivo
String texto = "Hola";  // referencia a un objeto String
```

---

## 6. Tipos primitivos: ejemplos de asignación

```java
char varCaracter = 'c';      // carácter Unicode
boolean varBooleano = false;
byte varByte = 8;            // 8 bits
short varShort = 24;         // 16 bits
int varEntera = 32;          // 32 bits
long varLong = 123456789L;   // 64 bits
float varFloat = 1244f;      // 32 bits
double varDouble = 12345.1234; // 64 bits

String varString = "Hola mundo"; // no es primitivo, es objeto
```

---

## 7. Constantes con `final`

`final` hace que una variable no pueda cambiar de valor después de asignarse.

```java
public class Ejemplo {
    public static void main(String[] args) {
        final int A;
        A = 3;   // primera (y única) asignación válida
        // A = 5; // ERROR: no se puede volver a asignar
    }
}
```

Convención: las constantes suelen escribirse en MAYÚSCULAS:

```java
final int MAX_EDAD = 120;
```

---

## 8. Literales

Son valores escritos directamente en el código.

Ejemplos:

```java
'b'           // char
42            // int
false         // boolean
2546789.343   // double
"Hola"        // String
```

### 8.1. Literales enteros en distintas bases

```java
int cinco = 5;       // decimal
int seis = 006;      // octal (6)
int nueve = 011;     // octal (9)
int x = 0x0001;      // hexadecimal (1)
int y = 0x7fffffff;  // max int positivo
int z = 0xDeadCafe;  // hexadecimal
```

### 8.2. Literales numéricos con sufijos

Por defecto:

* `int` para enteros
* `double` para flotantes

```java
int i = 32;
float f = 32.064F;  // F para float
double d = 32.064D; // D opcional para double
long  l = 32L;      // L para long
```

---

## 9. Casting (conversiones de tipo)

Permite convertir un valor de un tipo en otro.

### 9.1. Casting implícito

Cuando el tipo destino **tiene más capacidad**:

```java
int a = 100;
long b = a; // implícito: int → long
```

### 9.2. Casting explícito

Cuando puede haber **pérdida de información**:

```java
float x = 100.001f;
int y = (int) x;  // 100 (pierde decimales)
```

Ejemplo típico con `byte`:

```java
byte b = 3;
byte c = 8;
// byte d = b + c; // ERROR: resultado es int
byte d = (byte) (b + c); // casting explícito
```

---

## 10. Operadores

### 10.1. Asignación

`=`, `+=`, `-=`, `*=`, `/=`, `%=`

```java
int x = 10;
x += 5;  // x = x + 5 → 15
x -= 2;  // x = x - 2 → 13
```

### 10.2. Aritméticos

`+`, `-`, `*`, `/`, `%` (módulo)

```java
int r = 5 % 2; // 1
```

### 10.3. Incremento / Decremento

`++`, `--`

```java
int c = 0;
System.out.println(c++); // imprime 0, luego c pasa a 1
System.out.println(++c); // incrementa, luego imprime 2
```

### 10.4. Relacionales

`<`, `<=`, `>`, `>=`, `==`, `!=`

Devuelven `boolean`.

### 10.5. Lógicos

`&&`, `||`, `!`, `^`

```java
boolean b = (2 < 3) && (4 > 3); // true
```

Cortocircuito:

* En `A && B`, si `A` es `false`, no evalúa `B`.
* En `A || B`, si `A` es `true`, no evalúa `B`.

### 10.6. Operadores a nivel bit

`&`, `|`, `^` entre enteros.

```java
byte b1 = 6 & 8;
byte b2 = 7 | 9;
byte b3 = 5 ^ 4;
```

### 10.7. Operador ternario

```java
// sintaxis
resultado = condicion ? valorSiTrue : valorSiFalse;

int mascotas = 3;
String estado = (mascotas < 4) ? "numero correcto" : "demasiadas";
```

---

## 11. Precedencia de operadores

* `*` y `/` tienen mayor prioridad que `+` y `-`.
* Se evalúa de **izquierda a derecha**.
* Se pueden usar paréntesis para forzar orden.

```java
int a = 10 + 5 * 2;    // 10 + (5 * 2) = 20
int b = (10 + 5) * 2;  // (10 + 5) * 2 = 30

b *= 2 + 5;  // b = b * (2 + 5)
```

---

## 12. Sentencia `if` y `if-else`

```java
if (x > 3) {
    System.out.println("x es mayor que 3");
} else {
    System.out.println("x no es mayor que 3");
}
```

Sin llaves, solo afecta **la primera sentencia**:

```java
if (x > 3)
    y = 2;
z += 8; // esto se ejecuta SIEMPRE
```

---

## 13. Sentencia `switch`

Útil para muchos `if-else` sobre el mismo valor.

```java
int x = 3;
switch (x) {
    case 1:
        System.out.println("x es 1");
        break;
    case 2:
        System.out.println("x es 2");
        break;
    case 3:
        System.out.println("x es 3");
        break;
    default:
        System.out.println("No sé qué valor es x");
}
```

Reglas:

* En Java clásico, `switch` acepta `byte`, `short`, `char`, `int` y `enum`.
* Los `case` deben ser **constantes** del tipo compatible.
* Cuidado con valores fuera de rango (por ejemplo `byte` y `case 128`).

---

## 14. `while` y `do-while`

### 14.1. `while`

```java
int x = 2;
while (x < 10) {
    System.out.println(x);
    ++x;
}
```

### 14.2. `do-while`

```java
do {
    System.out.println("Dentro del lazo");
} while (!false);
```

* `while` puede no ejecutarse nunca.
* `do-while` se ejecuta **al menos una vez**.

---

## 15. `for`

```java
for (int i = 0; i < 10; i++) {
    System.out.println("i es " + i);
}
```

* 3 partes: inicialización; condición; actualización.
* La condición es obligatoria; las otras dos pueden omitirse.

```java
for (;;) {
    System.out.println("bucle infinito");
}
```

---

## 16. `break` y `continue`

```java
for (int i = 0; i < 7; i++) {
    if (i == 5) {
        break;      // sale del bucle
    }
    if (i == 4) {
        continue;   // salta a la próxima iteración
    }
    // código que se salteará cuando i == 4
}
```

* `break` se usa en bucles y `switch`.
* `continue` solo en bucles.

---

## 17. Alcance de variables (scope)

El **alcance** indica dónde es visible una variable.

```java
for (int x = 40; x > 0; x--) {
    System.out.println("x es " + x);
}

// x = 34; // ERROR: fuera del alcance del for
```

Variables declaradas dentro de un bloque `{ }` solo existen ahí.

---

## 18. Arreglos (arrays)

Un **arreglo** almacena varios valores del mismo tipo.

### 18.1. Declaración

```java
int[] key;      // forma recomendada
int key2[];     // también válida
```

### 18.2. Arreglos multidimensionales

```java
String[][][] arreglo3D; // 3 dimensiones
String[] personal[];    // 2 dimensiones
```

### 18.3. Creación y asignación

```java
int[] a = new int[100]; // índices 0 a 99

for (int i = 0; i < 100; i++) {
    a[i] = i;
}

int longitud = a.length; // cantidad de elementos
```

### 18.4. Inicialización compacta

```java
int[] enterosChicos = {2, 3, 4, 5, 6, 7, 8, 9};

// arreglo anónimo
enterosChicos = new int[] {21, 22, 23, 43, 33, 45, 46, 47};
```

### 18.5. Copia de arreglos con System.arraycopy

```java
int[] from = {1, 2, 3, 4, 5};
int[] to = new int[5];

System.arraycopy(from, 0, to, 0, from.length);
```

### 18.6. Recorrido típico

```java
int[] numeros = new int[100];

for (int i = 0; i < numeros.length; i++) {
    System.out.println("Numero " + i + " es " + numeros[i]);
}
```

---

# PREGUNTAS TIPO PARCIAL (con respuestas)

### 1. ¿Qué diferencia hay entre `while` y `do-while`?

**Respuesta:** `while` puede no ejecutarse nunca si la condición es falsa desde el inicio. `do-while` ejecuta el bloque al menos una vez y luego evalúa la condición.

---

### 2. ¿Qué imprime este código?

```java
int jugadores = 0;
System.out.println("jugadores online: " + jugadores++);
System.out.println("El valor de jugadores es " + jugadores);
System.out.println("El valor de jugadores es ahora " + ++jugadores);
```

**Respuesta:**

* `jugadores online: 0`
* `El valor de jugadores es 1`
* `El valor de jugadores es ahora 2`

---

### 3. Explique el efecto de `break` y `continue` en un bucle.

**Respuesta:** `break` finaliza el bucle y pasa a la siguiente sentencia. `continue` salta el resto del cuerpo del bucle y pasa directamente a la siguiente iteración.

---

### 4. ¿Qué es un arreglo? ¿Cómo se declara e inicializa un arreglo de 5 enteros con los valores 1 a 5?

**Respuesta:** Un arreglo es una estructura que almacena múltiples valores del mismo tipo. Ejemplo:

```java
int[] a = {1, 2, 3, 4, 5};
```

---

### 5. ¿Qué diferencia hay entre una variable primitiva y una de referencia?

**Respuesta:** La primitiva almacena directamente el valor (ej: `int`, `double`), mientras que la de referencia almacena una dirección o referencia a un objeto en memoria (ej: `String`, `Persona`).

---

# APUNTE — Java 5: Entrada/Salida (I/O), Streams y Serialización

Basado en el archivo de cátedra **java 5** (UTN – Programación II). Apunte pensado para entender bien la teoría + ver código real + tener material tipo parcial.

---

## 1. Concepto de Stream (Flujo)

Un **stream** es un *flujo de datos* que viaja en una dirección:

* Puede ser de **bytes** (binario) o de **caracteres** (texto).
* Permite:

  * Leer/escribir archivos.
  * Enviar/recibir datos por red.
  * Comunicar un programa con otro recurso externo.

Tipos principales:

* `InputStream` → flujo de **entrada** (leer datos).
* `OutputStream` → flujo de **salida** (escribir datos).

Hay dos "familias":

* **Flujos de bytes** → `InputStream` / `OutputStream` y derivados.
* **Flujos de caracteres** → `Reader` / `Writer` y derivados.

---

## 2. Clases para Flujo de Caracteres

Las principales clases para trabajar con **texto** son:

* `File` → representa rutas, archivos, directorios (no lee ni escribe por sí mismo).
* `FileReader` → lee caracteres desde un archivo.
* `BufferedReader` → envuelve a un `Reader` para hacerlo más eficiente y permitir leer por líneas.
* `FileWriter` → escribe caracteres en un archivo.
* `BufferedWriter` → envuelve a un `Writer` para mejorar rendimiento y dar métodos cómodos (`newLine()`).

### 2.1. Clase `File`

`java.io.File` no es el archivo en sí, sino un **objeto que representa la ruta**.

Ejemplo:

```java
import java.io.*;

class Writer1 {
    public static void main(String[] args) {
        try {
            boolean newFile = false;
            File file = new File("fileWrite1.txt"); // solo crea el objeto File

            System.out.println(file.exists());       // ¿ya existe el archivo?

            newFile = file.createNewFile();          // crea el archivo (si no existía)

            System.out.println(newFile);             // true si se creó
            System.out.println(file.exists());       // ahora debería ser true
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

Métodos útiles de `File`:

* `exists()`
* `createNewFile()`
* `getAbsoluteFile()` / `getCanonicalFile()`
* `getName()` / `getPath()`
* `canRead()`, `canWrite()`, `canExecute()`
* `isDirectory()`, `isHidden()`
* `renameTo(File nuevo)`

---

## 3. Flujo de Bytes: `FileInputStream` y `FileOutputStream`

Se usan para leer/escribir datos binarios (imágenes, binarios, etc.) o texto a nivel byte.

Ejemplo tipo *copiar archivo* simplificado:

```java
import java.io.*;

public class CopyBytes {
    public static void main(String[] args) throws IOException {
        FileInputStream in = null;
        FileOutputStream out = null;
        File f = null;
        try {
            f = new File("prueba.txt");
            f.createNewFile();

            in = new FileInputStream(f);        // leer bytes desde archivo
            out = new FileOutputStream(f);      // escribir bytes al mismo archivo

            out.write("linea 1 \n".getBytes());
            out.write("linea 2 \n".getBytes());

            out = new FileOutputStream("outagain.txt"); // destino copia
            int c;
            while ((c = in.read()) != -1) {      // lee byte a byte
                out.write(c);                    // escribe en archivo destino
            }
        } finally {
            if (in != null) in.close();
            if (out != null) out.close();
        }
    }
}
```

Puntos clave:

* `read()` devuelve un `int` con el byte leído o `-1` si terminó el stream.
* Siempre cerrar los streams en `finally` (o usar `try-with-resources` en Java moderno).

---

## 4. Flujo de Caracteres con Buffer: `BufferedReader` y `BufferedWriter`

Trabajar **línea por línea** con texto es mucho más cómodo con estas clases.

```java
import java.io.*;

class Prueba {
    public static void main(String[] args) throws IOException {
        BufferedReader in = null;
        BufferedWriter out = null;
        try {
            File f = new File("prueba.txt");
            f.createNewFile();

            in = new BufferedReader(new FileReader(f));
            out = new BufferedWriter(new FileWriter(f));

            // Escribimos en el archivo
            out.write("linea 1");
            out.newLine();
            out.write("linea 2");
            out.close(); // cerramos para que se guarde

            // Ahora copiamos a otro archivo
            out = new BufferedWriter(new FileWriter("otro.txt"));
            String aux;
            while ((aux = in.readLine()) != null) {
                System.out.println(aux); // mostramos en consola
                out.write(aux);          // copiamos
                out.newLine();
            }
        } catch (Exception e) {
            e.printStackTrace();
        } finally {
            if (in != null) in.close();
            if (out != null) out.close();
        }
    }
}
```

Métodos importantes:

* `readLine()` en `BufferedReader`.
* `write(String)` y `newLine()` en `BufferedWriter`.

---

## 5. Ejemplo combinado: escribir y leer caracteres

```java
class Writer2 {
    public static void main(String[] args) {
        char[] in = new char[50];  // buffer de entrada
        int size = 0;
        try {
            File file = new File("fileWrite2.txt");
            FileWriter fw = new FileWriter(file);

            fw.write("Hola a\n todos esto es una prueba\n");
            fw.flush();
            fw.close();

            FileReader fr = new FileReader(file);
            size = fr.read(in);    // lee caracteres al arreglo

            System.out.print(size + " ");
            for (char c : in) {
                System.out.print(c);
            }
            fr.close();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

Idea: se escribe texto al archivo, luego se lo lee y se muestra lo que se leyó.

---

## 6. Serialización

La **serialización** permite **convertir un objeto en bytes** para:

* Guardarlo en un archivo.
* Enviarlo por red.
* Persistir su estado y restaurarlo después.

Para que una clase sea serializable debe:

* Implementar la interfaz `java.io.Serializable`.
* No definir lógica especial (es una *marker interface*, solo marca la clase).

```java
import java.io.Serializable;

class Alumno implements Serializable {
    public String nombre;
    public String apellido;
}
```

---

### 6.1. El modificador `transient`

Si un atributo se marca como `transient`, **no se serializa**.

```java
public class Cliente implements java.io.Serializable {
    private String nombre;
    private transient String passWord; // no se guarda

    public Cliente(String nombre, String pw) {
        this.nombre = nombre;
        passWord = pw;
    }

    public String toString() {
        String texto = (passWord == null) ? "(no disponible)" : passWord;
        texto += nombre;
        return texto;
    }
}
```

Cuando se deserializa un objeto `Cliente`, `passWord` será `null`.

---

## 7. Ejemplo completo de Serialización con objetos

### Clase `Perro` serializable

```java
import java.io.Serializable;

public class Perro implements Serializable {
    private String nombre;
    private String raza;

    public Perro(String nombre, String raza) {
        this.nombre = nombre;
        this.raza = raza;
    }

    public String getRaza() { return raza; }
    public void setRaza(String raza) { this.raza = raza; }

    public String getNombre() { return nombre; }
    public void setNombre(String nombre) { this.nombre = nombre; }

    public String toString() {
        return "Perro: " + this.nombre + " Raza: " + this.raza;
    }
}
```

### Serializar y deserializar un array de Perro

```java
import java.io.*;

public class TestPerros {
    public static void main(String[] args) throws IOException {
        ObjectInputStream in = null;
        ObjectOutputStream out = null;

        Perro[] p = {
            new Perro("Sultan", "Ovj. Aleman"),
            new Perro("Pinky", "Caniche"),
            new Perro("Otro", "Otro")
        };

        try {
            File f = new File("perros.txt");
            f.createNewFile();

            // Serializar
            out = new ObjectOutputStream(new FileOutputStream(f));
            for (Perro aux : p) {
                out.writeObject(aux);
            }

            // Deserializar
            in = new ObjectInputStream(new FileInputStream(f));
            for (int i = 0; i < 3; i++) {
                Perro aux = (Perro) in.readObject();
                System.out.println(aux);
            }
        } catch (Exception e) {
            e.printStackTrace();
        } finally {
            if (in != null) in.close();
            if (out != null) out.close();
        }
    }
}
```

Puntos clave:

* Se usa `ObjectOutputStream` para escribir objetos.
* Se usa `ObjectInputStream` para leer objetos.
* Es necesario castear el resultado de `readObject()`.

---

# PREGUNTAS TIPO PARCIAL (con respuestas)

### 1. ¿Qué diferencia hay entre `File` y `FileInputStream`?

**Respuesta:** `File` representa la ruta de un archivo o directorio; no lee ni escribe. `FileInputStream` es un flujo de entrada que permite leer bytes de un archivo.

---

### 2. Mencione dos diferencias entre `FileInputStream` y `FileReader`.

**Respuesta:** `FileInputStream` trabaja con bytes (binario), `FileReader` con caracteres (texto). `FileReader` respeta el encoding de caracteres; `FileInputStream` no interpreta caracteres.

---

### 3. ¿Qué hace el modificador `transient` en un atributo de una clase serializable?

**Respuesta:** Evita que el atributo sea serializado. Al deserializar, su valor será el valor por defecto (por ejemplo `null`).

---

### 4. ¿Por qué hay que cerrar los streams en un bloque `finally`?

**Respuesta:** Para garantizar que el recurso se libere siempre, incluso si ocurre una excepción durante lectura/escritura.

---

### 5. ¿Qué métodos de clases se usan para serializar y deserializar objetos?

**Respuesta:** Se usan objetos de `ObjectOutputStream` con `writeObject()` para serializar, y `ObjectInputStream` con `readObject()` para deserializar.

---

# APUNTE — Java 6: Hilos (Threads) y Programación Concurrente

Basado en el archivo **java6.ppt** de Programación II (UTN). Apunte pensado para entender bien la teoría de hilos en Java, con ejemplos claros y preguntas tipo parcial.

---

## 1. ¿Qué es un hilo (Thread)?

La **programación concurrente** permite que varias tareas parezcan ejecutarse al mismo tiempo, aprovechando mejor el CPU.

En Java, un **hilo** (*thread*):

* Es un **proceso ligero** que se ejecuta dentro de un programa.
* Tiene **su propia pila de llamadas (call stack)**.
* Comparte memoria con otros hilos del mismo proceso.

En Java los hilos son dos cosas a la vez:

1. **Un objeto de la clase `java.lang.Thread`** → vive en el heap como cualquier objeto.
2. **Un flujo de ejecución** real en el CPU.

Cuando hablamos de “crear un hilo” normalmente queremos decir:

* Crear un objeto `Thread` asociado a un bloque de código (`run()`), y
* Ponerlo a correr llamando a `start()`.

---

## 2. Formas de definir un hilo en Java

Hay **dos formas clásicas** de definir la lógica de un hilo:

1. **Extendiendo la clase `Thread`**
2. **Implementando la interfaz `Runnable`**

---

### 2.1. Extender `Thread`

```java
class MyThread extends Thread {
    @Override
    public void run() {
        System.out.println("Important job running in MyThread");
    }
}
```

Características:

* Es simple de escribir.
* La lógica del hilo se define en el método `run()`.
* Limitación: **ya estás heredando de `Thread`**, no podés heredar de otra clase.

---

### 2.2. Implementar `Runnable`

```java
class MyRunnable implements Runnable {
    @Override
    public void run() {
        System.out.println("Important job running in MyRunnable");
    }
}
```

Características:

* Es más **flexible** que extender `Thread`.
* Podés heredar de otra clase y a la vez implementar `Runnable`.
* Es la forma **más recomendada** en diseños grandes.

---

## 3. Instanciar un hilo

### 3.1. Cuando extendés `Thread`

```java
MyThread t = new MyThread();
// todavía no se está ejecutando, solo está creado
```

### 3.2. Cuando implementás `Runnable`

Hay un paso extra: tenés que crear el `Runnable` y luego pasarlo al constructor de `Thread`.

```java
MyRunnable r = new MyRunnable();
Thread t = new Thread(r); // asociás el runnable al hilo
```

Ejemplo con varios hilos que comparten el mismo `Runnable`:

```java
public class TestThreads {
    public static void main(String[] args) {
        MyRunnable r = new MyRunnable();
        Thread foo = new Thread(r);
        Thread bar = new Thread(r);
        Thread bat = new Thread(r);
        // en este ejemplo aún no se llaman a start()
    }
}
```

---

## 4. Iniciar un hilo: `start()` vs `run()`

Para que el hilo **empiece realmente a ejecutarse**, hay que llamar a `start()`:

```java
class FooRunnable implements Runnable {
    @Override
    public void run() {
        for (int x = 1; x < 6; x++) {
            System.out.println("Runnable running");
        }
    }
}

public class TestThreads {
    public static void main(String[] args) {
        FooRunnable r = new FooRunnable();
        Thread t = new Thread(r);
        t.start(); // ¡acá arranca el hilo!
    }
}
```

🔴 **Cuidado:** llamar a `run()` directamente **no** inicia un hilo nuevo; se ejecuta en el mismo hilo que el `main`. El método correcto siempre es `start()`.

---

## 5. El hilo `main`

Cuando arranca un programa Java, ya existe un hilo llamado `main`:

```java
public class NameThreadTwo {
    public static void main(String[] args) {
        System.out.println("thread is " + Thread.currentThread().getName());
    }
}
```

Salida típica:

```text
thread is main
```

* Los programas que sólo ejecutan lógica dentro de `main` se consideran **monohilo**.
* Cuando creás otros `Thread` y llamás a `start()`, ya estás en un programa **multihilo**.

---

## 6. Nombres de hilos y varios hilos en paralelo

Podés darle nombre a los hilos para identificar quién está ejecutando qué:

```java
class NameRunnable implements Runnable {
    @Override
    public void run() {
        System.out.println("NameRunnable running");
        System.out.println("Run by " + Thread.currentThread().getName());
    }
}

public class NameThread {
    public static void main(String[] args) {
        NameRunnable nr = new NameRunnable();
        Thread t = new Thread(nr);
        t.setName("Fred");
        t.start();
    }
}
```

### Varios hilos ejecutando el mismo `Runnable`

```java
class NameRunnable implements Runnable {
    @Override
    public void run() {
        for (int x = 1; x <= 3; x++) {
            System.out.println("Run by "
                    + Thread.currentThread().getName()
                    + ", x is " + x);
        }
    }
}

public class ManyNames {
    public static void main(String[] args) {
        NameRunnable nr = new NameRunnable();
        Thread one = new Thread(nr);
        Thread two = new Thread(nr);
        Thread three = new Thread(nr);

        one.setName("Fred");
        two.setName("Lucy");
        three.setName("Ricky");

        one.start();
        two.start();
        three.start();
    }
}
```

* Los tres hilos ejecutan el **mismo código** (`run()`), pero el orden en que aparecen los mensajes puede **variar** entre ejecuciones.

---

## 7. Planificador de hilos (Thread Scheduler)

Dentro de la JVM existe un **planificador de hilos** que decide:

* Qué hilo se ejecuta en cada momento.
* Cuándo se pausa uno para darle lugar a otro.

No lo controlamos directamente, pero podemos **influenciar** su comportamiento con métodos de `Thread`:

* `sleep(long millis)`
* `yield()`
* `join()`
* `setPriority(int newPriority)`

---

## 8. Estados de un hilo

Estados típicos de un hilo en Java:

* **New** → se creó el objeto `Thread` pero no se llamó `start()`.
* **Runnable** → luego de `start()`, el hilo está listo para ejecutar.
* **Running** → el hilo está efectivamente usando CPU ejecutando `run()`.
* **Waiting / Blocked** → el hilo espera:

  * I/O,
  * que pase cierto tiempo (`sleep`),
  * o algún otro evento.
* **Dead (Terminated)** → terminó la ejecución de `run()`.

---

## 9. Dormir un hilo: `sleep()`

Sirve para **pausar** el hilo actual por cierto tiempo.

```java
try {
    Thread.sleep(5 * 60 * 1000); // 5 minutos
} catch (InterruptedException ex) {
    // manejo si alguien interrumpe el hilo mientras duerme
}
```

### Ejemplo con varios hilos durmiendo

```java
class NameRunnable implements Runnable {
    @Override
    public void run() {
        for (int x = 1; x < 4; x++) {
            System.out.println("Run by " + Thread.currentThread().getName());
            try {
                Thread.sleep(1000); // duerme 1 segundo
            } catch (InterruptedException ex) {
                // ignoramos la interrupción en este ejemplo
            }
        }
    }
}

public class ManyNames {
    public static void main(String[] args) {
        NameRunnable nr = new NameRunnable();

        Thread one = new Thread(nr);
        one.setName("Fred");

        Thread two = new Thread(nr);
        two.setName("Lucy");

        Thread three = new Thread(nr);
        three.setName("Ricky");

        one.start();
        two.start();
        three.start();
    }
}
```

---

## 10. Prioridades de hilos

Cada hilo tiene una **prioridad**, que es un número entero.

* Dependiendo de la JVM, el rango típico es de **1 a 10** (o 1 a 5 en algunos entornos).
* Un hilo con mayor prioridad **tiene más chances** de ser elegido para ejecutar.

```java
FooRunnable r = new FooRunnable();
Thread t = new Thread(r);
t.setPriority(8);
t.start();
```

⚠️ Importante: la prioridad **no garantiza** el orden exacto de ejecución, sólo influye.

---

## 11. Métodos `yield()` y `join()`

### 11.1. `yield()`

* Es un método estático de `Thread`.
* Indica que el hilo **cede voluntariamente** la CPU, permitiendo que otros hilos de igual prioridad se ejecuten.

No garantiza nada, es sólo una sugerencia al planificador.

### 11.2. `join()`

* Es un método **de instancia**.
* Hace que el hilo que llama a `join()` **espere** a que otro hilo termine.

Ejemplo:

```java
Thread t = new Thread();
t.start();
t.join(); // el hilo actual espera hasta que t termine
```

Ejemplo más completo:

```java
Runnable run1 = new Runnable() {
    public void run() {
        try {
            System.out.println("Run 1");
            Thread.sleep(1000);
        } catch (InterruptedException ex) { }
    }
};

final Thread t1 = new Thread(run1);

Runnable run2 = new Runnable() {
    public void run() {
        try {
            t1.join(); // espera a que termine t1
        } catch (InterruptedException ex) { }
        System.out.println("Run 2 después de un segundo");
    }
};

final Thread t2 = new Thread(run2);

t2.start();
t1.start();
```

---

## 12. Sincronización de métodos (`synchronized`)

Cuando varios hilos acceden al **mismo objeto** y modifican su estado, se pueden producir **condiciones de carrera** (race conditions).

La **sincronización** garantiza que sólo **un hilo por vez** ejecute un método crítico.

* Se usa la palabra clave `synchronized` para marcar métodos o bloques.
* Sólo métodos (o bloques de código) pueden ser sincronizados.
* No es obligatorio sincronizar *todo*, sólo lo que pueda causar inconsistencias.

Ejemplo básico:

```java
public class Contador {
    private int valor = 0;

    public synchronized void incrementar() {
        valor++; // este bloque es atómico respecto a otros hilos
    }

    public int getValor() {
        return valor;
    }
}
```

En este ejemplo, dos hilos que llamen `incrementar()` no podrán ejecutar al mismo tiempo ese método sobre el **mismo objeto** `Contador`.

---

# PREGUNTAS TIPO PARCIAL (con respuestas)

### 1. Nombre las dos formas de crear hilos en Java y dé un ejemplo de cada una.

**Respuesta:**

1. Extender `Thread`:

   ```java
   class MiHilo extends Thread {
       public void run() { /* código */ }
   }
   ```
2. Implementar `Runnable` y pasarlo a un `Thread`:

   ```java
   class MiTarea implements Runnable {
       public void run() { /* código */ }
   }
   Thread t = new Thread(new MiTarea());
   ```

---

### 2. ¿Cuál es la diferencia entre llamar `run()` y `start()` sobre un hilo?

**Respuesta:** `run()` ejecuta el código en el **mismo hilo** que llama al método (no crea concurrencia). `start()` crea un **nuevo hilo de ejecución** y dentro de él la JVM invoca a `run()`.

---

### 3. Mencione al menos tres estados por los que puede pasar un hilo.

**Respuesta:** `New`, `Runnable`, `Running`, `Waiting/Blocked`, `Dead`.

---

### 4. ¿Para qué se utilizan los métodos `sleep()` y `join()`?

**Respuesta:** `sleep()` pausa el hilo actual por un tiempo determinado. `join()` hace que un hilo espere a que otro hilo termine su ejecución antes de continuar.

---

### 5. ¿Qué problema resuelve la palabra clave `synchronized`?

**Respuesta:** Evita que varios hilos ejecuten al mismo tiempo un método o bloque crítico sobre el mismo objeto, previniendo **condiciones de carrera** y estados inconsistentes.

---

# APUNTE — Java 7: Igualdad entre Objetos, Colecciones (Collections), Generics y Métodos Importantes de List/Set

Basado en el archivo **java 7.ppt**. Incluye teoría UTN, ejemplos claros, comentarios pedagógicos y preguntas tipo parcial.

---

# 1. Igualdad entre Objetos: `==` vs `equals()`

Uno de los errores más comunes en Java es confundir:

* **`==`** → compara **referencias** (dirección en memoria)
* **`equals()`** → compara **contenido** (si está correctamente sobrescrito)

### Ejemplo con `==` y `equals()` sin sobrescribir

```java
class Shape { }

public class TestShapes {
    public static void main(String[] args) {
        Shape s1 = new Shape();
        Shape s2 = new Shape();

        System.out.println(s1 == s2);      // false → son objetos distintos
        System.out.println(s1.equals(s2)); // false → usa equals() heredado de Object
    }
}
```

El método `equals()` heredado de `Object` es equivalente a `==` (compara referencias).

---

## 1.1. Sobrescribiendo `equals()` correctamente

Para que dos objetos puedan compararse por su **contenido**, hay que sobreescribir `equals()`.

Ejemplo:

```java
public class Car {    
    private String color;
    private String name;

    public Car(String color, String name) {
        this.color = color;
        this.name = name;
    }

    public boolean equals(Object o) {
        if (!(o instanceof Car)) return false;
        Car c = (Car) o;
        return color.equals(c.color) && name.equals(c.name);    
    }
}
```

### Uso:

```java
Car s1 = new Car("white", "toyota");
Car s2 = new Car("white", "toyota");
System.out.println(s1.equals(s2)); // true
```

---

# 2. Colecciones: List

Una **Lista (`List`)** es una colección **ordenada**, que permite elementos duplicados.

Las implementaciones más comunes:

* **ArrayList** (la más usada)
* LinkedList
* Vector (antigua / sincronizada)

---

## 2.1. Ejemplo sobre métodos de List

```java
import java.util.List;
import java.util.ArrayList;

public class PruebaListas {
    public static void main(String[] args) {
        List<String> arl = new ArrayList<String>();

        arl.add("Java");
        arl.add("Perl");
        arl.add("PHP");  // arl = [Java, Perl, PHP]

        System.out.println(arl.contains("Java"));  // true
        System.out.println(arl.get(1));             // Perl
        System.out.println(arl.indexOf("Java"));   // 0

        arl.remove("Java");        // borra el objeto "Java"
        System.out.println(arl.size()); // 2
    }
}
```

### Métodos importantes de List

* `add(E elem)`
* `remove(Object o)` o `remove(int index)`
* `get(index)`
* `contains(obj)`
* `size()`
* `indexOf(obj)`
* `clear()`

---

# 3. Clases Wrapper (repaso rápido)

Las colecciones **no aceptan tipos primitivos**. Por eso se usan las *wrapper classes*:

* `Integer`, `Double`, `Float`, `Long`, `Boolean`, etc.

Ejemplo:

```java
List<Integer> nums = new ArrayList<Integer>();
nums.add(1);
nums.add(2);
```

---

# 4. Generics

Los **generics** permiten parametrizar clases y colecciones con un tipo seguro.

Ejemplo sin generics (Java viejo):

```java
List list = new ArrayList();
list.add("Hello");
list.add(new Integer(17)); // error en runtime, no en compilación
```

### Con generics

```java
List<String> list = new ArrayList<String>();
list.add("Hello");
// list.add(new Integer(17)); // error en compilación
```

Beneficios:

* Mayor seguridad en tiempo de compilación.
* Evita castings innecesarios.
* Código más legible.

---

# 5. Otros ejemplos importantes de List

### 5.1. remove(index) vs remove(obj)

```java
List<String> arl = new ArrayList<String>();
arl.add("Java");
arl.add("Perl");
arl.add("PHP");

arl.remove("Java"); // borra el objeto
arl.remove(0);       // borra por índice
```

---

## 5.2. El método `equals()` en colecciones

Cuando usás métodos como:

* `contains(obj)`
* `remove(obj)`
* `indexOf(obj)`

Java usa **equals()** para comparar elementos. Si no está bien sobrescrito, no va a encontrarlos.

Ejemplo:

```java
List<Alumno> lista = new ArrayList<>();
lista.add(new Alumno("Ana", 123));
lista.add(new Alumno("Luis", 456));

Alumno buscado = new Alumno("Ana", 123);
lista.contains(buscado); // → false si equals() no está sobreescrito
```

---

# 6. Sets (Conjuntos)

Un **Set**:

* NO permite duplicados.
* No garantiza orden (HashSet) o lo ordena por árbol (TreeSet).

### Ejemplo:

```java
import java.util.*;

public class TestSet {
    public static void main(String[] args) {
        Set<String> s = new HashSet<String>();
        s.add("Hola");
        s.add("Chao");
        s.add("Si");
        s.add("Si"); // duplicado, no se agrega

        System.out.println("Mi Set contiene: " + s);
    }
}
```

---

# 7. HashSet y el método `hashCode()`

Para que un HashSet funcione correctamente con objetos propios, hay que **sobreescribir `equals()` y `hashCode()`**.

Regla: si dos objetos son iguales según `equals()`, **deben** tener el mismo `hashCode()`.

Ejemplo simple:

```java
public class Alumno {
    private int dni;
    private String nombre;

    public boolean equals(Object o) {
        if (!(o instanceof Alumno)) return false;
        Alumno a = (Alumno) o;
        return this.dni == a.dni;
    }

    public int hashCode() {
        return dni * 31; // típica fórmula simple
    }
}
```

---

# 8. Iteración sobre colecciones

Java permite recorrer una colección de varias formas.

### 8.1. For-each

```java
for (String x : lista) {
    System.out.println(x);
}
```

### 8.2. Con Iterator (forma clásica)

```java
Iterator<String> it = lista.iterator();
while (it.hasNext()) {
    System.out.println(it.next());
}
```

---

# 9. Preguntas Clave de Colecciones

* Las colecciones guardan **referencias**, no objetos físicos.
* No se puede hacer `new List()`, porque List es **interfaz**.
* `ArrayList` permite índices, `Set` no.
* `HashSet` no mantiene orden.
* `ArrayList` permite duplicados.

---

# PREGUNTAS TIPO PARCIAL (con respuestas)

## 1. ¿Qué diferencia hay entre `==` y `equals()`?

**Respuesta:** `==` compara referencias (misma ubicación en memoria). `equals()` compara contenido si está sobrescrito correctamente.

---

## 2. ¿Qué método usa `ArrayList.contains()` para comparar objetos?

**Respuesta:** Usa internamente `equals()`.

---

## 3. ¿Por qué `HashSet` requiere sobrescribir `hashCode()` además de `equals()`?

**Respuesta:** Porque agrupa objetos en buckets usando hash. Si dos objetos son iguales según `equals()`, deben tener el mismo hashCode para ubicarse en el mismo bucket.

---

## 4. ¿Qué diferencia hay entre `remove(0)` y `remove("Java")` en una Lista?

**Respuesta:** `remove(0)` borra el elemento en el índice 0; `remove("Java")` busca un objeto igual a “Java” usando `equals()`.

---

## 5. ¿Puede un Set tener elementos duplicados? ¿Por qué?

**Respuesta:** No. Set se basa en `equals()` y `hashCode()` para evitar duplicados.

---

🔵 UNIDAD 1 — Introducción a Java, JVM, Bytecode, JDK/JRE
1. ¿Qué diferencia hay entre JDK y JRE?

Respuesta:

JDK incluye el compilador y herramientas de desarrollo.

JRE solo ejecuta aplicaciones Java, no compila.

2. ¿Qué es la JVM y qué ejecuta?

Respuesta:
La JVM es la máquina virtual que ejecuta bytecode (.class) y hace que Java sea multiplataforma.

3. ¿Qué significa “Write Once, Run Anywhere”?

Respuesta:
Que Java compila una vez a bytecode y se ejecuta en cualquier plataforma con una JVM.

4. Explique el proceso de compilación y ejecución de un programa Java.

Respuesta:

Escribir .java

Compilar → javac → .class

Ejecutar → java + JVM carga el bytecode

5. ¿Qué método debe tener todo programa Java para ejecutarse?

Respuesta:
public static void main(String[] args)

🔵 UNIDAD 2 — Sintaxis básica, tipos, operadores, control de flujo
6. ¿Qué diferencia hay entre una variable primitiva y una de referencia?

Respuesta:
La primitiva almacena directamente el valor, la referencia guarda la dirección a un objeto en memoria.

7. ¿Qué imprime este código?
int jugadores = 0;
System.out.println(jugadores++);
System.out.println(++jugadores);


Respuesta:
0
2

8. Explique break y continue.

Respuesta:

break corta el bucle.

continue salta a la siguiente iteración.

9. ¿Cuál es la diferencia entre == y !=?

Respuesta:
Son operadores relacionales:

== compara igualdad de valores

!= compara desigualdad

10. ¿Qué sucede si a un switch(byte) le pones un case 200?

Respuesta:
Error de compilación: 200 está fuera del rango de byte.

11. ¿Cuál es la diferencia entre while y do-while?

Respuesta:

while evalúa antes de ejecutar

do-while ejecuta al menos una vez

🔵 UNIDAD 3 — POO: clase, objeto, encapsulamiento, herencia, polimorfismo
12. Defina clase y objeto.

Respuesta:

Clase: un molde.

Objeto: una instancia real del molde.

13. ¿Qué es encapsulación?

Respuesta:
Ocultar atributos usando private y acceder mediante getters/setters.

14. ¿Qué es polimorfismo? Dé un ejemplo.

Respuesta:
Capacidad de un método de comportarse distinto según el objeto.

Ejemplo:

Animal a = new Perro();
a.hablar(); // “Guau”

15. ¿Qué pasa si redefinís un método pero cambiás los parámetros?

Respuesta:
Eso es overloading, NO overriding.

16. ¿Puede una clase Java extender dos clases? ¿Puede implementar dos interfaces?

Respuesta:

Extender 2 clases → NO

Implementar muchas interfaces → SÍ

🔵 UNIDAD 4 — Modificadores, this/super, abstract, final, constructores
17. ¿Qué significa que una clase sea final?

Respuesta:
Que no puede ser heredada.

18. ¿Qué diferencia hay entre this y super?

Respuesta:

this: referencia al objeto actual.

super: referencia a la superclase.

19. ¿Qué pasa si una clase declara un constructor con parámetros y no define el constructor vacío?

Respuesta:
El compilador no genera el constructor por defecto.

20. ¿Qué significa que un método sea abstract?

Respuesta:
Debe ser implementado por las subclases; la clase no se puede instanciar.

🔵 UNIDAD 5 — Interfaces
21. Diferencia entre interface y clase abstracta.

Respuesta:

Interface → solo define métodos (hasta Java 7).

Abstracta → puede tener métodos abstractos + concretos + atributos.

22. ¿Puede una interfaz extender otra interfaz?

Respuesta:
Sí, interfaces pueden extender múltiples interfaces.

23. ¿Puede una interfaz implementar otra interfaz?

Respuesta:
NO, solo puede EXTENDER, no IMPLEMENTAR.

🔵 UNIDAD 6 — Hilos (Threads)
24. ¿Qué diferencia hay entre llamar run() y start()?

Respuesta:

run() → se ejecuta en el hilo actual.

start() → crea un hilo nuevo y ejecuta run() dentro de él.

25. Nombre los estados de un hilo.

Respuesta:
New – Runnable – Running – Blocked/Waiting – Dead

26. ¿Para qué sirve join()?

Respuesta:
Hace que un hilo espere a que otro termine.

27. ¿Qué pasa si dos hilos acceden a la misma variable sin sincronizar?

Respuesta:
Condición de carrera (inconsistencia de datos).

28. ¿Para qué sirve synchronized?

Respuesta:
Bloquea un método o bloque para que un solo hilo lo ejecute a la vez.

🔵 UNIDAD 7 — Colecciones (List, Set), equals(), hashCode(), Generics
29. ¿Qué compara == en objetos?

Respuesta:
La referencia, no el contenido.

30. ¿Qué método usa ArrayList.contains() para buscar elementos?

Respuesta:
equals().

31. ¿Por qué es obligatorio sobrescribir hashCode() cuando sobrescribís equals()?

Respuesta:
Porque colecciones como HashSet y HashMap usan ambos métodos para ubicar elementos.

32. ¿Qué diferencia hay entre List y Set?

Respuesta:

List → ordenada, permite duplicados.

Set → no permite duplicados, no garantiza orden (HashSet).

33. ¿Qué diferencia hay entre remove(0) y remove(“Java”)?

Respuesta:

remove(0) → elimina por índice.

remove(“Java”) → busca un objeto igual a “Java” usando equals().

34. ¿Qué es un Generic? ¿Por qué se usa?

Respuesta:
Permite definir colecciones tipadas:
List<String> lista = new ArrayList<>();
Evita castings y errores en runtime.

🔥 PREGUNTAS CRUZADAS (LAS MÁS PELIGROSAS EN PARCIALES)
35. ¿Puede un ArrayList<Perro> contener un Gato si ambos heredan de Animal?

Respuesta:
NO, el tipo genérico debe coincidir exactamente.

36. ¿Qué imprime este código?
String x = "Hola";
x.concat(" Mundo");
System.out.println(x);


Respuesta:
Hola → porque String es inmutable.

37. ¿Qué pasa si intentás hacer new List()?

Respuesta:
Error. List es una interfaz, no se puede instanciar.

38. ¿Por qué conviene usar Runnable en vez de extender Thread?

Respuesta:
Porque Java no soporta herencia múltiple y Runnable permite heredar de otra clase.

39. ¿Qué diferencia hay entre File y FileInputStream?

Respuesta:

File → representa ruta

FileInputStream → lee bytes del archivo

40. ¿Qué hace transient en la serialización?

Respuesta:
Evita que un atributo sea serializado.

🔥 BONUS: PREGUNTAS TRAMPA QUE SUELE TOMAR UTN
41. ¿Puede una clase abstracta NO contener métodos abstractos?

Respuesta:
Sí.

42. ¿Puede un objeto Thread reejecutar start() después de haber terminado?

Respuesta:
NO, lanza IllegalThreadStateException.

43. ¿Puede una interfaz tener atributos?

Respuesta:
Sí, pero son:
public static final por defecto.

44. ¿Qué imprime esto?
Integer a = new Integer(128);
Integer b = new Integer(128);
System.out.println(a == b);


Respuesta:
false → referencias distintas.

45. ¿Por qué HashSet no permite duplicados?

Respuesta:
Por la combinación de equals() y hashCode().


🔷 UNIDAD 4 — (50 PREGUNTAS)
Modificadores, Constructores, this, super, abstract, final
🔹 CONSTRUCTORES (1–15)

¿Qué es un constructor en Java?
R: Un método especial que inicializa un objeto.

¿Puede un constructor tener tipo de retorno?
R: No, ni siquiera void.

¿Qué pasa si una clase NO tiene constructor declarado?
R: El compilador genera uno por defecto.

¿Qué pasa si la clase define un constructor con parámetros?
R: El compilador ya NO genera el constructor vacío.

¿Los constructores pueden ser private?
R: Sí (por ejemplo en patrones Singleton).

¿Puede una clase tener múltiples constructores?
R: Sí, mediante overloading.

¿Se puede llamar un constructor desde otro constructor?
R: Sí, usando this().

¿Un constructor puede llamar a super()?
R: Sí, y debe ser la primera línea.

¿Qué pasa si super() no está explícito?
R: El compilador inserta super() automático.

¿Puede un constructor ser abstracto?
R: No.

¿Puede un constructor ser static?
R: No.

¿Puede un constructor lanzar excepciones?
R: Sí.

¿Puede un constructor estar sobrecargado?
R: Sí.

¿Puede un constructor llamar a métodos?
R: Sí, pero con cuidado: los atributos pueden no estar inicializados.

¿Puede una interfaz tener constructor?
R: No.

🔹 MODIFICADORES (16–25)

¿Qué significa public en un atributo?
R: Es accesible desde cualquier clase.

¿Qué significa private?
R: Solo accesible desde la misma clase.

¿Qué significa protected?
R: Accesible desde el mismo paquete o subclases.

¿Qué significa “default” (sin escribir nada)?
R: Accesible únicamente dentro del mismo paquete.

¿Un método private se hereda?
R: Se hereda pero NO es accesible.

¿Puede un método public ser sobreescrito como private?
R: No, porque reduce visibilidad.

¿Puede un método private ser overrideado?
R: No, porque no es visible.

¿Puede un método final ser overrideado?
R: No.

¿Puede una clase final ser heredada?
R: No.

¿Puede un método static ser overrideado?
R: No, se oculta (shadowing).

🔹 ABSTRACT y FINAL (26–40)

¿Qué es una clase abstracta?
R: Una clase que no puede instanciarse.

¿Qué es un método abstracto?
R: Un método sin cuerpo.

¿Debe una clase abstracta tener métodos abstractos?
R: No es obligatorio.

¿Una clase abstracta puede tener métodos concretos?
R: Sí.

¿Qué pasa si la subclase no implementa los métodos abstractos?
R: Debe ser abstracta.

¿Puede una clase abstracta tener constructor?
R: Sí.

¿Puede una clase abstracta extender otra abstracta?
R: Sí.

¿Puede un método abstracto ser private?
R: No.

¿Puede un método abstracto ser final?
R: No.

¿Puede una clase final ser abstracta?
R: No.

¿Puede un método abstracto ser static?
R: No.

¿Puede un atributo ser abstracto?
R: No.

¿Puede una interfaz contener métodos abstractos?
R: Sí (antes de Java 8, todos lo eran).

¿Puede una clase tener ambos: final y abstract?
R: No.

¿Un método final puede estar en una clase abstracta?
R: Sí.

🔹 this y super (41–50)

¿Para qué se usa this?
R: Referencia al objeto actual.

¿Para qué se usa super?
R: Referencia a la superclase.

¿Un constructor puede llamar a this() y super()?
R: No simultáneamente (solo uno, y debe ser primera línea).

¿Qué pasa si super() apunta a un constructor inexistente?
R: Error de compilación.

¿Se puede acceder a un método sobreescrito usando super?
R: Sí.

¿Puede this() estar en la segunda línea?
R: No, debe ser la primera.

¿Puede super.method() invocar un método static?
R: Sí, pero no es recomendable.

¿Puede super() usarse fuera de un constructor?
R: No.

¿Puede this usarse en métodos static?
R: No.

¿Puede super usarse en métodos static?
R: No.

🔷 UNIDAD 5 — INTERFACES (30 PREGUNTAS)

¿Qué es una interfaz?
R: Un contrato que define métodos que deben implementarse.

¿Una interfaz puede tener cuerpo en sus métodos?
R: No (Java 7), excepto static/default desde Java 8.

¿Una interfaz puede tener atributos?
R: Sí, pero siempre son public static final.

¿Una interfaz puede tener constructor?
R: No.

¿Una interfaz puede extender otra?
R: Sí.

¿Una interfaz puede implementar otra?
R: No.

¿Una clase puede implementar múltiples interfaces?
R: Sí.

¿Se puede instanciar una interfaz?
R: No.

¿Una interfaz puede ser abstracta?
R: Es abstracta por default.

¿Puede una interfaz contener métodos private?
R: No en Java 7.

¿Puede una interfaz contener métodos static?
R: Sí (Java 8+).

¿Qué pasa si una clase no implementa todos los métodos de una interfaz?
R: Debe ser abstracta.

¿Se puede usar una interfaz como tipo de referencia?
R: Sí.

¿Puede una interfaz extender múltiples interfaces?
R: Sí.

¿Una clase puede extender una clase y a la vez implementar una interfaz?
R: Sí.

¿Puede una interfaz tener métodos final?
R: No.

¿Puede una interfaz tener métodos protected?
R: No.

¿Puede una interfaz heredar de una clase?
R: No.

¿Puede una interfaz tener inner classes?
R: Sí.

¿Puede una interfaz tener constantes?
R: Sí: public static final por default.

🔷 UNIDAD 6 — HILOS (THREADS) (50 PREGUNTAS)
🔹 Creación de hilos (71–85)

Nombre dos formas de crear hilos.
R: Extender Thread / implementar Runnable.

¿Qué método ejecuta el hilo?
R: run().

¿Qué método ARRANCA el hilo?
R: start().

¿Qué pasa si se llama run() directamente?
R: No crea un hilo nuevo, se ejecuta en el hilo actual.

¿Qué pasa si intento ejecutar start() dos veces?
R: IllegalThreadStateException.

¿Thread implementa Runnable?
R: Sí.

¿Puede una clase extender Thread y otra a la vez?
R: No (Java no soporta herencia múltiple).

¿Runnable es una interfaz o clase?
R: Interfaz.

¿Se puede pasar un Runnable al constructor de Thread?
R: Sí.

¿Thread puede recibir un nombre?
R: Sí: new Thread(runnable, “nombre”).

🔹 Estados del hilo (86–95)

¿Cuál es el estado inicial de un hilo recién creado?
R: NEW.

¿Qué estado tiene después de start()?
R: RUNNABLE.

¿Qué estado tiene cuando ejecuta run()?
R: RUNNING.

¿Qué estado tiene cuando está esperando I/O?
R: BLOCKED o WAITING.

¿Qué estado tiene cuando run() finaliza?
R: DEAD.

¿Qué método provoca WAITING?
R: sleep(), join(), wait().

¿Qué método desbloquea un WAIT?
R: notify() o notifyAll().

¿Qué significa DEAD?
R: El hilo terminó.

¿Un hilo DEAD puede reiniciarse?
R: No.

¿Runnable es estado o interfaz?
R: Interfaz.

🔹 Sincronización y concurrencia (96–110)

¿Qué es una condición de carrera?
R: Acceso concurrente no controlado que causa inconsistencia.

¿Cómo se evita una condición de carrera?
R: Con synchronized.

¿Qué sincroniza synchronized?
R: El acceso de hilos al mismo objeto/bloque crítico.

¿Qué es un monitor?
R: Un mecanismo de exclusión mutua usado por synchronized.

¿Puede un método static ser synchronized?
R: Sí.

¿Qué método hace que un hilo espere a otro?
R: join().

¿Qué hace yield()?
R: Sugiere ceder CPU a otro hilo.

¿Qué hace sleep()?
R: Pausa el hilo.

¿sleep() libera el lock?
R: No.

¿Puede synchronized aplicarse a bloques?
R: Sí, con synchronized(obj).

¿Qué hace wait()?
R: Libera el lock y suspende el hilo.

¿Qué hace notify()?
R: Despierta un hilo en wait().

¿Qué hace notifyAll()?
R: Despierta a todos los hilos en wait().

¿Qué diferencia hay entre wait() y sleep()?
R: wait libera el lock, sleep no.

¿Qué pasa si llamo wait() fuera de synchronized?
R: IllegalMonitorStateException.

🔷 UNIDAD 7 — COLECCIONES, GENERICS, EQUALS/HASHCODE (70 PREGUNTAS)
🔹 equals() y hashCode() (111–130)

¿Qué compara == en objetos?
R: Referencias.

¿Qué compara equals()?
R: Contenido (si está overrideado).

¿Qué pasa si no sobrescribo equals()?
R: Hereda el de Object (compara referencias).

¿Qué pasa si sobrescribo equals() pero no hashCode()?
R: El objeto funciona mal en HashSet/HashMap.

¿Cuándo deben ser iguales dos hashCodes?
R: Cuando equals() devuelve true.

¿hashCode() debe ser único?
R: No. Solo consistente.

¿Qué pasa si dos objetos tienen distinto hashCode pero equals true?
R: Rompe el contrato; comportamiento errático.

¿TreeSet usa equals() o compareTo()?
R: compareTo().

¿HashSet usa equals()?
R: Sí.

¿HashMap usa hashCode()?
R: Sí.

¿Qué es un bucket en HashSet?
R: Un listado interno donde se agrupan elementos con hash similar.

¿Qué método determina la posición en HashSet?
R: hashCode().

¿Qué método determina la igualdad final?
R: equals().

¿Pueden dos objetos tener igual hashCode?
R: Sí (colisión).

¿Qué pasa si equals() devuelve false para objetos con mismo hash?
R: Ambos se guardan en el mismo bucket.

¿Es obligatorio que hashCode sea rápido?
R: Sí (eficiencia del HashSet).

¿Se debe basar equals en atributos inmutables?
R: Idealmente sí.

¿hashCode puede cambiar durante la vida del objeto?
R: No debería (rompe estructuras de hash).

¿Qué interfaz requiere implementar compareTo()?
R: Comparable.

¿Puede un objeto tener hashCode constante?
R: Sí, pero baja rendimiento.

🔹 List (131–150)

¿List permite duplicados?
R: Sí.

¿List mantiene orden?
R: Sí.

¿Se puede hacer new List()?
R: No, es interfaz.

¿ArrayList es sincronizado?
R: No.

¿Vector es sincronizado?
R: Sí.

¿remove(int index) y remove(Object o) son iguales?
R: No.

¿contains usa equals()?
R: Sí.

¿get(int index) existe en Set?
R: No.

¿List permite null?
R: Sí.

¿ArrayList tiene capacidad inicial?
R: Sí, por defecto 10.

¿Se puede ordenar una List?
R: Sí, con Collections.sort().

¿Qué hace indexOf()?
R: Busca usando equals().

¿Qué hace clear()?
R: Borra todos los elementos.

¿Qué pasa si get(index) está fuera del rango?
R: IndexOutOfBoundsException.

¿Se puede iterar un ArrayList con for-each?
R: Sí.

¿Se puede hacer una lista de objetos propios?
R: Sí.

¿List funciona con generics?
R: Sí, recomendado.

¿List<Object> acepta cualquier cosa?
R: Sí.

¿List<String> acepta Integer?
R: No.

¿Una lista puede tener otro List adentro?
R: Sí (listas anidadas).

🔹 Set (151–165)

¿Set permite duplicados?
R: No.

¿HashSet mantiene orden?
R: No.

¿LinkedHashSet mantiene orden?
R: Sí, por inserción.

¿TreeSet ordena automáticamente?
R: Sí.

¿TreeSet usa compareTo()?
R: Sí.

¿HashSet usa hashCode()?
R: Sí.

¿Set permite null?
R: HashSet sí, TreeSet no.

¿remove(Object o) usa equals()?
R: Sí.

¿contains usa hashCode()?
R: Sí.

¿Puede un Set tener un objeto duplicado si equals() está mal?
R: Sí.

¿Se puede mezclar distintos tipos en un Set?
R: Sí, pero no recomendable.

¿Set tiene índices?
R: No.

¿Set puede iterarse?
R: Sí, con Iterator o for-each.

¿Set utiliza buckets?
R: HashSet sí.

¿TreeSet puede almacenar objetos sin Comparable?
R: No.

🔹 Generics (166–180)

¿Qué son los generics?
R: Tipos parametrizados.

¿Para qué sirven los generics?
R: Tipos seguros y evitar castings.

¿Qué significa List<?>?
R: Lista de tipo desconocido.

¿Se pueden crear arrays de tipos genéricos?
R: No directamente.

¿Puede List<String> convertirse a List<Object>?
R: No (invariancia).

¿Puede List<Object> contener Strings?
R: Sí.

¿Puede un generic tener múltiples parámetros?
R: Sí: Map<K,V>.

¿Puede una clase ser genérica?
R: Sí.

¿Puede un método ser genérico?
R: Sí.

¿Los generics existen en runtime?
R: No, se borran (type erasure).

¿Puede un generic usar extends?
R: Sí: List<? extends Number>.

¿Puede un generic usar super?
R: Sí: List<? super Integer>.

¿Puede una wildcard capturar tipos?
R: Sí, con capture conversion.

¿Puede un generic usar tipos primitivos?
R: No, solo wrappers.

¿Puede un generic restringirse a una interfaz?
R: Sí: <T extends Runnable>.

🔹 Map (181–200)

¿Map permite claves duplicadas?
R: No.

¿Map permite valores duplicados?
R: Sí.

¿HashMap mantiene orden?
R: No.

¿LinkedHashMap mantiene orden?
R: Sí.

¿TreeMap ordena claves automáticamente?
R: Sí.

¿Map usa hashCode() de la clave?
R: Sí.

¿get(key) usa equals()?
R: Sí.

¿put reemplaza valores?
R: Sí, si la clave existe.

¿Puede Map tener null como clave?
R: HashMap sí, TreeMap no.

¿Cómo se recorre un Map?
R: Con entrySet(), keySet() o values().

¿Map es una colección?
R: No, no extiende Collection.

¿Qué devuelve entrySet()?
R: Conjunto de pares clave–valor.

¿Qué pasa si equals está mal implementado en la clave?
R: El mapa “pierde” entradas.

¿Se puede usar un objeto mutable como clave en un Map?
R: No recomendable.

¿Qué método obtiene todas las claves?
R: keySet().

¿Qué método obtiene todos los valores?
R: values().

¿Se puede tener Map<List, Set>?
R: Sí, los tipos pueden ser complejos.

¿HashMap es sincronizado?
R: No.

¿Hashtable permite null?
R: No.

¿Qué diferencia hay entre HashMap y TreeMap?
R:

HashMap → no ordena, usa hash.

TreeMap → ordena según Comparable/Comparator.

El código es este (versión clásica de la PPT):

class NameRunnable implements Runnable {
    public void run() {
        for (int x = 1; x <= 3; x++) {
            System.out.println("Run by "
                    + Thread.currentThread().getName()
                    + ", x is " + x);
        }
    }
}

public class ManyNames {
    public static void main(String [] args) {
        NameRunnable nr = new NameRunnable();
        Thread one = new Thread(nr);
        Thread two = new Thread(nr);
        Thread three = new Thread(nr);
        one.setName("Fred");
        two.setName("Lucy");
        three.setName("Ricky");
        one.start();
        two.start();
        three.start();
    }
}

1️⃣ Qué líneas puede imprimir el programa

En total, el programa imprime 9 líneas, una por cada vuelta de cada hilo:

Hilo Fred:

Run by Fred, x is 1

Run by Fred, x is 2

Run by Fred, x is 3

Hilo Lucy:

Run by Lucy, x is 1

Run by Lucy, x is 2

Run by Lucy, x is 3

Hilo Ricky:

Run by Ricky, x is 1

Run by Ricky, x is 2

Run by Ricky, x is 3

Esas 9 líneas son fijas: no hay otras.

2️⃣ Restricción IMPORTANTÍSIMA (orden dentro de cada hilo)

Dentro de cada hilo, el valor de x SIEMPRE avanza en orden:

Para Fred:
Fred, x is 1 → después Fred, x is 2 → después Fred, x is 3

Lo mismo para Lucy y Ricky.

Eso significa:

Nunca vas a ver:
Run by Fred, x is 2 antes que Run by Fred, x is 1

Ni Run by Lucy, x is 3 antes que Run by Lucy, x is 2, etc.

3️⃣ Lo que SÍ puede variar: el intercalado entre hilos

El planificador de hilos decide en qué orden se mezclan esas 9 líneas.

Entonces, cualquier salida válida es:

Cualquier permutación de estas 9 líneas tal que, dentro de cada hilo, se respete el orden 1→2→3.

Matemáticamente:

Tenés 9 posiciones en la salida.

De esas 9, 3 serán de Fred (en orden 1,2,3),
otras 3 de Lucy (1,2,3),
otras 3 de Ricky (1,2,3).

La cantidad de combinaciones distintas es:

9
!
3
!
 
3
!
 
3
!
=
1680
3!3!3!
9!
	​

=1680

Obviamente no las vas a listar una por una en un parcial 😅.
Lo que el profe espera es que entiendas:

“La salida puede ser cualquier mezcla de las 9 líneas, siempre respetando que para cada nombre los x van en orden 1,2,3.”

4️⃣ Ejemplos de salidas posibles (todas correctas)
Ejemplo A (súper ordenado por hilo)
Run by Fred, x is 1
Run by Fred, x is 2
Run by Fred, x is 3
Run by Lucy, x is 1
Run by Lucy, x is 2
Run by Lucy, x is 3
Run by Ricky, x is 1
Run by Ricky, x is 2
Run by Ricky, x is 3

Ejemplo B (mezclado pero válido)
Run by Fred, x is 1
Run by Lucy, x is 1
Run by Ricky, x is 1
Run by Fred, x is 2
Run by Lucy, x is 2
Run by Ricky, x is 2
Run by Fred, x is 3
Run by Lucy, x is 3
Run by Ricky, x is 3

Ejemplo C (mezcla más caótica, pero correcta)
Run by Lucy, x is 1
Run by Fred, x is 1
Run by Lucy, x is 2
Run by Ricky, x is 1
Run by Fred, x is 2
Run by Lucy, x is 3
Run by Ricky, x is 2
Run by Fred, x is 3
Run by Ricky, x is 3


Todas esas son combinaciones posibles de salida.

5️⃣ Cómo responder esto en un parcial

En un parcial, si te ponen este código y preguntan:

“¿Qué imprime este código?”

La respuesta ideal es algo así:

Imprime 9 líneas del tipo
Run by <nombre>, x is <1|2|3>,
con los tres valores de x para cada hilo (Fred, Lucy, Ricky).
El orden exacto de las líneas no está determinado,
cualquier intercalado es posible siempre que para cada hilo
el valor de x aparezca en orden 1,2,3.

🧩 EJERCICIOS 1–20 (constructores, this/super, métodos)
1.
class A {
    int x = 5;
    public A() {
        x = x + 3;
        System.out.println(x);
    }
}

public class Test1 {
    public static void main(String[] args) {
        A a = new A();
    }
}


Salida:
8

2.
class A {
    int x;
    public A(int x) {
        this.x = x;
    }
    void mostrar() {
        System.out.println(x);
    }
}

public class Test2 {
    public static void main(String[] args) {
        A a = new A(10);
        a.mostrar();
    }
}


Salida:
10

3.
class Padre {
    String nombre = "Padre";
    public Padre() {
        System.out.println("Constructor " + nombre);
    }
}

class Hijo extends Padre {
    String nombre = "Hijo";
    public Hijo() {
        System.out.println("Constructor " + nombre);
    }
}

public class Test3 {
    public static void main(String[] args) {
        new Hijo();
    }
}


Salida:

Constructor Padre
Constructor Hijo

4.
class A {
    int y = 1;
    public A() {
        y = 2;
        metodo();
    }
    void metodo() {
        System.out.println("A: " + y);
    }
}

class B extends A {
    int z = 10;
    void metodo() {
        System.out.println("B: " + z);
    }
}

public class Test4 {
    public static void main(String[] args) {
        new B();
    }
}


Salida:
B: 10

5.
class A {
    A() {
        this(5);
        System.out.println("A()");
    }
    A(int x) {
        System.out.println("A(int): " + x);
    }
}

public class Test5 {
    public static void main(String[] args) {
        new A();
    }
}


Salida:

A(int): 5
A()

6.
class A {
    int x = 3;
    void m() {
        int x = 5;
        System.out.println(x);
    }
}

public class Test6 {
    public static void main(String[] args) {
        new A().m();
    }
}


Salida:
5

7.
class A {
    int x = 3;
    void m() {
        int x = 5;
        System.out.println(this.x);
    }
}

public class Test7 {
    public static void main(String[] args) {
        new A().m();
    }
}


Salida:
3

8.
class A {
    static int cont = 0;
    public A() {
        cont++;
    }
}

public class Test8 {
    public static void main(String[] args) {
        new A();
        new A();
        new A();
        System.out.println(A.cont);
    }
}


Salida:
3

9.
class A {
    final int x;
    A() {
        x = 10;
    }
    void print() {
        System.out.println(x);
    }
}

public class Test9 {
    public static void main(String[] args) {
        new A().print();
    }
}


Salida:
10

10.
class A {
    static void m() {
        System.out.println("A.m");
    }
}

class B extends A {
    static void m() {
        System.out.println("B.m");
    }
}

public class Test10 {
    public static void main(String[] args) {
        A a = new B();
        a.m();
    }
}


Salida:
A.m (método estático: ocultamiento, no polimorfismo)

11.
class A {
    void m(int x) {
        System.out.println("int");
    }
    void m(double x) {
        System.out.println("double");
    }
}

public class Test11 {
    public static void main(String[] args) {
        A a = new A();
        a.m(5);
    }
}


Salida:
int

12.
class A {
    void m(int x) {
        System.out.println("int");
    }
    void m(Integer x) {
        System.out.println("Integer");
    }
}

public class Test12 {
    public static void main(String[] args) {
        A a = new A();
        a.m(5);
    }
}


Salida:
int (elige primitivo exacto)

13.
class A {
    void m(Integer x) {
        System.out.println("Integer");
    }
    void m(Number x) {
        System.out.println("Number");
    }
}

public class Test13 {
    public static void main(String[] args) {
        A a = new A();
        a.m(5);
    }
}


Salida:
Integer

14.
class A {
    void m(Object o) {
        System.out.println("Object");
    }
    void m(String s) {
        System.out.println("String");
    }
}

public class Test14 {
    public static void main(String[] args) {
        A a = new A();
        a.m(null);
    }
}


Salida:
String (elige el más específico)

15.
class A {
    int x = 1;
    A() {
        x = 2;
    }
}

class B extends A {
    B() {
        x = 3;
    }
}

public class Test15 {
    public static void main(String[] args) {
        B b = new B();
        System.out.println(b.x);
    }
}


Salida:
3

16.
abstract class A {
    abstract void m();
}

class B extends A {
    void m() {
        System.out.println("B.m");
    }
}

public class Test16 {
    public static void main(String[] args) {
        A a = new B();
        a.m();
    }
}


Salida:
B.m

17.
class A {
    final void m() {
        System.out.println("A.m");
    }
}

class B extends A {
    // no puede overridear m()
}

public class Test17 {
    public static void main(String[] args) {
        new B().m();
    }
}


Salida:
A.m

18.
class A {
    int x = 1;
    A() {
        System.out.println("x = " + x);
        m();
    }
    void m() {
        System.out.println("A.m");
    }
}

class B extends A {
    int y = 10;
    void m() {
        System.out.println("B.m y = " + y);
    }
}

public class Test18 {
    public static void main(String[] args) {
        new B();
    }
}


Salida:

x = 1
B.m y = 10

19.
class A {
    static { System.out.println("static A"); }
    { System.out.println("init A"); }
    A() { System.out.println("ctor A"); }
}

public class Test19 {
    public static void main(String[] args) {
        new A();
        new A();
    }
}


Salida:

static A
init A
ctor A
init A
ctor A

20.
class A {
    static int x = 0;
    { x++; }
    A() { x++; }
}

public class Test20 {
    public static void main(String[] args) {
        new A();
        new A();
        System.out.println(A.x);
    }
}


Salida:
4

🧩 EJERCICIOS 21–40 (interfaces, override, equals básico, String, wrappers)
21.
interface I {
    void m();
}

class A implements I {
    public void m() {
        System.out.println("A.m");
    }
}

public class Test21 {
    public static void main(String[] args) {
        I i = new A();
        i.m();
    }
}


Salida:
A.m

22.
class A {
    void m() {
        System.out.println("A");
    }
}

class B extends A {
    void m() {
        System.out.println("B");
    }
}

public class Test22 {
    public static void main(String[] args) {
        A a = new B();
        a.m();
    }
}


Salida:
B

23.
public class Test23 {
    public static void main(String[] args) {
        String s1 = "Java";
        String s2 = "Java";
        System.out.println(s1 == s2);
    }
}


Salida:
true (pool de strings)

24.
public class Test24 {
    public static void main(String[] args) {
        String s1 = new String("Java");
        String s2 = new String("Java");
        System.out.println(s1 == s2);
    }
}


Salida:
false

25.
public class Test25 {
    public static void main(String[] args) {
        String s = "Hola";
        s.concat(" Mundo");
        System.out.println(s);
    }
}


Salida:
Hola

26.
public class Test26 {
    public static void main(String[] args) {
        StringBuilder sb = new StringBuilder("Hola");
        sb.append(" Mundo");
        System.out.println(sb);
    }
}


Salida:
Hola Mundo

27.
public class Test27 {
    public static void main(String[] args) {
        Integer a = 128;
        Integer b = 128;
        System.out.println(a == b);
    }
}


Salida:
false (fuera del cache -128..127)

28.
public class Test28 {
    public static void main(String[] args) {
        Integer a = 100;
        Integer b = 100;
        System.out.println(a == b);
    }
}


Salida:
true (dentro del cache)

29.
class A {
    int x;
    A(int x) {
        this.x = x;
    }
}

public class Test29 {
    public static void main(String[] args) {
        A a1 = new A(5);
        A a2 = new A(5);
        System.out.println(a1.equals(a2));
    }
}


Salida:
false (equals de Object → referencia)

30.
class A {
    int x;
    A(int x) { this.x = x; }
    public boolean equals(Object o) {
        if (!(o instanceof A)) return false;
        A a = (A) o;
        return this.x == a.x;
    }
}

public class Test30 {
    public static void main(String[] args) {
        A a1 = new A(5);
        A a2 = new A(5);
        System.out.println(a1.equals(a2));
    }
}


Salida:
true

31.
public class Test31 {
    public static void main(String[] args) {
        String s = "abc";
        System.out.println(s.toUpperCase());
        System.out.println(s);
    }
}


Salida:

ABC
abc

32.
public class Test32 {
    public static void main(String[] args) {
        String s = "   hola   ";
        System.out.println("(" + s.trim() + ")");
    }
}


Salida:
(hola)

33.
public class Test33 {
    public static void main(String[] args) {
        String s = "Java";
        System.out.println(s.length());
        System.out.println(s.charAt(1));
    }
}


Salida:

4
a

34.
public class Test34 {
    public static void main(String[] args) {
        String s = "abcdef";
        System.out.println(s.substring(1, 4));
    }
}


Salida:
bcd

35.
public class Test35 {
    public static void main(String[] args) {
        boolean b = (2 < 3) && (4 > 5);
        System.out.println(b);
    }
}


Salida:
false

36.
public class Test36 {
    public static void main(String[] args) {
        int x = 5;
        System.out.println(x++); 
        System.out.println(x);
    }
}


Salida:

5
6

37.
public class Test37 {
    public static void main(String[] args) {
        int x = 5;
        System.out.println(++x); 
        System.out.println(x);
    }
}


Salida:

6
6

38.
public class Test38 {
    public static void main(String[] args) {
        int x = 10;
        x += 3 * 2;
        System.out.println(x);
    }
}


Cálculo: 3*2=6 → x=10+6=16
Salida:
16

39.
public class Test39 {
    public static void main(String[] args) {
        int x = 10;
        int y = 3;
        System.out.println(x / y);
        System.out.println(x % y);
    }
}


Salida:

3
1

40.
public class Test40 {
    public static void main(String[] args) {
        int a = 5;
        int b = 5;
        System.out.println(a == b);
    }
}


Salida:
true

🧩 EJERCICIOS 41–70 (List, Set, Map, equals/hashCode, generics)
41.
import java.util.*;

public class Test41 {
    public static void main(String[] args) {
        List<String> l = new ArrayList<String>();
        l.add("A");
        l.add("B");
        l.add("A");
        System.out.println(l.size());
    }
}


Salida:
3

42.
import java.util.*;

public class Test42 {
    public static void main(String[] args) {
        Set<String> s = new HashSet<String>();
        s.add("A");
        s.add("B");
        s.add("A");
        System.out.println(s.size());
    }
}


Salida:
2

43.
import java.util.*;

public class Test43 {
    public static void main(String[] args) {
        List<String> l = new ArrayList<String>();
        l.add("Java");
        l.add("Perl");
        System.out.println(l.get(0));
    }
}


Salida:
Java

44.
import java.util.*;

public class Test44 {
    public static void main(String[] args) {
        List<String> l = new ArrayList<String>();
        l.add("Java");
        l.add("Perl");
        l.remove("Java");
        System.out.println(l.size());
        System.out.println(l.get(0));
    }
}


Salida:

1
Perl

45.
import java.util.*;

public class Test45 {
    public static void main(String[] args) {
        List<Integer> l = new ArrayList<Integer>();
        l.add(10);
        l.add(20);
        l.remove(0);
        System.out.println(l.get(0));
    }
}


Salida:
20

46.
import java.util.*;

public class Test46 {
    public static void main(String[] args) {
        List<Integer> l = new ArrayList<Integer>();
        l.add(10);
        l.add(20);
        l.remove(new Integer(10));
        System.out.println(l.get(0));
    }
}


Salida:
20

47.
import java.util.*;

public class Test47 {
    public static void main(String[] args) {
        Set<String> s = new HashSet<String>();
        s.add("Hola");
        s.add("Chao");
        System.out.println(s.contains("Hola"));
    }
}


Salida:
true

48.
import java.util.*;

public class Test48 {
    public static void main(String[] args) {
        Map<String,Integer> m = new HashMap<String,Integer>();
        m.put("a", 1);
        m.put("b", 2);
        System.out.println(m.get("a"));
    }
}


Salida:
1

49.
import java.util.*;

public class Test49 {
    public static void main(String[] args) {
        Map<String,Integer> m = new HashMap<String,Integer>();
        m.put("a", 1);
        m.put("a", 5);
        System.out.println(m.get("a"));
    }
}


Salida:
5

50.
import java.util.*;

public class Test50 {
    public static void main(String[] args) {
        Map<String,Integer> m = new HashMap<String,Integer>();
        m.put("a", 1);
        m.put("b", 2);
        System.out.println(m.size());
        m.remove("a");
        System.out.println(m.size());
    }
}


Salida:

2
1

51.
import java.util.*;

class Alumno {
    int legajo;
    Alumno(int l) { legajo = l; }
}

public class Test51 {
    public static void main(String[] args) {
        Set<Alumno> s = new HashSet<Alumno>();
        s.add(new Alumno(1));
        s.add(new Alumno(1));
        System.out.println(s.size());
    }
}


Salida:
2 (sin equals/hashCode → distintos)

52.
import java.util.*;

class Alumno {
    int legajo;
    Alumno(int l) { legajo = l; }
    public boolean equals(Object o) {
        if (!(o instanceof Alumno)) return false;
        return this.legajo == ((Alumno)o).legajo;
    }
    public int hashCode() {
        return legajo;
    }
}

public class Test52 {
    public static void main(String[] args) {
        Set<Alumno> s = new HashSet<Alumno>();
        s.add(new Alumno(1));
        s.add(new Alumno(1));
        System.out.println(s.size());
    }
}


Salida:
1

53.
import java.util.*;

public class Test53 {
    public static void main(String[] args) {
        List<String> l = new ArrayList<String>();
        l.add("A");
        l.add("B");
        l.add("C");
        for (String s : l) {
            System.out.print(s + " ");
        }
    }
}


Salida:
A B C

54.
import java.util.*;

public class Test54 {
    public static void main(String[] args) {
        Set<String> s = new LinkedHashSet<String>();
        s.add("Uno");
        s.add("Dos");
        s.add("Tres");
        for (String x : s) {
            System.out.print(x + " ");
        }
    }
}


Salida:
Uno Dos Tres

55.
import java.util.*;

public class Test55 {
    public static void main(String[] args) {
        Set<String> s = new HashSet<String>();
        s.add("Uno");
        s.add("Dos");
        s.add("Tres");
        System.out.println(s.contains("Dos"));
    }
}


Salida:
true

56.
import java.util.*;

public class Test56 {
    public static void main(String[] args) {
        List<String> l = new ArrayList<String>();
        l.add("Java");
        l.add("Java");
        System.out.println(l.indexOf("Java"));
        System.out.println(l.lastIndexOf("Java"));
    }
}


Salida:

0
1

57.
import java.util.*;

public class Test57 {
    public static void main(String[] args) {
        List<Integer> l = Arrays.asList(1, 2, 3);
        System.out.println(l.contains(2));
        System.out.println(l.contains(4));
    }
}


Salida:

true
false

58.
import java.util.*;

public class Test58 {
    public static void main(String[] args) {
        Map<Integer,String> m = new TreeMap<Integer,String>();
        m.put(2, "B");
        m.put(1, "A");
        m.put(3, "C");
        for (Integer k : m.keySet()) {
            System.out.print(k + ":" + m.get(k) + " ");
        }
    }
}


Salida:
1:A 2:B 3:C

59.
import java.util.*;

public class Test59 {
    public static void main(String[] args) {
        Map<String,String> m = new LinkedHashMap<String,String>();
        m.put("z", "Z");
        m.put("a", "A");
        m.put("m", "M");
        for (String k : m.keySet()) {
            System.out.print(k + " ");
        }
    }
}


Salida:
z a m

60.
import java.util.*;

public class Test60 {
    public static void main(String[] args) {
        List<? extends Number> l = Arrays.asList(1, 2, 3);
        Number n = l.get(0);
        System.out.println(n);
    }
}


Salida:
1

61.
import java.util.*;

public class Test61 {
    public static void main(String[] args) {
        List<Integer> l = new ArrayList<Integer>();
        l.add(1);
        l.add(2);
        l.add(3);
        l.clear();
        System.out.println(l.size());
    }
}


Salida:
0

62.
import java.util.*;

public class Test62 {
    public static void main(String[] args) {
        List<String> l1 = new ArrayList<String>();
        l1.add("A"); l1.add("B");
        List<String> l2 = new ArrayList<String>();
        l2.add("A"); l2.add("B");
        System.out.println(l1.equals(l2));
    }
}


Salida:
true

63.
import java.util.*;

public class Test63 {
    public static void main(String[] args) {
        Set<String> s1 = new HashSet<String>();
        s1.add("A");
        s1.add("B");
        Set<String> s2 = new HashSet<String>();
        s2.add("B");
        s2.add("A");
        System.out.println(s1.equals(s2));
    }
}


Salida:
true

64.
import java.util.*;

public class Test64 {
    public static void main(String[] args) {
        List<Object> l = new ArrayList<Object>();
        l.add("Hola");
        l.add(10);
        System.out.println(l.get(0) + " " + l.get(1));
    }
}


Salida:
Hola 10

65.
import java.util.*;

public class Test65 {
    public static void main(String[] args) {
        List<String> l = new ArrayList<String>();
        l.add("A");
        l.add("B");
        l.add(1, "X");
        System.out.println(l);
    }
}


Salida:
[A, X, B]

66.
import java.util.*;

public class Test66 {
    public static void main(String[] args) {
        String[] arr = {"a", "b", "c"};
        List<String> l = Arrays.asList(arr);
        arr[0] = "z";
        System.out.println(l);
    }
}


Salida:
[z, b, c]

67.
import java.util.*;

public class Test67 {
    public static void main(String[] args) {
        List<String> l = Arrays.asList("a", "b", "c");
        // l.add("d"); // lanzaría UnsupportedOperationException
        System.out.println(l.size());
    }
}


Salida:
3

68.
import java.util.*;

public class Test68 {
    public static void main(String[] args) {
        Map<String,Integer> m = new HashMap<String,Integer>();
        System.out.println(m.get("x"));
    }
}


Salida:
null

69.
import java.util.*;

public class Test69 {
    public static void main(String[] args) {
        List<String> l = new ArrayList<String>();
        System.out.println(l.isEmpty());
        l.add("X");
        System.out.println(l.isEmpty());
    }
}


Salida:

true
false

70.
import java.util.*;

public class Test70 {
    public static void main(String[] args) {
        Set<Integer> s = new TreeSet<Integer>();
        s.add(3);
        s.add(1);
        s.add(2);
        System.out.println(s);
    }
}


Salida:
[1, 2, 3]

🧩 EJERCICIOS 71–100 (varios mezclados, algunos con threads pero SALIDA FIJA o explicación clara)
71.
public class Test71 {
    public static void main(String[] args) {
        int x = 0;
        for (int i = 0; i < 3; i++) {
            x += i;
        }
        System.out.println(x);
    }
}


Salida:
3 (0+1+2)

72.
public class Test72 {
    public static void main(String[] args) {
        int x = 1;
        for (int i = 1; i <= 3; i++) {
            x *= i;
        }
        System.out.println(x);
    }
}


Salida:
6 (112*3)

73.
public class Test73 {
    public static void main(String[] args) {
        int x = 5;
        if (x > 3) {
            System.out.println("Mayor");
        } else {
            System.out.println("Menor o igual");
        }
    }
}


Salida:
Mayor

74.
public class Test74 {
    public static void main(String[] args) {
        int x = 10;
        String s = (x % 2 == 0) ? "Par" : "Impar";
        System.out.println(s);
    }
}


Salida:
Par

75.
public class Test75 {
    public static void main(String[] args) {
        int x = 2;
        switch (x) {
            case 1: System.out.println("Uno"); break;
            case 2: System.out.println("Dos"); break;
            default: System.out.println("Otro");
        }
    }
}


Salida:
Dos

76.
public class Test76 {
    public static void main(String[] args) {
        int x = 3;
        switch (x) {
            case 1: System.out.println("Uno");
            case 2: System.out.println("Dos");
            case 3: System.out.println("Tres");
            default: System.out.println("Default");
        }
    }
}


Salida:

Tres
Default

77.
public class Test77 {
    public static void main(String[] args) {
        int[] a = {1, 2, 3};
        System.out.println(a[0] + a[2]);
    }
}


Salida:
4

78.
public class Test78 {
    public static void main(String[] args) {
        int[] a = new int[3];
        System.out.println(a[0]);
    }
}


Salida:
0

79.
public class Test79 {
    public static void main(String[] args) {
        boolean[] b = new boolean[2];
        System.out.println(b[0]);
    }
}


Salida:
false

80.
public class Test80 {
    public static void main(String[] args) {
        String[] s = new String[2];
        System.out.println(s[0]);
    }
}


Salida:
null

81.
class Foo {
    static int x = 0;
    Foo() { x++; }
}

public class Test81 {
    public static void main(String[] args) {
        new Foo();
        new Foo();
        new Foo();
        System.out.println(Foo.x);
    }
}


Salida:
3

82.
class Padre {
    void m() { System.out.println("Padre"); }
}

class Hijo extends Padre {
    void m() { System.out.println("Hijo"); }
}

public class Test82 {
    public static void main(String[] args) {
        Padre p = new Hijo();
        p.m();
    }
}


Salida:
Hijo


83.
class Padre {
    static void m() { System.out.println("Padre"); }
}

class Hijo extends Padre {
    static void m() { System.out.println("Hijo"); }
}

public class Test83 {
    public static void main(String[] args) {
        Padre p = new Hijo();
        p.m();
    }
}


Salida:
Padre (estático)

84.
public class Test84 {
    public static void main(String[] args) {
        try {
            System.out.println("A");
            int x = 5 / 0;
            System.out.println("B");
        } catch (ArithmeticException e) {
            System.out.println("C");
        }
        System.out.println("D");
    }
}


Salida:

A
C
D

85.
public class Test85 {
    public static void main(String[] args) {
        try {
            System.out.println("A");
        } finally {
            System.out.println("B");
        }
        System.out.println("C");
    }
}


Salida:

A
B
C

86.
public class Test86 {
    public static void main(String[] args) {
        Integer x = null;
        try {
            System.out.println(x.toString());
        } catch (NullPointerException e) {
            System.out.println("NPE");
        }
    }
}


Salida:
NPE

87.
class A {
    public String toString() {
        return "A!"; 
    }
}

public class Test87 {
    public static void main(String[] args) {
        A a = new A();
        System.out.println(a);
    }
}


Salida:
A!

88.
class A {
    int x = 5;
    void m() {
        int x = 10;
        System.out.println(x);
    }
}

public class Test88 {
    public static void main(String[] args) {
        new A().m();
    }
}


Salida:
10

89.
class A {
    int x = 5;
    void m() {
        int x = 10;
        System.out.println(this.x);
    }
}

public class Test89 {
    public static void main(String[] args) {
        new A().m();
    }
}


Salida:
5

90.
public class Test90 {
    public static void main(String[] args) {
        System.out.println("Hola" + 1 + 2);
        System.out.println(1 + 2 + "Hola");
    }
}


Salida:

Hola12
3Hola

91.
public class Test91 {
    public static void main(String[] args) {
        char c = 'A';
        System.out.println((int)c);
    }
}


Salida:
65

92.
public class Test92 {
    public static void main(String[] args) {
        System.out.println( (char)('A' + 2) );
    }
}


Salida:
C

93.
public class Test93 {
    public static void main(String[] args) {
        byte b = 3;
        b += 130;
        System.out.println(b);
    }
}


130 mod 256 = 130 → 3+130=133; en byte: 133-256 = -123
Salida:
-123

94.
public class Test94 {
    public static void main(String[] args) {
        long l = 10;
        int x = (int)(l * 3);
        System.out.println(x);
    }
}


Salida:
30

95.
public class Test95 {
    public static void main(String[] args) {
        double d = 3.99;
        int x = (int)d;
        System.out.println(x);
    }
}


Salida:
3

96.
public class Test96 {
    public static void main(String[] args) {
        Boolean b1 = new Boolean("true");
        Boolean b2 = new Boolean("True");
        System.out.println(b1 + " " + b2);
    }
}


Salida:
true true

97.
public class Test97 {
    public static void main(String[] args) {
        Boolean b = new Boolean("false");
        if (b) {
            System.out.println("A");
        } else {
            System.out.println("B");
        }
    }
}


Salida:
B

98.
public class Test98 {
    public static void main(String[] args) {
        String s1 = "abc";
        String s2 = "ab" + "c";
        System.out.println(s1 == s2);
    }
}


Salida:
true (concatenación en compile-time)

99.
public class Test99 {
    public static void main(String[] args) {
        String s1 = "ab";
        String s2 = s1 + "c";
        String s3 = "abc";
        System.out.println(s2 == s3);
        System.out.println(s2.equals(s3));
    }
}


Salida:

false
true

100.
public class Test100 {
    public static void main(String[] args) {
        StringBuilder sb = new StringBuilder("abc");
        String s = sb.toString();
        System.out.println(s.equals("abc"));
    }
}


Salida:
true
