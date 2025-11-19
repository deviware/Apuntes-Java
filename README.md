# Apuntes-Java

PROGRAMACIÓN JAVA: APUNTE UNIVERSITARIO INTEGRAL
Nivel: Programación I y II | Enfoque: UTN / Ingeniería
Versión: Final Compilada

ÍNDICE DE CONTENIDOS
UNIDAD 1: Fundamentos del Lenguaje y Arquitectura
UNIDAD 2: Control de Flujo y Datos Estáticos
UNIDAD 3: Programación Orientada a Objetos (POO)
UNIDAD 4: Algoritmos y Estructuras de Datos Dinámicas
UNIDAD 5: Persistencia, Errores y Java Moderno
UNIDAD 6: Distribución de Aplicaciones

UNIDAD 1: FUNDAMENTOS DEL LENGUAJE Y ARQUITECTURA
1.1. Historia y Características
Java nació a principios de los 90 de la mano de James Gosling en Sun Microsystems. Originalmente pensado para electrodomésticos, evolucionó para ser el lenguaje de la web y sistemas empresariales 1.
Características Principales:
WORA (Write Once, Run Anywhere): "Escribe una vez, ejecuta en cualquier lugar". Esto se logra gracias a la Máquina Virtual.
Orientado a Objetos: Todo en Java se modela como objetos (salvo los tipos primitivos)2.
Robusto y Seguro: Gestión automática de memoria (Garbage Collector) y tipado fuerte para evitar errores comunes como desbordamientos de memoria 3.
Multihilo: Capacidad nativa para ejecutar tareas simultáneas4.
1.2. Arquitectura: ¿Cómo funciona Java?
El proceso de ejecución en Java tiene tres etapas clave que garantizan su portabilidad 5555:
Código Fuente (.java): Lo que escribe el programador.
Compilación (javac): El compilador traduce el código fuente a Bytecodes (.class). Estos no son código máquina, sino un "lenguaje intermedio" universal.
Interpretación (JVM): La Java Virtual Machine (JVM) toma los bytecodes y los traduce en tiempo real al código máquina específico del sistema operativo (Windows, Linux, Mac) donde se está ejecutando.
Concepto JIT (Just In Time): Para mejorar el rendimiento, la JVM moderna compila "al vuelo" las partes de código que se usan frecuentemente a código nativo para no tener que interpretarlas una y otra vez6.
1.3. Sintaxis Básica
Un programa mínimo en Java requiere una clase y un método main 7.
Java
public class HolaMundo { // Nombre de clase (PascalCase)
    // Método principal: Punto de entrada de la aplicación
    public static void main(String[] args) {
        System.out.println("Hola Mundo"); // Sentencia terminada en ;
    }
}

Case Sensitive: Java distingue mayúsculas de minúsculas (A != a)8.
Bloques: Delimitados por llaves { }9.
1.4. Tipos de Datos Primitivos
Java tiene 8 tipos de datos básicos que no son objetos. Se almacenan directamente en la pila de memoria (Stack) 10.
Tipo
Tamaño
Descripción / Rango
Uso común
byte
8 bits
-128 a 127
Ahorro extremo de memoria.
short
16 bits
-32,768 a 32,767
Poco uso actual.
int
32 bits
-2^31 a 2^31-1
El estándar para enteros.
long
64 bits
Muy grande (usar sufijo 'L')
Cálculos científicos/tiempos.
float
32 bits
Decimal simple (sufijo 'f')
Gráficos, ahorro memoria.
double
64 bits
Decimal doble precisión
El estándar para decimales.
boolean
1 bit*
true o false
Condiciones lógicas.
char
16 bits
Un solo carácter (Unicode)
'a', '@'. Comillas simples.

