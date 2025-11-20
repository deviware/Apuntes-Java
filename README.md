
import java.util.Scanner;

public class Ejercicio1_Fundamentos {

    // --- Ejercicio 1.2: Variable global (static) para el Login ---
    // 'static' significa que esta variable pertenece a la clase, no a un objeto específico.
    // Es compartida por todas las llamadas.
    static int intentosFallidos = 0; 

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.println("=== EJERCICIO 1.1: CALCULADORA ===");
        mostrarMenuCalculadora(scanner);

        System.out.println("\n=== EJERCICIO 1.2: LOGIN ===");
        // Simulamos intentos
        validarUsuario("admin", "1234"); // Correcto (simulado)
        validarUsuario("admin", "badpass"); // Fallo 1
        validarUsuario("admin", "badpass"); // Fallo 2
        validarUsuario("admin", "badpass"); // Fallo 3
        validarUsuario("admin", "badpass"); // Bloqueo

        System.out.println("\n=== EJERCICIO 1.3: VALOR VS REFERENCIA ===");
        pruebaValorReferencia();
    }

    // --- Métodos Ejercicio 1.1 ---
    
    // Procedimiento: Realiza una acción pero no devuelve valor (void)
    public static void mostrarMenuCalculadora(Scanner sc) {
        System.out.println("1. Sumar | 2. Restar | 3. Multiplicar | 4. Dividir");
        System.out.print("Elige opción: ");
        int op = sc.nextInt();
        System.out.print("Ingresa num 1: ");
        double n1 = sc.nextDouble();
        System.out.print("Ingresa num 2: ");
        double n2 = sc.nextDouble();

        double res = 0;
        // Llamamos a las funciones que devuelven el resultado
        switch(op) {
            case 1: res = sumar(n1, n2); break;
            case 2: res = restar(n1, n2); break;
            case 3: res = multiplicar(n1, n2); break;
            case 4: res = dividir(n1, n2); break;
        }
        System.out.println("Resultado: " + res);
    }

    // Funciones: Reciben parámetros y retornan un valor (double)
    public static double sumar(double a, double b) { return a + b; }
    public static double restar(double a, double b) { return a - b; }
    public static double multiplicar(double a, double b) { return a * b; }
    public static double dividir(double a, double b) { 
        if(b == 0) { System.out.println("Error: Div por 0"); return 0; }
        return a / b; 
    }

    // --- Métodos Ejercicio 1.2 ---
    
    public static void validarUsuario(String user, String pass) {
        // Variables locales: solo existen dentro de este método
        String usuarioCorrecto = "admin";
        String passCorrecta = "1234";

        if (user.equals(usuarioCorrecto) && pass.equals(passCorrecta)) {
            System.out.println("Login exitoso.");
            intentosFallidos = 0; // Reseteamos si entra bien
        } else {
            intentosFallidos++; // Modificamos la variable global
            System.out.println("Login fallido. Intentos: " + intentosFallidos);
            if (intentosFallidos > 3) {
                System.out.println("¡USUARIO BLOQUEADO!");
            }
        }
    }

    // --- Métodos Ejercicio 1.3 ---

    public static void pruebaValorReferencia() {
        int numero = 10;
        int[] arreglo = {10, 20, 30};

        System.out.println("Antes -> Numero: " + numero + ", Arreglo[0]: " + arreglo[0]);
        
        duplicarNumero(numero); // Paso por VALOR (copia)
        duplicarArreglo(arreglo); // Paso por REFERENCIA (dirección de memoria)

        // El 'numero' no cambia, el 'arreglo' sí.
        System.out.println("Después -> Numero: " + numero + " (No cambia), Arreglo[0]: " + arreglo[0] + " (Cambia)");
    }

    public static void duplicarNumero(int x) {
        x = x * 2; // Esto solo modifica la copia local 'x', no la original
    }

    public static void duplicarArreglo(int[] arr) {
        for (int i = 0; i < arr.length; i++) {
            arr[i] = arr[i] * 2; // Esto modifica el espacio de memoria original
        }
    }
}
2. Estructuras Secuenciales y de Control
Este código agrupa los ejercicios 21 al 25, cubriendo if, switch, bucles (for, while, do-while), break y continue.

Java

import java.util.Scanner;

public class Ejercicio2_Estructuras {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // --- 2.2 Sistema de Calificaciones ---
        System.out.print("Ingrese una nota (0-10): ");
        int nota = sc.nextInt();
        
        // Lógica con IF-ELSE
        if (nota < 6) System.out.println("Reprobado");
        else if (nota >= 6 && nota < 9) System.out.println("Aprobado");
        else if (nota >= 9) System.out.println("Excelente");

