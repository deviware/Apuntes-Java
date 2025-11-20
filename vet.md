
import java.util.ArrayList;
import java.util.InputMismatchException;
import java.util.Objects;
import java.util.Scanner;
import java.util.function.Predicate;

// Justificación del contexto:
// Este sistema está pensado para una pequeña empresa de logística que necesita llevar un
// control simple de su flota de vehículos. La empresa maneja autos para gerentes,
// motos para mensajería y colectivos para el transporte de personal.

// --- INTERFACES ---

// Interfaz para que los vehículos tengan un identificador único (la patente)
interface Identificable {
    String getIdentificador();
}

// Interfaz para calcular el costo de mantenimiento (ejemplo de uso de interfaz)
@FunctionalInterface
interface CalculadorCosto {
    double calcular(Vehiculo v);
}

// --- EXCEPCIÓN PERSONALIZADA ---

// Excepción para cuando una patente no es válida
class PatenteInvalidaException extends Exception {
    public PatenteInvalidaException(String mensaje) {
        super(mensaje);
    }
}

// --- CLASE BASE VEHÍCULO ---

abstract class Vehiculo implements Identificable {
    // Atributos privados para encapsulamiento
    private String marca;
    private int anio; // Se cambió "modelo" por "año" que es más común
    private String patente;
    private int kilometraje;

    // Constructor parametrizado
    public Vehiculo(String marca, int anio, String patente, int kilometraje) {
        this.marca = marca;
        this.anio = anio;
        this.patente = patente.toUpperCase(); // La guardo en mayúsculas para ser consistente
        this.kilometraje = kilometraje;
    }

    // Getters y Setters
    public String getMarca() {
        return marca;
    }

    public void setMarca(String marca) {
        this.marca = marca;
    }

    public int getAnio() {
        return anio;
    }

    public void setAnio(int anio) {
        this.anio = anio;
    }

    public String getPatente() {
        return patente;
    }

    public void setPatente(String patente) {
        // Valido que la patente no sea nula o vacía
        if (patente != null && !patente.trim().isEmpty()) {
            this.patente = patente.toUpperCase();
        }
    }

    public int getKilometraje() {
        return kilometraje;
    }

    public void setKilometraje(int kilometraje) {
        this.kilometraje = kilometraje;
    }

    // --- MÉTODOS REQUERIDOS ---

    // Método abstracto que las subclases deben implementar (polimorfismo)
    public abstract String getTipoVehiculo();

    // Sobrescribiendo equals y hashCode para identificar por patente
    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        Vehiculo vehiculo = (Vehiculo) o;
        return patente.equals(vehiculo.patente);
    }

    @Override
    public int hashCode() {
        return Objects.hash(patente);
    }

    // Implementación del método de la interfaz Identificable
    @Override
    public String getIdentificador() {
        return this.patente;
    }

    @Override
    public String toString() {
        return String.format("Patente: %s, Marca: %s, Año: %d, Km: %d",
                patente, marca, anio, kilometraje);
    }

    // Sobrecarga de método: mostrar info básica o completa
    public void mostrarInfo() {
        System.out.printf("Vehículo Patente: %s (%s, %d)\n", this.patente, this.marca, this.anio);
    }

    public void mostrarInfo(boolean detallada) {
        if (detallada) {
            System.out.println("--- Ficha del Vehículo ---");
            System.out.printf("Tipo: %s\n", this.getTipoVehiculo());
            System.out.printf("Patente: %s\n", this.patente);
            System.out.printf("Marca: %s\n", this.marca);
            System.out.printf("Año: %d\n", this.anio);
            System.out.printf("Kilometraje: %d km\n", this.kilometraje);
        } else {
            this.mostrarInfo();
        }
    }
}

// --- SUBCLASES ---

class Auto extends Vehiculo {
    private int cantPuertas;

    public Auto(String marca, int anio, String patente, int kilometraje, int cantPuertas) {
        super(marca, anio, patente, kilometraje);
        this.cantPuertas = cantPuertas;
    }

    @Override
    public String getTipoVehiculo() {
        return "Auto";
    }

    @Override
    public String toString() {
        return super.toString() + ", Puertas: " + cantPuertas;
    }
}