1.5. Operadores
Aritméticos: +, -, *, /, % (módulo/resto) 11.
Asignación: =, +=, -=, etc. (Ej: x += 4 equivale a x = x + 4)12.
Incremento/Decremento:
x++ (Post-incremento): Usa el valor y luego suma.
++x (Pre-incremento): Suma y luego usa el valor 13.
Relacionales: ==, !=, >, <, >=, <=. Devuelven un boolean.
Lógicos: && (AND), || (OR), ! (NOT)14.

UNIDAD 2: CONTROL DE FLUJO Y DATOS ESTÁTICOS
2.1. Ámbito de Variables (Scope)
El lugar donde declaras una variable determina su vida útil y visibilidad 15.
Variables Locales: Declaradas dentro de un método. Solo existen mientras se ejecuta ese método. No tienen valor por defecto (deben inicializarse)16.
Variables de Instancia (Globales al objeto): Declaradas dentro de la clase pero fuera de métodos. Pertenecen al objeto.
Variables Estáticas (Globales a la clase): Compartidas por todas las instancias.
Constantes: Se usa la palabra final. Su valor no puede cambiar una vez asignado. Convención: MAYUSCULAS.
final double PI = 3.1416;17.
2.2. Entrada y Salida (I/O)
Salida: System.out.println() (con salto de línea), System.out.print() (sin salto), System.out.printf() (con formato: %s string, %d entero, %.2f decimal) 18.
Entrada: Clase Scanner19.
Java
Scanner sc = new Scanner(System.in);
int edad = sc.nextInt();
sc.nextLine(); // IMPORTANTE: Limpiar el buffer después de leer números
String nombre = sc.nextLine();

Advertencia: Al usar nextInt(), el "Enter" queda en el buffer. Si luego usas nextLine(), leerá ese "Enter" vacío. Siempre haz un nextLine() extra para "limpiar" el buffer.
2.3. Estructuras Condicionales
IF / ELSE IF / ELSE: Evalúa condiciones booleanas 20.
OPERADOR TERNARIO: Forma corta de if-else.
variable = (condición) ? valorSiVerdad : valorSiFalso;21.
SWITCH: Estructura para múltiples casos de un mismo valor. Soporta int, char, String, Enum. Requiere break para evitar ejecutar los siguientes casos ("fall-through") 22.
2.4. Estructuras Iterativas (Bucles)
WHILE: Evalúa la condición antes de entrar. Puede no ejecutarse nunca23.
DO-WHILE: Ejecuta al menos una vez, luego evalúa. Ideal para menús de usuario 24.
FOR: Bucle determinado (sabemos cuántas veces iterar). for (inicio; condición; paso).
FOR-EACH: Bucle mejorado para recorrer colecciones/arreglos sin índice. for (Tipo elemento : coleccion) 25.
2.5. Arreglos (Arrays)
Estructura estática (tamaño fijo) que almacena elementos del mismo tipo 26.
Unidimensionales: int[] numeros = new int[5]; o int[] n = {1, 2, 3};.
Bidimensionales (Matrices): Arreglos de arreglos. int[][] matriz = new int[3][3];. Se recorren con dos for anidados (filas y columnas) 27.
2.6. La Clase String
En Java, String es un objeto, no un tipo primitivo. Son inmutables (no se modifican, se crean nuevos)28.
Comparación: NUNCA usar == para comparar contenido de Strings (eso compara referencias de memoria). Usar .equals()29.
Métodos útiles: length(), toUpperCase(), toLowerCase(), contains(), charAt().