        // Lógica con SWITCH (Ejercicio 18)
        // Nota: Switch no maneja rangos nativos fácilmente sin trucos en versiones viejas,
        // aquí usamos casos discretos para ejemplificar.
        switch(nota) {
            case 10: case 9: System.out.println("Excelente (Switch)"); break;
            case 8: case 7: case 6: System.out.println("Aprobado (Switch)"); break;
            default: 
                if(nota < 6) System.out.println("Reprobado (Switch)");
                break;
        }

        // --- 2.3 Repetitivas ---
        System.out.println("\n--- Bucles ---");
        
        // FOR: Bueno cuando sabemos cuántas veces iterar
        System.out.print("For (1-10): ");
        for(int i = 1; i <= 10; i++) {
            System.out.print(i + " ");
        }
        
        // WHILE: Bueno cuando la condición depende de algo externo al conteo
        System.out.print("\nWhile (10-1): ");
        int j = 10;
        while(j >= 1) {
            System.out.print(j + " ");
            j--;
        }

        // DO-WHILE: Se ejecuta al menos una vez
        System.out.println("\nDo-While (Ingresa 0 para salir):");
        int num;
        do {
            System.out.print("Numero: ");
            num = sc.nextInt();
        } while(num != 0);

        // FOR-EACH: Para recorrer arreglos
        int[] numeros = {100, 200, 300};
        System.out.print("For-Each: ");
        for(int n : numeros) {
            System.out.print(n + " ");
        }

        // --- 2.4 Control de Flujo (Break) ---
        System.out.println("\n\n--- Break (Ingresa 999 para cortar) ---");
        int count = 0;
        while(true) { // Bucle infinito intencional
            System.out.print("Dato: ");
            int dato = sc.nextInt();
            if(dato == 999) {
                break; // Rompe el bucle inmediatamente
            }
            count++;
        }
        System.out.println("Ingresaste " + count + " números antes de detenerse.");

        // --- 2.5 Continue ---
        System.out.println("\n--- Continue (Solo pares) ---");
        System.out.println("Simulando ingreso de 1 al 5...");
        for(int k = 1; k <= 5; k++) {
            if(k % 2 != 0) {
                continue; // Salta el resto del código y va a la siguiente iteración
            }
            System.out.println("Número par procesado: " + k);
        }
    }
}
3. Entrada y Salida de Datos
Ejercicios 31 a 35. Nos enfocamos en Scanner y formatos con printf.

Java

import java.util.Scanner;

public class Ejercicio3_InputOutput {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        // Configurar scanner para usar punto como decimal (opcional, depende de la región)
        sc.useLocale(java.util.Locale.US); 

        // --- 3.1 Datos Personales ---
        System.out.print("Nombre: ");
        String nombre = sc.nextLine(); 
        System.out.print("Edad: ");
        int edad = sc.nextInt();
        sc.nextLine(); // TRUCO IMPORTANTE: Consumir el salto de línea residual después de nextInt()
        System.out.print("Ciudad: ");
        String ciudad = sc.nextLine();
        
        System.out.println("Hola " + nombre + ", tienes " + edad + " años y vives en " + ciudad + ".");

        // --- 3.2 Operaciones y printf ---
        System.out.print("\nIngresa dos enteros para multiplicar: ");
        int n1 = sc.nextInt();
        int n2 = sc.nextInt();
        // %d es para enteros (decimal integer)
        // \n es salto de línea
        System.out.printf("El producto es: %d\n", (n1 * n2));

        // --- 3.3 Conversión Temperatura ---
        System.out.print("\nGrados Celsius: ");
        double celsius = sc.nextDouble();
        double fahrenheit = (celsius * 9/5) + 32;
        // %.2f significa float/double con 2 decimales
        System.out.printf("Equivale a: %.2f °F\n", fahrenheit);

        // --- 3.5 Promedio ---
        System.out.println("\nIngresa 3 notas decimales:");
        double nota1 = sc.nextDouble();
        double nota2 = sc.nextDouble();
        double nota3 = sc.nextDouble();
        double promedio = (nota1 + nota2 + nota3) / 3;
        System.out.printf("El promedio del alumno es: %.2f\n", promedio);
    }
}
4. Strings (Cadenas de texto)
Ejercicios 41 a 48. Manipulación de texto.

Java

import java.util.Scanner;

public class Ejercicio4_Strings {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // --- 4.1 y 4.2 Creación y Concatenación ---
        System.out.print("Nombre: ");
        String nombre = sc.nextLine();
        System.out.print("Apellido: ");
        String apellido = sc.nextLine();
        