class Moto extends Vehiculo {
    public Moto(String marca, int anio, String patente, int kilometraje) {
        super(marca, anio, patente, kilometraje);
    }

    @Override
    public String getTipoVehiculo() {
        return "Moto";
    }
}

class Colectivo extends Vehiculo {
    private int cantAsientos;

    public Colectivo(String marca, int anio, String patente, int kilometraje, int cantAsientos) {
        super(marca, anio, patente, kilometraje);
        this.cantAsientos = cantAsientos;
    }

    @Override
    public String getTipoVehiculo() {
        return "Colectivo";
    }
     @Override
    public String toString() {
        return super.toString() + ", Asientos: " + cantAsientos;
    }
}

// --- CLASE PRINCIPAL DEL SISTEMA ---

public class SistemaDeVehiculos {

    // Variable global para la lista de vehículos (ArrayList)
    private static ArrayList<Vehiculo> flota = new ArrayList<>();
    private static Scanner scanner = new Scanner(System.in);

    public static void main(String[] args) {
        // Precargamos algunos datos para que no esté vacío
        cargarDatosDeEjemplo();

        int opcion;
        do {
            mostrarMenu();
            opcion = leerOpcion();

            // Switch para manejar las opciones del menú
            switch (opcion) {
                case 1:
                    crearVehiculo();
                    break;
                case 2:
                    buscarVehiculoPorPatente();
                    break;
                case 3:
                    actualizarVehiculo();
                    break;
                case 4:
                    eliminarVehiculo();
                    break;
                case 5:
                    mostrarTodosLosVehiculos();
                    break;
                case 6:
                    contarVehiculosPorTipo();
                    break;
                case 7:
                    System.out.println("Saliendo del sistema...");
                    break;
                default:
                    System.out.println("Opción no válida. Intente de nuevo.");
            }
            System.out.println(); // un espacio para que no quede todo pegado

        } while (opcion != 7);

        scanner.close();
    }

    // --- MÉTODOS DEL SISTEMA ---

    private static void mostrarMenu() {
        System.out.println("--- Sistema de Gestión de Vehículos ---");
        System.out.println("1. Registrar nuevo vehículo");
        System.out.println("2. Buscar vehículo por patente");
        System.out.println("3. Actualizar datos de un vehículo");
        System.out.println("4. Eliminar vehículo");
        System.out.println("5. Mostrar todos los vehículos");
        System.out.println("6. Contar vehículos por tipo (recursivo)");
        System.out.println("7. Salir");
        System.out.print("Elija una opción: ");
    }

    private static int leerOpcion() {
        int opcion = -1;
        // Bucle while para asegurar que se ingrese un número
        while (opcion == -1) {
            try {
                opcion = scanner.nextInt();
            } catch (InputMismatchException e) {
                System.out.print("Error: debe ingresar un número. Intente de nuevo: ");
                scanner.next(); // Limpio el buffer del scanner
                continue; // Vuelvo al inicio del while
            }
        }
        scanner.nextLine(); // Consumo el salto de línea
        return opcion;
    }
    