UNIDAD 3: PROGRAMACIÓN ORIENTADA A OBJETOS (POO)
3.1. Conceptos Fundamentales
La POO modela el software basándose en entidades del mundo real.
Clase: Es el molde o plano. Define atributos (datos) y métodos (comportamiento)30.
Objeto: Es la instancia concreta creada a partir de la clase (new Clase())31.
Constructor: Método especial que se ejecuta al crear el objeto. Se usa para inicializar atributos32.
3.2. Los 4 Pilares de la POO
Abstracción: Enfocarse en lo esencial y ocultar la complejidad interna. Definir qué hace un objeto sin importar cómo33.
Encapsulamiento: Proteger los datos internos. Los atributos se definen private y se accede a ellos mediante métodos públicos getters y setters. Esto controla quién y cómo modifica los datos34.
Herencia: Capacidad de crear nuevas clases basadas en existentes (extends). La subclase hereda atributos y métodos de la superclase. Promueve la reutilización. Java no soporta herencia múltiple de clases353535.
Palabra clave super: Llama al constructor o métodos del padre36.
Polimorfismo: "Muchas formas". Un mismo mensaje puede ser respondido de diferente manera por distintos objetos.
Sobrecarga: Mismo nombre de método, distintos parámetros (en la misma clase)37.
Sobrescritura (@Override): Redefinir un método heredado en la subclase38.
3.3. Elementos Avanzados de Clases
this: Referencia al objeto actual. Resuelve ambigüedad entre atributos y parámetros39.
Métodos/Atributos Estáticos (static): Pertenecen a la clase, no a los objetos. Se pueden invocar sin instanciar (Clase.metodo())40.
Clases Abstractas: Clases que no se pueden instanciar. Sirven de base para la herencia. Pueden tener métodos abstractos (sin cuerpo, obligan a los hijos a implementarlos) y concretos41.
Interfaces: Contratos puros. Solo definen métodos abstractos (qué hacer) y constantes. Una clase puede implementar múltiples interfaces (implements), solucionando la falta de herencia múltiple 42.

UNIDAD 4: ALGORITMOS Y ESTRUCTURAS DE DATOS DINÁMICAS
4.1. Algoritmos de Ordenamiento
Bubble Sort (Burbuja): Compara pares adyacentes e intercambia. Sencillo pero ineficiente ($O(n^2)$). No recomendado para grandes volúmenes 43.
Quick Sort: "Divide y vencerás". Elige un pivote y particiona la lista en menores y mayores. Muy eficiente ($O(n \log n)$)44.
Merge Sort: Divide la lista en mitades recursivamente hasta tener 1 elemento, luego fusiona ordenadamente. Estable y eficiente45.
4.2. Colecciones (Estructuras Dinámicas)
A diferencia de los arrays, crecen dinámicamente.
Listas (ArrayList): Acceso rápido por índice. Implementa interfaz List. Permite duplicados 46.
Pilas (Stack): Estructura LIFO (Last In, First Out - Último en entrar, primero en salir). Operaciones: push (meter), pop (sacar), peek (mirar cima)47.
Colas (LinkedList como Queue): Estructura FIFO (First In, First Out - Primero en entrar, primero en salir). Operaciones: offer (encolar), poll (desencolar)48.
4.3. Árboles
Estructura no lineal jerárquica.
Árbol N-ario: Cada nodo puede tener N hijos49.
Componentes: Raíz (inicio), Hijos, Hojas (sin hijos).
Recorridos Recursivos:
Preorden: Raíz -> Hijos.
Posorden: Hijos -> Raíz.
4.4. Recursividad
Técnica donde un método se llama a sí mismo. Esencial para árboles y ciertos algoritmos (como factorial).
Requisito vital: Debe tener un Caso Base (condición de fin) para evitar un bucle infinito (StackOverflowError)50505050.