        // Concatenación simple con +
        String nombreCompleto = nombre + " " + apellido;
        System.out.println("Hola, " + nombre + ", bienvenido a Java!");
        System.out.println("Nombre completo: " + nombreCompleto);

        // --- 4.3 Longitud ---
        System.out.println("Tu nombre completo tiene " + nombreCompleto.length() + " caracteres.");

        // --- 4.4 Comparación ---
        System.out.print("\nEscribe 'Java': ");
        String palabra = sc.next(); // next() lee hasta el primer espacio
        
        // NUNCA usar '==' para comparar Strings, usar equals()
        if(palabra.equals("Java")) {
            System.out.println("Es exactamente igual.");
        }
        if(palabra.equalsIgnoreCase("java")) {
            System.out.println("Es igual ignorando mayúsculas.");
        }

        // --- 4.5 Mayúsculas/Minúsculas ---
        System.out.println("Mayúsculas: " + nombreCompleto.toUpperCase());
        System.out.println("Minúsculas: " + nombreCompleto.toLowerCase());

        // --- 4.6 Recorrido con charAt ---
        System.out.println("\nDeletreando nombre:");
        for(int i = 0; i < nombre.length(); i++) {
            // charAt(i) obtiene el caracter en la posición i
            System.out.println(nombre.charAt(i));
        }

        // --- 4.7 Búsqueda ---
        sc.nextLine(); // Limpiar buffer
        System.out.print("\nEscribe una frase: ");
        String frase = sc.nextLine();
        System.out.print("Palabra a buscar: ");
        String busqueda = sc.next();

        if(frase.contains(busqueda)) {
            System.out.println("La frase contiene la palabra.");
            // indexOf devuelve el índice donde empieza la palabra, o -1 si no está
            System.out.println("Empieza en la posición: " + frase.indexOf(busqueda));
        } else {
            System.out.println("No se encontró la palabra.");
        }

        // --- 4.8 Caracteres de Escape ---
        // \t mete una tabulación, \n un salto de línea
        System.out.println("\nFormato con escapes:\nNombre:\t" + nombre + "\nEdad:\t25\nCiudad:\tResistencia");
    }
}

5. Arrays Estáticos y Gestión de Objetos

Contexto: Los ejercicios 5.1 (Estudiantes) , 5.2 (Productos) y 5.3 (Mascotas)  siguen la misma lógica "CRUD" (Crear, Leer, Actualizar, Borrar) sobre un arreglo de tamaño fijo.



A continuación, presento la solución completa para el Ejercicio 5.1 (Gestión de Estudiantes). La lógica de "eliminar huecos" en un array es la parte más técnica aquí.

Java

import java.util.Scanner;

// 1. Definimos la clase base (El "Molde" del objeto)
class Estudiante {
    String nombre;
    int edad;
    double promedio;

    // Constructor: Inicializa los datos al crear el objeto
    public Estudiante(String nombre, int edad, double promedio) {
        this.nombre = nombre;
        this.edad = edad;
        this.promedio = promedio;
    }

    // toString: Permite mostrar el objeto como texto legible
    @Override
    public String toString() {
        return "Nombre: " + nombre + " | Edad: " + edad + " | Promedio: " + promedio;
    }
}

// 2. Clase Gestora (Maneja el array)
class ColeccionDeEstudiantes {
    // Array fijo de 5 posiciones (Ejercicio 5.1)
    private Estudiante[] estudiantes = new Estudiante[5]; 
    private int cantidadActual = 0; // Contador real de cuántos hay guardados

    // --- Método para AGREGAR ---
    public void agregar(String nombre, int edad, double promedio) {
        if (cantidadActual < estudiantes.length) {
            // Creamos el objeto y lo guardamos en la primera posición libre
            estudiantes[cantidadActual] = new Estudiante(nombre, edad, promedio);
            cantidadActual++;
            System.out.println("Estudiante agregado.");
        } else {
            System.out.println("Error: Lista llena.");
        }
    }

    // --- Método para LISTAR ---
    public void listar() {
        System.out.println("--- Lista de Estudiantes ---");
        // Solo recorremos hasta 'cantidadActual' para no mostrar nulos
        for (int i = 0; i < cantidadActual; i++) {
            System.out.println((i) + ". " + estudiantes[i].toString());
        }
    }

    // --- Método para MODIFICAR ---
    public void modificar(String nombreBuscado, double nuevoPromedio) {
        for (int i = 0; i < cantidadActual; i++) {
            if (estudiantes[i].nombre.equalsIgnoreCase(nombreBuscado)) {
                estudiantes[i].promedio = nuevoPromedio;
                System.out.println("Datos actualizados.");
                return; // Terminamos al encontrarlo
            }
        }
        System.out.println("Estudiante no encontrado.");
    }