    // 1. CREAR
    private static void crearVehiculo() {
        System.out.println("\n--- Registro de Nuevo Vehículo ---");
        System.out.print("Tipo de vehículo (1: Auto, 2: Moto, 3: Colectivo): ");
        int tipo = leerOpcion();

        try {
            System.out.print("Ingrese Patente: ");
            String patente = scanner.nextLine();
            validarPatente(patente); // Lanzo excepción si es inválida o duplicada

            // Uso de anyMatch con lambda para verificar si ya existe
            if (flota.stream().anyMatch(v -> v.getPatente().equalsIgnoreCase(patente))) {
                System.out.println("Error: La patente " + patente.toUpperCase() + " ya existe.");
                return;
            }

            System.out.print("Ingrese Marca: ");
            String marca = scanner.nextLine();
            System.out.print("Ingrese Año: ");
            int anio = scanner.nextInt();
            System.out.print("Ingrese Kilometraje: ");
            int km = scanner.nextInt();
            scanner.nextLine();

            Vehiculo nuevoVehiculo = null;
            // Uso de switch para crear el tipo de vehículo correcto
            switch (tipo) {
                case 1:
                    System.out.print("Ingrese cantidad de puertas: ");
                    int puertas = scanner.nextInt();
                    scanner.nextLine();
                    nuevoVehiculo = new Auto(marca, anio, patente, km, puertas);
                    break;
                case 2:
                    nuevoVehiculo = new Moto(marca, anio, patente, km);
                    break;
                case 3:
                    System.out.print("Ingrese cantidad de asientos: ");
                    int asientos = scanner.nextInt();
                    scanner.nextLine();
                    nuevoVehiculo = new Colectivo(marca, anio, patente, km, asientos);
                    break;
                default:
                    System.out.println("Tipo de vehículo no válido.");
                    return; // break no es suficiente, tengo que salir del método
            }
            flota.add(nuevoVehiculo);
            System.out.println("¡Vehículo registrado con éxito!");

        } catch (PatenteInvalidaException e) {
            System.out.println("Error de validación: " + e.getMessage());
        } catch (InputMismatchException e) {
            System.out.println("Error: Ingresó un formato de número incorrecto.");
            scanner.next();
        } finally {
            System.out.println("Fin del proceso de registro."); // finally para mostrar que el bloque terminó
        }
    }

    // Método para demostrar el try-catch y la excepción personalizada
    private static void validarPatente(String patente) throws PatenteInvalidaException {
        // Uso de contains para una validación simple
        if (patente == null || patente.trim().length() < 6 || patente.contains(" ")) {
            throw new PatenteInvalidaException("La patente debe tener al menos 6 caracteres y no contener espacios.");
        }
    }

    // 2. LEER (búsqueda recursiva)
    private static void buscarVehiculoPorPatente() {
        System.out.print("\nIngrese la patente a buscar: ");
        String patente = scanner.nextLine().toUpperCase();
        
        Vehiculo encontrado = buscarRecursivo(patente, 0);

        if (encontrado != null) {
            System.out.println("Vehículo encontrado:");
            encontrado.mostrarInfo(true); // Uso del método sobrecargado
        } else {
            System.out.println("No se encontró ningún vehículo con la patente " + patente);
        }
    }

    // Función recursiva para buscar en el ArrayList
    private static Vehiculo buscarRecursivo(String patente, int indice) {
        // Caso base: si el índice se pasa del tamaño de la lista, no se encontró
        if (indice >= flota.size()) {
            return null;
        }
        // Caso base: si encuentro el vehículo, lo devuelvo
        Vehiculo actual = flota.get(indice);
        if (actual.getPatente().equalsIgnoreCase(patente)) {
            return actual;
        }
        // Caso recursivo: llamo a la función con el siguiente índice
        return buscarRecursivo(patente, indice + 1);
    }
    
    // 3. ACTUALIZAR (demuestra paso por referencia)
    private static void actualizarVehiculo() {
        System.out.print("\nIngrese la patente del vehículo a actualizar: ");
        String patente = scanner.nextLine().toUpperCase();

        Vehiculo vehiculo = buscarRecursivo(patente, 0);

        if (vehiculo != null) {
            System.out.println("Vehículo encontrado. Ingrese los nuevos datos.");
            // Aquí se demuestra el paso por referencia: el objeto "vehiculo" es una referencia
            // al objeto que está DENTRO de la lista "flota". Si lo modifico, se modifica en la lista.
            modificarDatos(vehiculo);
            System.out.println("Vehículo actualizado con éxito.");
        } else {
            System.out.println("Vehículo no encontrado.");
        }
    }

    // Método que modifica un objeto, demostrando el paso por referencia
    private static void modificarDatos(Vehiculo v) {
        System.out.print("Nuevo kilometraje (actual: " + v.getKilometraje() + "): ");
        int nuevoKm = scanner.nextInt();
        scanner.nextLine(); // limpiar buffer
        v.setKilometraje(nuevoKm);

        System.out.print("Nueva marca (actual: " + v.getMarca() + "): ");
        String nuevaMarca = scanner.nextLine();
        v.setMarca(nuevaMarca);
    }