UNIDAD 5: PERSISTENCIA, ERRORES Y JAVA MODERNO
5.1. Manejo de Excepciones (Errores)
Mecanismo para controlar errores en tiempo de ejecución y evitar que el programa "crashee"51.
Try: Bloque de código "peligroso" que puede fallar.
Catch: Bloque que captura el error y lo maneja (ej. mostrar mensaje).
Finally: Bloque que se ejecuta siempre (haya error o no). Ideal para cerrar recursos (archivos, conexiones)52525252.
Tipos:
Checked (Comprobadas): Java obliga a tratarlas (ej. IOException).
Unchecked (Runtime): Errores de lógica (ej. dividir por cero), no es obligatorio capturarlas pero sí recomendable prevenirlas.
5.2. Archivos (File I/O)
Clases del paquete java.io.
File: Representación lógica de un archivo/carpeta (crear, borrar, verificar existencia)53.
Escritura: FileWriter + BufferedWriter (Buffer mejora rendimiento)54.
Lectura: FileReader + BufferedReader (método readLine() para leer texto línea a línea)55.
5.3. Serialización
Convierte un objeto (instancia) en una secuencia de bytes para guardarlo en un archivo o enviarlo por red.
La clase debe implementar implements Serializable.
transient: Palabra clave para atributos que NO se deben guardar (ej. contraseñas)56565656.
5.4. Bases de Datos (JDBC)
Conectividad Java con Bases de Datos (ej. MySQL).
Pasos estándar:
Cargar Driver JDBC.
Connection: Establecer conexión con URL, usuario y password57.
Statement / PreparedStatement: Crear la sentencia SQL.
ResultSet: Recibir los resultados de un SELECT e iterarlos con .next()58.
close(): Cerrar conexión.
5.5. Programación Funcional (Lambdas y Streams)
Introducido en Java 8, permite un código más conciso.
Expresión Lambda: Función anónima. Sintaxis: (parámetros) -> expresión59.
Streams: Flujo de datos para procesar colecciones de forma declarativa.
filter(): Filtrar elementos.
map(): Transformar elementos.
forEach(): Ejecutar acción por cada elemento.
collect(): Convertir el stream de vuelta a lista60.

UNIDAD 6: DISTRIBUCIÓN DE APLICACIONES
6.1. Archivos JAR (Java ARchive)
Formato de archivo (basado en ZIP) que empaqueta todos los componentes de una aplicación (clases compiladas .class, imágenes, sonidos, librerías) en un solo archivo distribuible61.
6.2. Creación y Ejecución
Creación: Se configura en el IDE como un "Artifact". Es vital definir la Clase Principal (Main Class) en el manifiesto para que el sistema sepa dónde arrancar62.
Ejecución:
Desde la consola de comandos:
java -jar MiAplicacion.jar
(Requiere tener instalado el JRE - Java Runtime Environment).

APÉNDICE: GLOSARIO RÁPIDO
API: Conjunto de librerías y herramientas que ofrece Java.
Cast (Casteo): Convertir un tipo de dato a otro (ej. (int) 3.5 pasa a 3).
IDE: Entorno de Desarrollo Integrado (IntelliJ, Eclipse, NetBeans).
Null: Referencia a "nada". Causa común de errores (NullPointerException).
Scope: Ámbito o visibilidad de una variable.

UNIDAD 1: Fundamentos (Variables y Operadores)
Objetivo: Entender tipos de datos primitivos, operadores aritméticos y entrada/salida básica.

Ejemplo: Calculadora de Índice de Masa Corporal (IMC)

Java

import java.util.Scanner;

public class CalculadoraIMC {
    public static void main(String[] args) {
        // 1. Entrada de datos (Scanner)
        Scanner sc = new Scanner(System.in);

        // 2. Declaración de Variables (Tipos Primitivos)
        System.out.print("Ingrese su peso en kg (ej: 70,5): ");
        double peso = sc.nextDouble(); // Variable tipo decimal

        System.out.print("Ingrese su altura en metros (ej: 1,75): ");
        double altura = sc.nextDouble();

        // 3. Operadores Aritméticos
        double imc = peso / (altura * altura); // Fórmula matemática

        // 4. Salida con formato (printf)
        System.out.printf("Su IMC es: %.2f%n", imc);
        
        // Cierre de recurso (Buena práctica)
        sc.close();
    }
}
UNIDAD 2: Control de Flujo y Arrays
Objetivo: Usar condicionales, bucles y almacenamiento estático.

Ejemplo: Analizador de Calificaciones

Java