    // --- Método para ELIMINAR (El más complejo) ---
    // Al borrar en un array estático, quedan "huecos". Debemos desplazar los elementos.
    public void eliminar(String nombreBuscado) {
        int indiceEncontrado = -1;

        // 1. Buscamos la posición
        for (int i = 0; i < cantidadActual; i++) {
            if (estudiantes[i].nombre.equalsIgnoreCase(nombreBuscado)) {
                indiceEncontrado = i;
                break;
            }
        }

        if (indiceEncontrado != -1) {
            // 2. Desplazamos todo lo que está a la derecha una posición a la izquierda
            // para tapar el hueco del eliminado.
            for (int i = indiceEncontrado; i < cantidadActual - 1; i++) {
                estudiantes[i] = estudiantes[i + 1];
            }
            // 3. Limpiamos la última posición (ahora duplicada) y bajamos el contador
            estudiantes[cantidadActual - 1] = null;
            cantidadActual--;
            System.out.println("Estudiante eliminado.");
        } else {
            System.out.println("No se encontró para eliminar.");
        }
    }
}

// Clase Main para probar
public class Ejercicio5_ArraysObjetos {
    public static void main(String[] args) {
        ColeccionDeEstudiantes colegio = new ColeccionDeEstudiantes();
        
        // Pruebas
        colegio.agregar("Juan", 20, 8.5);
        colegio.agregar("Ana", 22, 9.0);
        colegio.agregar("Pedro", 19, 5.5);
        
        colegio.listar();
        
        System.out.println("\n>> Modificando promedio de Pedro...");
        colegio.modificar("Pedro", 7.0);
        
        System.out.println("\n>> Eliminando a Ana...");
        colegio.eliminar("Ana");
        
        colegio.listar(); // Ana ya no debe estar y Pedro debe haber subido de posición
    }
}
6. Clases Abstractas e Interfaces
Contexto: Aquí implementamos jerarquías.


Clase Abstracta: Define qué es el objeto y da una base común (ej. Figura con calcularArea).


Interfaz: Define qué puede hacer el objeto, sin importar su herencia (ej. Dibujable).

A continuación, resuelvo el Ejercicio 6.1 (Figuras), que combina ambos conceptos. La lógica es idéntica para los ejercicios de Animales , Vehículos, etc.


Java

// --- INTERFAZ (El "Comportamiento") ---
// Cualquier cosa que implemente esto DEBE tener un método dibujar.
interface Dibujable {
    void dibujar(); 
}

// --- CLASE ABSTRACTA (El "Concepto") ---
// No se pueden crear objetos "Figura" directamente, solo hijos (Círculos, Rectángulos).
abstract class Figura {
    // Método abstracto: Obliga a los hijos a escribir la fórmula matemática específica
    abstract double calcularArea();
    
    // Método concreto: Algo que todos heredan tal cual
    public void imprimirTipo() {
        System.out.print("Soy una figura -> ");
    }
}

// --- CLASES CONCRETAS (La implementación real) ---

// 1. Círculo
class Circulo extends Figura implements Dibujable {
    double radio;

    public Circulo(double radio) {
        this.radio = radio;
    }

    @Override
    double calcularArea() {
        return Math.PI * radio * radio;
    }

    @Override
    public void dibujar() {
        System.out.println("Dibujando un círculo O");
    }
}

// 2. Rectángulo
class Rectangulo extends Figura implements Dibujable {
    double base, altura;

    public Rectangulo(double base, double altura) {
        this.base = base;
        this.altura = altura;
    }

    @Override
    double calcularArea() {
        return base * altura;
    }

    @Override
    public void dibujar() {
        System.out.println("Dibujando un rectángulo []");
    }
}

public class Ejercicio6_AbstractasInterfaces {
    public static void main(String[] args) {
        // Polimorfismo: Usamos la clase padre 'Figura' para referenciar a los hijos
        Figura f1 = new Circulo(5);
        Figura f2 = new Rectangulo(4, 6);

        // Probando Círculo
        f1.imprimirTipo(); 
        // Necesitamos "castear" (convertir) a Dibujable para usar el método de la interfaz
        // si la variable es de tipo 'Figura' y Figura no implementa Dibujable directamente.
        // Pero para simplificar, aquí llamamos directo si definimos bien las variables:
        
        System.out.printf("Area Circulo: %.2f\n", f1.calcularArea());
        ((Dibujable) f1).dibujar(); 

        System.out.println("---");

        // Probando Rectángulo
        f2.imprimirTipo();
        System.out.println("Area Rectangulo: " + f2.calcularArea());
        ((Dibujable) f2).dibujar();
    }
}
Explicación de conceptos clave (para tus comentarios):
abstract class: Sirve para crear una plantilla. En el ejercicio 6.2, Animal sería abstracta porque un "Animal" genérico no hace un sonido específico, pero Perro (con su "Guau") sí.