    // 4. ELIMINAR
    private static void eliminarVehiculo() {
        System.out.print("\nIngrese la patente del vehículo a eliminar: ");
        String patente = scanner.nextLine().toUpperCase();

        // Uso de removeIf con una expresión lambda como predicado
        boolean eliminado = flota.removeIf(v -> v.getPatente().equalsIgnoreCase(patente));

        if (eliminado) {
            System.out.println("Vehículo eliminado correctamente.");
        } else {
            System.out.println("No se encontró un vehículo con esa patente.");
        }
    }
    
    // 5. MOSTRAR TODOS
    private static void mostrarTodosLosVehiculos() {
        System.out.println("\n--- Listado de Todos los Vehículos ---");
        if (flota.isEmpty()) {
            System.out.println("No hay vehículos registrados en la flota.");
            return;
        }
        // Uso de forEach con una expresión lambda para recorrer la lista
        flota.forEach(v -> System.out.println(v.toString()));
        
        // Ejemplo de uso de filter y forEach para mostrar solo los autos
        System.out.println("\n--- Filtrando solo Autos ---");
        flota.stream()
             .filter(v -> v instanceof Auto)
             .forEach(v -> System.out.println(v.getIdentificador() + " - " + v.getMarca()));
    }

    // 6. CONTAR (recursivo)
    private static void contarVehiculosPorTipo() {
         System.out.print("\n¿Qué tipo de vehículo desea contar? (Auto, Moto, Colectivo): ");
         String tipo = scanner.nextLine();
         
         // Creamos un predicado (lambda) para la condición
         Predicate<Vehiculo> condicion = v -> v.getTipoVehiculo().equalsIgnoreCase(tipo);
         
         int cantidad = contarRecursivo(condicion, 0);
         System.out.printf("Hay %d vehículos del tipo '%s'.\n", cantidad, tipo);
    }

    // Función recursiva que cuenta elementos que cumplen una condición
    private static int contarRecursivo(Predicate<Vehiculo> condicion, int indice) {
        // Caso base: si llegamos al final de la lista
        if (indice >= flota.size()) {
            return 0;
        }
        // Verifico si el elemento actual cumple la condición
        int actual = condicion.test(flota.get(indice)) ? 1 : 0;
        
        // Caso recursivo: sumo el actual (0 o 1) con el resultado del resto de la lista
        return actual + contarRecursivo(condicion, indice + 1);
    }
    
    private static void cargarDatosDeEjemplo() {
        flota.add(new Auto("Ford", 2020, "AE123FD", 50000, 5));
        flota.add(new Moto("Honda", 2022, "A123BKT", 15000));
        flota.add(new Colectivo("Mercedes Benz", 2018, "AC456GT", 200000, 40));
        flota.add(new Auto("Chevrolet", 2021, "AF789CZ", 40000, 4));
    }
}


1. Importaciones (librerías)
import java.util.ArrayList;
import java.util.InputMismatchException;
import java.util.Objects;
import java.util.Scanner;
import java.util.function.Predicate;


ArrayList:
Estructura de datos dinámica de Java (colecciones – Unidad 4).
La usamos como “base de datos en memoria” para guardar todos los vehículos.

InputMismatchException:
Excepción que lanza Scanner cuando alguien mete un tipo de dato incorrecto (por ejemplo, letras donde esperaba un int).
Sirve para capturar errores de carga por teclado (Unidad 5).

Objects:
Se usa para ayudar con hashCode() y, en general, para operaciones con objetos.
En tu código lo usás en Objects.hash(patente) dentro de hashCode().

Scanner:
Clase para leer datos desde teclado. Es fundamental para hacer menú por consola (Unidad 2).

Predicate (de java.util.function):
Es una interfaz funcional que representa una condición booleana test(T t).
La usás para hacer un contador recursivo con condición (contarRecursivo), mezclando recursividad + lambdas (Unidad 3/4).

2. Comentario de contexto
// Este sistema está pensado para una pequeña empresa de logística...


Justificación que pide el enunciado del parcial / TPI:
explicar en qué contexto se usa el sistema (empresa de logística, flota de vehículos).

Sirve para:

demostrar que estás modelando un problema real con clases (Unidad 3: modelado).

3. Interfaces
3.1 Identificable
interface Identificable {
    String getIdentificador();
}


Interfaz simple, con un solo método: getIdentificador().

La implementa Vehiculo, devolviendo la patente como identificador único.

Cumple con:

creación de una interfaz (Unidad 3),

y sirve también para mostrar polimorfismo por interfaz.

3.2 CalculadorCosto
@FunctionalInterface
interface CalculadorCosto {
    double calcular(Vehiculo v);
}


Marcada con @FunctionalInterface: solo un método abstracto → se puede usar con expresiones lambda.

Representa algo que calcula un costo a partir de un Vehiculo.

En este código no la estás usando todavía, pero:

demuestra que sabés definir una interfaz funcional (Unidad 3),

se podría usar con un lambda tipo:
CalculadorCosto c = v -> v.getKilometraje() * 1.5;

4. Excepción personalizada
class PatenteInvalidaException extends Exception {
    public PatenteInvalidaException(String mensaje) {
        super(mensaje);
    }
}


Extiende de Exception → excepción chequeada.

Sirve para validar patentes: si no cumple la condición, lanzo esta excepción.

Demuestra:

manejo de excepciones,

throw / throws,

creación de excepción personalizada (Unidad 5).

5. Clase base Vehiculo (POO full)
abstract class Vehiculo implements Identificable {
    private String marca;
    private int anio;
    private String patente;
    private int kilometraje;
    ...
}

5.1 Atributos privados

marca, anio, patente, kilometraje son private.
→ Encapsulamiento: solo se accede a través de getters/setters.

5.2 Constructor parametrizado
public Vehiculo(String marca, int anio, String patente, int kilometraje) {
    this.marca = marca;
    this.anio = anio;
    this.patente = patente.toUpperCase();
    this.kilometraje = kilometraje;
}


Recibe todos los datos → constructor parametrizado (Unidad 3).

Pasa de parámetros a atributos con this.

patente.toUpperCase() → normalizás la patente a mayúsculas para evitar inconsistencias.

5.3 Getters y setters
public String getMarca() { ... }
public void setMarca(String marca) { ... }
...
public void setPatente(String patente) {
    if (patente != null && !patente.trim().isEmpty()) {
        this.patente = patente.toUpperCase();
    }
}


Aplica encapsulamiento:
variables privadas + acceso controlado.

En setPatente hacés validación mínima, evitando patentes vacías.

5.4 Método abstracto (polimorfismo)
public abstract String getTipoVehiculo();


Hace que Vehiculo sea abstracta.

Obliga a las subclases a definir qué tipo son: "Auto", "Moto", "Colectivo".

Demuestra polimorfismo dinámico: según el objeto concreto, el método se comporta distinto.

5.5 equals y hashCode
@Override
public boolean equals(Object o) {
    if (this == o) return true;
    if (o == null || getClass() != o.getClass()) return false;
    Vehiculo vehiculo = (Vehiculo) o;
    return patente.equals(vehiculo.patente);
}

@Override
public int hashCode() {
    return Objects.hash(patente);
}


Dos vehículos son iguales si tienen la misma patente.

Cumple con:

comparación correcta en colecciones,

requisito de la cátedra (Unidad 4: equals/hashCode).

Objects.hash(patente) es una forma cómoda de generar el hash.

5.6 Implementación de la interfaz Identificable
@Override
public String getIdentificador() {
    return this.patente;
}


Indica que el identificador único del vehículo es la patente.

5.7 toString() para mostrar info
@Override
public String toString() {
    return String.format("Patente: %s, Marca: %s, Año: %d, Km: %d",
            patente, marca, anio, kilometraje);
}


Sirve para mostrar un vehículo de forma legible.

Se usa en mostrarTodosLosVehiculos().

5.8 Sobrecarga de método mostrarInfo
public void mostrarInfo() { ... }
public void mostrarInfo(boolean detallada) { ... }


Sobrecarga: mismo nombre, distinta firma.

Si detallada = true, mostrás una ficha completa.

Si false, mostrás algo más resumido (o llamás al otro método).