public class AnalizadorNotas {
    public static void main(String[] args) {
        // 1. Array (Estructura Estática)
        int[] notas = {8, 4, 9, 2, 6, 10};
        int suma = 0;

        // 2. Bucle For-Each (Recorrido)
        System.out.println("--- Lista de Notas ---");
        for (int nota : notas) {
            System.out.print(nota + " ");
            suma += nota; // Acumulador
        }

        // Cálculo promedio
        double promedio = (double) suma / notas.length;

        System.out.println("\nPromedio: " + promedio);

        // 3. Condicional (Control de Flujo)
        if (promedio >= 6) {
            System.out.println("Estado: APROBADO");
        } else {
            System.out.println("Estado: REPROBADO");
        }
    }
}
UNIDAD 3: Programación Orientada a Objetos (POO)
Objetivo: Aplicar Clases, Herencia, Polimorfismo e Interfaces.

Ejemplo: Sistema de Pagos

Java

// 1. Abstracción y Herencia
abstract class MetodoPago {
    protected String titular;
    
    public MetodoPago(String titular) { this.titular = titular; }
    
    // Método Abstracto (Polimorfismo obligatorio)
    public abstract void procesarPago(double monto);
}

// 2. Interfaz (Contrato)
interface Validable {
    boolean verificarFondos(double monto);
}

// 3. Clase Concreta
class TarjetaCredito extends MetodoPago implements Validable {
    public TarjetaCredito(String titular) { super(titular); }

    @Override
    public boolean verificarFondos(double monto) {
        return true; // Lógica simulada
    }

    @Override
    public void procesarPago(double monto) {
        if(verificarFondos(monto)) {
            System.out.println("Pago de $" + monto + " procesado con Tarjeta de: " + titular);
        }
    }
}

public class MainPOO {
    public static void main(String[] args) {
        // Polimorfismo: Referencia de clase padre, instancia de hija
        MetodoPago pago = new TarjetaCredito("Juan Pérez");
        pago.procesarPago(1500.50);
    }
}
UNIDAD 4: Estructuras Dinámicas y Algoritmos
Objetivo: Usar Colecciones dinámicas (ArrayList) y ordenamiento.

Ejemplo: Gestor de Inventario

Java

import java.util.ArrayList;
import java.util.Collections;

public class Inventario {
    public static void main(String[] args) {
        // 1. Estructura Dinámica (ArrayList)
        ArrayList<String> productos = new ArrayList<>();

        // Agregar elementos
        productos.add("Laptop");
        productos.add("Mouse");
        productos.add("Teclado");

        System.out.println("Desordenado: " + productos);

        // 2. Algoritmo de Ordenamiento (Uso de API Collections)
        Collections.sort(productos);

        // 3. Recorrido
        System.out.println("Ordenado A-Z:");
        for (String p : productos) {
            System.out.println("- " + p);
        }
    }
}
UNIDAD 5: Persistencia y Excepciones
Objetivo: Guardar datos en disco y manejar errores robustamente.

Ejemplo: Guardar Bitácora (Log) en Archivo

Java

import java.io.FileWriter;
import java.io.IOException;

public class Logger {
    public static void main(String[] args) {
        String mensaje = "Inicio de sesión exitoso: Usuario Admin";

        // 1. Manejo de Excepciones (Try-Catch-Finally)
        try {
            // 2. Persistencia (FileWriter) - 'true' para modo append (agregar al final)
            FileWriter escritor = new FileWriter("bitacora.txt", true);
            escritor.write(mensaje + "\n");
            escritor.close();
            
            System.out.println("Log guardado correctamente.");
            
        } catch (IOException e) {
            // Captura del error
            System.err.println("Error al escribir en el archivo: " + e.getMessage());
        }
    }
}
UNIDAD 6: Distribución
Objetivo: Empaquetar. (No es código, son pasos).

Ejemplo Práctico:

Tomas el proyecto final.

Vas a File > Project Structure > Artifacts.

Creas un JAR from modules with dependencies.

Seleccionas la clase Main.

Ejecutas Build > Build Artifacts.

Entregas el archivo .jar resultante.