interface: Es un contrato. En el ejercicio 6.3, Auto y Moto heredan de Vehiculo, pero implementan Recargable. Esto permite que si mañana creas una clase Celular (que no es vehículo), también pueda ser Recargable.

Polimorfismo: Es la capacidad de tratar a un Circulo o un Rectangulo simplemente como Figura, permitiendo hacer arrays o listas genéricas (ej. List<Figura>).

¡Perfecto! Continuemos con la Parte 3, que cubre los temas más avanzados y modernos de Java, incluyendo Lambdas, colecciones dinámicas y la gestión manual de listas.Aquí tienes la solución para la Sección 7 (Expresiones Lambda y Métodos por Referencia) y las Secciones 9 y 10 (Estructuras de Datos).7. Expresiones Lambda y Métodos por Referencia (Java Moderno)Estos ejercicios $(\text{7.1 a 7.5})$ te introducen al paradigma funcional, usando Lambdas para realizar acciones concisas y métodos por referencia para reutilizar funcionalidad existente.Estructura Común de ClasesCreamos las clases base (Persona, Estudiante, Producto, Arbol, Empleado) para los ejercicios $\text{7.1}$ a $\text{7.5}$.Javaimport java.time.Year;
import java.util.ArrayList;
import java.util.List;
import java.util.function.Consumer;
import java.util.stream.Collectors;

// Clase base para 7.1
class Persona {
    String nombre;
    int anioNacimiento;

    public Persona(String nombre, int anioNacimiento) {
        this.nombre = nombre;
        this.anioNacimiento = anioNacimiento;
    }

    public int getEdad() {
        // Obtenemos el año actual del sistema
        return Year.now().getValue() - anioNacimiento;
    }

    public String getNombre() { return nombre; }
    public int getAnioNacimiento() { return anioNacimiento; }
}

// Clase base para 7.2
class EstudiantePromedio {
    String nombre;
    double promedio;

    public EstudiantePromedio(String nombre, double promedio) {
        this.nombre = nombre;
        this.promedio = promedio;
    }

    public String getNombre() { return nombre; }
    public double getPromedio() { return promedio; }
}

// Clase base para 7.3
class ProductoLambda {
    String nombre;
    double precio;

    public ProductoLambda(String nombre, double precio) {
        this.nombre = nombre;
        this.precio = precio;
    }

    public String getNombre() { return nombre; }
    public double getPrecio() { return precio; }
    
    // Método estático para usar como referencia (7.3)
    public static void mostrarPrecioOriginal(ProductoLambda p) {
        System.out.println("Precio Original de " + p.nombre + ": $" + p.precio);
    }
}

// Clase base para 7.4
class Arbol {
    String especie;
    int anioPlantacion;

    public Arbol(String especie, int anioPlantacion) {
        this.especie = especie;
        this.anioPlantacion = anioPlantacion;
    }

    // Método de instancia para usar como referencia (7.4)
    @Override
    public String toString() {
        return "Arbol [especie=" + especie + ", año=" + anioPlantacion + "]";
    }
}

// Clase base para 7.5
class EmpleadoLambda {
    String nombre;
    double sueldo;

    public EmpleadoLambda(String nombre, double sueldo) {
        this.nombre = nombre;
        this.sueldo = sueldo;
    }

    public double getSueldo() { return sueldo; }
    
    // Método de instancia para usar como referencia (7.5)
    public void mostrarDatosActualizados() {
        System.out.printf("Empleado: %s | Sueldo Actualizado: $%.2f\n", nombre, sueldo);
    }
}


public class Ejercicio7_Lambdas {

    public static void main(String[] args) {
        // Ejecución de todos los ejercicios de Lambda
        ejercicio7_1();
        ejercicio7_2();
        ejercicio7_3();
        ejercicio7_4();
        ejercicio7_5();
    }
    