6. Subclases: Auto, Moto, Colectivo
6.1 Auto
class Auto extends Vehiculo {
    private int cantPuertas;

    public Auto(String marca, int anio, String patente, int kilometraje, int cantPuertas) {
        super(marca, anio, patente, kilometraje);
        this.cantPuertas = cantPuertas;
    }

    @Override
    public String getTipoVehiculo() {
        return "Auto";
    }

    @Override
    public String toString() {
        return super.toString() + ", Puertas: " + cantPuertas;
    }
}


extends Vehiculo → herencia.

Atributo como extensión: cantPuertas.

Redefinís getTipoVehiculo() (polimorfismo).

Redefinís toString() agregando info específica.

6.2 Moto
class Moto extends Vehiculo {
    public Moto(String marca, int anio, String patente, int kilometraje) {
        super(marca, anio, patente, kilometraje);
    }

    @Override
    public String getTipoVehiculo() {
        return "Moto";
    }
}


No tiene atributos extra, solo redefine getTipoVehiculo().

6.3 Colectivo
class Colectivo extends Vehiculo {
    private int cantAsientos;

    public Colectivo(String marca, int anio, String patente, int kilometraje, int cantAsientos) {
        super(marca, anio, patente, kilometraje);
        this.cantAsientos = cantAsientos;
    }

    @Override
    public String getTipoVehiculo() {
        return "Colectivo";
    }

    @Override
    public String toString() {
        return super.toString() + ", Asientos: " + cantAsientos;
    }
}


Atributo extra: cantAsientos.

Redefinís tipo + toString().

7. Clase principal SistemaDeVehiculos
public class SistemaDeVehiculos {
    private static ArrayList<Vehiculo> flota = new ArrayList<>();
    private static Scanner scanner = new Scanner(System.in);
    ...
}


flota es la lista global de vehículos:

static para que sea accesible desde todos los métodos.

Es la “base de datos” del sistema.

scanner también es static para usarlo desde cualquier método.

8. Método main
public static void main(String[] args) {
    cargarDatosDeEjemplo();

    int opcion;
    do {
        mostrarMenu();
        opcion = leerOpcion();

        switch (opcion) {
            case 1: crearVehiculo(); break;
            case 2: buscarVehiculoPorPatente(); break;
            case 3: actualizarVehiculo(); break;
            case 4: eliminarVehiculo(); break;
            case 5: mostrarTodosLosVehiculos(); break;
            case 6: contarVehiculosPorTipo(); break;
            case 7: System.out.println("Saliendo del sistema..."); break;
            default: System.out.println("Opción no válida. Intente de nuevo.");
        }
        System.out.println();

    } while (opcion != 7);

    scanner.close();
}


do-while: se repite hasta que el usuario elige salir (7).

switch: controla la lógica del menú.

Llama a distintos métodos → subprogramas (Unidad 2).

9. mostrarMenu y leerOpcion
private static void mostrarMenu() { ... }

private static int leerOpcion() {
    int opcion = -1;
    while (opcion == -1) {
        try {
            opcion = scanner.nextInt();
        } catch (InputMismatchException e) {
            System.out.print("Error: debe ingresar un número. Intente de nuevo: ");
            scanner.next();
            continue;
        }
    }
    scanner.nextLine();
    return opcion;
}


Menú impreso por consola con println.

leerOpcion():

Usa while + try/catch.

Si el usuario escribe cualquier cosa que no sea número, cae en InputMismatchException.

Limpiás el buffer con scanner.next() y volvés a pedir.

Demuestra:

manejo de excepciones,

validación de entrada,

uso de continue.

10. crearVehiculo (Create del CRUD)
private static void crearVehiculo() { ... }


Hace:

Pide tipo de vehículo (1,2,3).

Pide patente, la valida con validarPatente(patente) → puede lanzar PatenteInvalidaException.

Revisa con anyMatch si la patente ya existe:

if (flota.stream().anyMatch(v -> v.getPatente().equalsIgnoreCase(patente)))


→ Ejemplo de lambda + stream + anyMatch.

Pide marca, año, km.

Según tipo hace un switch y crea:

Auto, Moto o Colectivo.

Agrega a la flota.