PROYECTO FINAL INTEGRADOR (Unidades 1 a 6)
Nombre: Sistema de Gestión de Estudiantes. Funcionalidad:

Permite cargar estudiantes (POO, Scanner).

Guarda los estudiantes en un archivo (Persistencia, Serialización).

Maneja errores si el archivo no existe (Excepciones).

Usa una lista dinámica para gestionarlos (Colecciones).

Archivo 1: Estudiante.java (El Objeto)

Java

import java.io.Serializable;

// Implementa Serializable para poder guardarse en archivo (Unidad 5)
public class Estudiante implements Serializable {
    private static final long serialVersionUID = 1L; // Versión de serialización
    
    // Encapsulamiento (Unidad 3)
    private String nombre;
    private double promedio;

    public Estudiante(String nombre, double promedio) {
        this.nombre = nombre;
        this.promedio = promedio;
    }

    @Override
    public String toString() {
        return "Estudiante: " + nombre + " | Promedio: " + promedio;
    }
}
Archivo 2: SistemaGestion.java (La Lógica)

Java

import java.io.*;
import java.util.ArrayList;
import java.util.Scanner;

public class SistemaGestion {

    // Lista Dinámica (Unidad 4)
    private static ArrayList<Estudiante> listaEstudiantes = new ArrayList<>();
    private static final String ARCHIVO = "datos_estudiantes.ser";

    public static void main(String[] args) {
        cargarDatos(); // Intenta recuperar datos previos (Persistencia)
        
        Scanner sc = new Scanner(System.in);
        int opcion = 0;

        // Bucle de Menú (Unidad 2)
        do {
            System.out.println("\n--- GESTIÓN ESCOLAR ---");
            System.out.println("1. Agregar Estudiante");
            System.out.println("2. Listar Estudiantes");
            System.out.println("3. Guardar y Salir");
            System.out.print("Opción: ");
            
            // Manejo de error si ingresa letras en vez de números (Unidad 5)
            try {
                opcion = Integer.parseInt(sc.nextLine());
            } catch (NumberFormatException e) {
                System.out.println("¡Error! Ingrese un número válido.");
                continue;
            }

            switch (opcion) { // Control de Flujo (Unidad 2)
                case 1:
                    System.out.print("Nombre: ");
                    String nombre = sc.nextLine();
                    System.out.print("Promedio: ");
                    double prom = Double.parseDouble(sc.nextLine());
                    
                    // Creación de Objeto (Unidad 3)
                    listaEstudiantes.add(new Estudiante(nombre, prom));
                    break;
                case 2:
                    // Uso de Lambdas para imprimir (Unidad 5 - Java Moderno)
                    if(listaEstudiantes.isEmpty()) System.out.println("Lista vacía.");
                    else listaEstudiantes.forEach(System.out::println);
                    break;
                case 3:
                    guardarDatos(); // Serialización
                    System.out.println("¡Datos guardados! Saliendo...");
                    break;
                default:
                    System.out.println("Opción incorrecta.");
            }
        } while (opcion != 3);
    }

    // Método para SERIALIZAR (Guardar en disco) - Unidad 5
    private static void guardarDatos() {
        try (ObjectOutputStream oos = new ObjectOutputStream(new FileOutputStream(ARCHIVO))) {
            oos.writeObject(listaEstudiantes);
        } catch (IOException e) {
            System.err.println("Error al guardar: " + e.getMessage());
        }
    }

    // Método para DESERIALIZAR (Leer del disco) - Unidad 5
    @SuppressWarnings("unchecked")
    private static void cargarDatos() {
        try (ObjectInputStream ois = new ObjectInputStream(new FileInputStream(ARCHIVO))) {
            listaEstudiantes = (ArrayList<Estudiante>) ois.readObject();
        } catch (FileNotFoundException e) {
            System.out.println("Archivo no encontrado. Se creará uno nuevo.");
        } catch (IOException | ClassNotFoundException e) {
            System.err.println("Error al cargar: " + e.getMessage());
        }
    }
}