    // --- 7.1 Filtrar personas mayores de edad ---
    public static void ejercicio7_1() {
        System.out.println("=== 7.1: Personas Mayores de Edad (usando Stream y Lambda) ===");
        List<Persona> lista = List.of(
            new Persona("Juan", 2005), // Mayor de edad (2025 - 2005 = 20)
            new Persona("Maria", 2010), // Menor de edad
            new Persona("Pedro", 2000)
        );

        // 1. Filtrar usando stream() y una expresión lambda
        List<Persona> mayores = lista.stream()
            // Lambda: p -> p.getEdad() >= 18 es el predicado de filtro.
            .filter(p -> p.getEdad() >= 18) 
            .collect(Collectors.toList());

        // 2. Mostrar nombres y edades (con mayúsculas en el nombre)
        System.out.println("Mayores de edad:");
        mayores.forEach(p -> {
            // Lambda para Consumer (lo que se hace con cada elemento)
            System.out.printf("Nombre: %s (%d años)\n", 
                p.getNombre().toUpperCase(), p.getEdad()); 
        });
        System.out.println("-------------------------------------");
    }

    // --- 7.2 Lista de Estudiantes y Promedios ---
    public static void ejercicio7_2() {
        System.out.println("=== 7.2: Estudiantes y Promedios ===");
        List<EstudiantePromedio> estudiantes = List.of(
            new EstudiantePromedio("Alex", 8.5),
            new EstudiantePromedio("Beto", 6.8),
            new EstudiantePromedio("Carlos", 7.0)
        );

        // Imprimir nombres de estudiantes con promedio >= 7
        System.out.println("Nombres con Promedio >= 7:");
        estudiantes.stream()
            // Filtro Lambda
            .filter(e -> e.getPromedio() >= 7.0) 
            // Consumidor Lambda para imprimir solo el nombre
            .forEach(e -> System.out.println(e.getNombre()));

        // Mostrar todos los promedios usando un método de referencia (::)
        System.out.println("Todos los Promedios (Método por Referencia):");
        // Utilizamos el método println de System.out como referencia.
        // La sintaxis 'Clase::metodo' mapea la función que espera forEach (Consumer)
        // a un método existente que recibe un argumento (el promedio, en este caso).
        estudiantes.stream()
            .map(EstudiantePromedio::getPromedio) // Mapeamos a un Stream<Double>
            .forEach(System.out::println); 
        System.out.println("-------------------------------------");
    }

    // --- 7.3 Productos en una tienda ---
    public static void ejercicio7_3() {
        System.out.println("=== 7.3: Productos y Precios ===");
        List<ProductoLambda> productos = new ArrayList<>(List.of(
            new ProductoLambda("Pan", 100),
            new ProductoLambda("Leche", 150)
        ));

        double IVA = 0.21;
        
        // Mostrar nombre y precio con IVA (forEach con Lambda)
        System.out.println("Precios con IVA (21%):");
        productos.forEach(p -> {
            double precioConIva = p.getPrecio() * (1 + IVA);
            System.out.printf("%s: $%.2f (con IVA)\n", p.getNombre(), precioConIva);
        });

        // Mostrar precios originales (Método de Referencia estático)
        System.out.println("Precios Originales (Método por Referencia):");
        // Referenciamos el método estático 'mostrarPrecioOriginal' de la clase ProductoLambda
        productos.forEach(ProductoLambda::mostrarPrecioOriginal);
        System.out.println("-------------------------------------");
    }

    // --- 7.4 Lista de árboles ---
    public static void ejercicio7_4() {
        System.out.println("=== 7.4: Árboles y Edad ===");
        int anioActual = 2025; // Requisito del ejercicio
        List<Arbol> arboles = List.of(
            new Arbol("Pino", 2015),
            new Arbol("Roble", 1995)
        );

        // Lambda para imprimir cuántos años tiene cada árbol en 2025
        System.out.println("Edad de los árboles en 2025:");
        arboles.forEach(a -> {
            int edad = anioActual - a.anioPlantacion;
            System.out.println(a.especie + " tiene " + edad + " años.");
        });

        // Mostrar el contenido completo del objeto (Método de Referencia de instancia)
        System.out.println("Contenido completo (Método por Referencia toString):");
        // Usamos la referencia 'Objeto::metodoDeInstancia' (Object::toString)
        arboles.forEach(System.out::println); // System.out.println llama implícitamente a toString()
        System.out.println("-------------------------------------");
    }