Maneja excepciones:

PatenteInvalidaException,

InputMismatchException.

finally: imprime "Fin del proceso de registro." sí o sí.

11. validarPatente
private static void validarPatente(String patente) throws PatenteInvalidaException {
    if (patente == null || patente.trim().length() < 6 || patente.contains(" ")) {
        throw new PatenteInvalidaException("La patente debe tener al menos 6 caracteres y no contener espacios.");
    }
}


Valida reglas mínimas:

no nula,

sin espacios,

largo mínimo.

Si no cumple → throw new PatenteInvalidaException(...).

Demuestra: throws + throw + excepción personalizada (Unidad 5).

12. buscarVehiculoPorPatente + buscarRecursivo
private static void buscarVehiculoPorPatente() { ... }

private static Vehiculo buscarRecursivo(String patente, int indice) { ... }


Pide patente.

Llama a una función recursiva:

caso base: indice >= flota.size() → no encontró.

caso base 2: si la patente coincide → devuelve el vehículo.

caso recursivo: llama con indice + 1.

Si encontró, usa mostrarInfo(true) (sobrecarga + polimorfismo).

13. actualizarVehiculo + modificarDatos
private static void actualizarVehiculo() { ... }

private static void modificarDatos(Vehiculo v) { ... }


Busca el vehículo por patente (usando la recursiva).

Si lo encuentra, pide nuevos datos:

nuevo kilometraje,

nueva marca.

Llama a modificarDatos(v):

como v es una referencia, modificarlo modifica el objeto en la lista → demuestra paso por referencia a nivel objeto (Unidad 2/3).

14. eliminarVehiculo
private static void eliminarVehiculo() {
    ...
    boolean eliminado = flota.removeIf(v -> v.getPatente().equalsIgnoreCase(patente));
    ...
}


Usa removeIf con una lambda:

recorre la lista y elimina todo lo que cumpla la condición.

Devuelve true si borró algo.

Muestra cómo usar colecciones + lambdas (Unidad 3/4).

15. mostrarTodosLosVehiculos
private static void mostrarTodosLosVehiculos() {
    ...
    flota.forEach(v -> System.out.println(v.toString()));

    System.out.println("\n--- Filtrando solo Autos ---");
    flota.stream()
         .filter(v -> v instanceof Auto)
         .forEach(v -> System.out.println(v.getIdentificador() + " - " + v.getMarca()));
}


Si la lista está vacía, avisa y sale.

Recorre la lista con forEach y una lambda.

Después hace:

flota.stream().filter(v -> v instanceof Auto)...
→ Usa stream + filter + forEach para mostrar solo autos.

16. contarVehiculosPorTipo + contarRecursivo
private static void contarVehiculosPorTipo() {
    ...
    Predicate<Vehiculo> condicion = v -> v.getTipoVehiculo().equalsIgnoreCase(tipo);
    int cantidad = contarRecursivo(condicion, 0);
    ...
}

private static int contarRecursivo(Predicate<Vehiculo> condicion, int indice) { ... }


Pide tipo: "Auto", "Moto", "Colectivo".

Crea un Predicate<Vehiculo> con una lambda que compara getTipoVehiculo() con el tipo ingresado.

Llama a una función recursiva:

caso base: indice >= flota.size() → 0.

caso recursivo:

suma 1 si el vehículo en esa posición cumple la condición, si no 0.

devuelve actual + contarRecursivo(... indice + 1).

Esto mezcla:

recursividad,

interfaz funcional,

lambdas,

listas → todo adentro del programa de la cátedra.

17. cargarDatosDeEjemplo
private static void cargarDatosDeEjemplo() {
    flota.add(new Auto("Ford", 2020, "AE123FD", 50000, 5));
    flota.add(new Moto("Honda", 2022, "A123BKT", 15000));
    flota.add(new Colectivo("Mercedes Benz", 2018, "AC456GT", 200000, 40));
    flota.add(new Auto("Chevrolet", 2021, "AF789CZ", 40000, 4));
}


Solo sirve para que el sistema no arranque vacío.

Es útil para probar rápidamente los métodos sin tener que cargar todo a mano cada vez.