    // --- 7.5 Empleados y sueldos ---
    public static void ejercicio7_5() {
        System.out.println("=== 7.5: Empleados y Sueldos ===");
        List<EmpleadoLambda> empleados = new ArrayList<>(List.of(
            new EmpleadoLambda("Elena", 150000),
            new EmpleadoLambda("Fernando", 250000),
            new EmpleadoLambda("Gaby", 190000)
        ));

        // Aumentar sueldo (Lambda)
        empleados.forEach(e -> {
            if (e.getSueldo() < 200000) {
                // Modificamos el estado del objeto en la lista
                e.sueldo = e.sueldo * 1.10; // Aumento del 10%
                System.out.println("Sueldo de " + e.nombre + " aumentado.");
            }
        });

        // Mostrar datos actualizados (Método de Referencia de instancia)
        System.out.println("\nDatos Actualizados (Método por Referencia de Instancia):");
        // Referenciamos el método 'mostrarDatosActualizados' de la instancia.
        empleados.forEach(EmpleadoLambda::mostrarDatosActualizados);
        System.out.println("-------------------------------------");
    }
}
9 & 10. Estructuras Dinámicas y ColeccionesEstos ejercicios se centran en el manejo de listas. El Ejercicio 9 simula la lógica de una lista dinámica sobre un array estático, y el Ejercicio 10 utiliza la colección ArrayList nativa de Java para simplificar la gestión.9.3 Transformar Lista Estática a PersonasEl ejercicio $\text{9.3}$ requiere modificar la clase DatosEstaticos para manejar objetos Persona en lugar de int1.Java// 9.3 Clase Persona para la lista estática
class PersonaLista {
    String nombre;
    String apellido;
    int dni; // Usado como índice/identificador (index)
    int edad;

    public PersonaLista(String nombre, String apellido, int dni, int edad) {
        this.nombre = nombre;
        this.apellido = apellido;
        this.dni = dni;
        this.edad = edad;
    }

    @Override
    public String toString() {
        return nombre + " (DNI:" + dni + ")";
    }

    // Usado en 9.2: El "mayor" elemento
    public int getDni() { return dni; }
}

// Clase transformada para manejar objetos Persona
class DatosEstaticosPersonas {
    private PersonaLista[] datos;
    private int size;

    public DatosEstaticosPersonas(int capacity) {
        // El array ahora guarda objetos PersonaLista
        this.datos = new PersonaLista[capacity];
        this.size = 0;
    }

    // 9.1 Implementación de insertar en posición específica
    // El método permite insertar un nuevo elemento en una posición específica[cite: 75].
    public boolean insert(int index, PersonaLista value) {
        // Si el índice es inválido (menor a 0 o mayor que el tamaño actual), no se modifica[cite: 76].
        if (index < 0 || index > size || size == datos.length) {
            System.out.println("Índice o Capacidad inválida para insertar.");
            return false;
        }

        // Desplazamos los elementos a la derecha para hacer un hueco
        for (int i = size; i > index; i--) {
            datos[i] = datos[i - 1];
        }
        
        datos[index] = value;
        size++;
        return true;
    }

    // 9.2 Implementa un método que devuelva el mayor elemento de la lista (por DNI)[cite: 77].
    public PersonaLista maximo() {
        // Si la lista está vacía debe devolver null[cite: 78].
        if (size == 0) return null;

        PersonaLista maxPersona = datos[0];
        // Buscamos el mayor DNI
        for (int i = 1; i < size; i++) {
            if (datos[i].getDni() > maxPersona.getDni()) {
                maxPersona = datos[i];
            }
        }
        return maxPersona;
    }

    // Métodos originales (add, remove, get) adaptados a PersonaLista
    public boolean add(PersonaLista value) {
        if (size < datos.length) {
            datos[size] = value;
            size++;
            return true;
        } else {
            return false;
        }
    }

    public void printAll() {
        for (int i = 0; i < size; i++) {
            System.out.print(datos[i] + (i < size - 1 ? ", " : ""));
        }
        System.out.println();
    }
}


public class Ejercicio9_ListaTransformada {
    public static void main(String[] args) {
        DatosEstaticosPersonas lista = new DatosEstaticosPersonas(5);
        
        // 9.3 Llenado de lista con objetos
        lista.add(new PersonaLista("Ana", "Gomez", 300, 25));
        lista.add(new PersonaLista("Beto", "Diaz", 100, 30));
        lista.add(new PersonaLista("Carlos", "Rios", 500, 40));
        lista.printAll();

        // 9.1 Prueba de insertar
        System.out.println("Insertando 'David' en índice 1...");
        lista.insert(1, new PersonaLista("David", "Perez", 250, 22));
        lista.printAll(); // Output: Ana, David, Beto, Carlos

        // 9.2 Prueba de máximo
        PersonaLista max = lista.maximo();
        System.out.println("Persona con mayor DNI: " + (max != null ? max.nombre : "N/A"));
        
    }
}
10.1 Sistema de gestión de productos de limpieza (ArrayList)El ejercicio $\text{10.1}$ usa ArrayList, que maneja el redimensionamiento y el desplazamiento de elementos automáticamente, a diferencia del ejercicio $\text{9.3}$.Java// Clase Producto (Identificador: Código)
class ProductoLimpieza {
    int codigo; // Identificador único [cite: 90]
    String nombre; // Cadena de texto [cite: 90]
    String marca; // Cadena de texto [cite: 90]
    double precio; // Número decimal [cite: 90]

    public ProductoLimpieza(int codigo, String nombre, String marca, double precio) {
        this.codigo = codigo;
        this.nombre = nombre;
        this.marca = marca;
        this.precio = precio;
    }

    public int getCodigo() { return codigo; }
    public String getNombre() { return nombre; }
    public void setPrecio(double precio) { this.precio = precio; }

    @Override
    public String toString() {
        return String.format("[Cód: %d] %s (%s) - $%.2f", codigo, nombre, marca, precio);
    }
}

public class Ejercicio10_ArrayList {

    // Usamos ArrayList para gestión dinámica [cite: 90]
    private static List<ProductoLimpieza> productos = new ArrayList<>();

    public static void main(String[] args) {
        // Simulamos el menú de opciones
        agregarProducto(101, "Detergente", "Magia", 500.50);
        agregarProducto(102, "Lavandina", "Claro", 200.00);
        agregarProducto(101, "Jabon", "Magia", 100.00); // Intento fallido
        
        listarProductos();
        
        System.out.println("\n--- Búsqueda ---");
        buscarProducto(102);
        
        System.out.println("\n--- Modificar Precio ---");
        modificarPrecio(101, 550.99);
        listarProductos();
        
        System.out.println("\n--- Eliminar Producto ---");
        eliminarProducto(102);
        listarProductos();
    }
    
    // 1. Agregar un nuevo producto y verificar que el código sea único [cite: 91]
    public static void agregarProducto(int codigo, String nombre, String marca, double precio) {
        // Verificar existencia por código
        boolean existe = productos.stream()
            .anyMatch(p -> p.getCodigo() == codigo);
        
        if (existe) {
            System.out.println("Error: Ya existe un producto con el código " + codigo);
        } else {
            productos.add(new ProductoLimpieza(codigo, nombre, marca, precio));
            System.out.println("Producto agregado con éxito.");
        }
    }

    // 2. Listar todos los productos [cite: 92]
    public static void listarProductos() {
        System.out.println("\n*** LISTADO DE PRODUCTOS (" + productos.size() + ") ***");
        if (productos.isEmpty()) {
            System.out.println("La lista de productos está vacía."); // Mostrar mensaje si vacía [cite: 92]
            return;
        }
        productos.forEach(System.out::println);
    }

    // 3. Buscar un producto por código [cite: 91]
    public static void buscarProducto(int codigo) {
        // Usamos stream y filter para buscar
        ProductoLimpieza encontrado = productos.stream()
            .filter(p -> p.getCodigo() == codigo)
            .findFirst() // Devuelve el primer resultado (Optional)
            .orElse(null); // O null si no se encuentra
        
        if (encontrado != null) {
            System.out.println("Encontrado: " + encontrado);
        } else {
            System.out.println("Producto con código " + codigo + " no encontrado.");
        }
    }

    // 4. Modificar el precio de un producto [cite: 91]
    public static void modificarPrecio(int codigo, double nuevoPrecio) {
        // Buscar el objeto por código y modificar su propiedad
        productos.stream()
            .filter(p -> p.getCodigo() == codigo)
            .findFirst()
            .ifPresentOrElse(
                p -> {
                    p.setPrecio(nuevoPrecio);
                    System.out.println("Precio de " + p.getNombre() + " modificado a $" + nuevoPrecio);
                },
                () -> System.out.println("No se puede modificar. Código " + codigo + " no encontrado.")
            );
    }

    // 5. Eliminar un producto por código [cite: 91]
    public static void eliminarProducto(int codigo) {
        // removeIf usa una expresión lambda como predicado de eliminación
        boolean removido = productos.removeIf(p -> p.getCodigo() == codigo);
        
        if (removido) {
            System.out.println("Producto con código " + codigo + " eliminado.");
        } else {
            System.out.println("No se encontró el producto para eliminar.");
        }
    }
}
<img width="1604" height="659" alt="image" src="https://github.com/user-attachments/assets/17c34c37-4b20-4778-9b61-eba672d17bb0" />

// Importa las clases que va a usar
import com.supermercado.gestion.Inventario; 
import com.supermercado.modelo.Producto;

public class MainApp {
    public static void main(String[] args) {
        Inventario inv = new Inventario();
        Producto p1 = new Producto();
        // ...
    }
}
