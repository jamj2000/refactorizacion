# Refactorización de código


## Renombrar variables y hacerlas descriptivas

```java
// Código original
public double calcular(double[] nums) {
    double sum = 0;
    for (int i = 0; i < nums.length; i++) {
        sum += nums[i];
    }
    return sum / nums.length;
}

// Refactorizado
public double calcularPromedio(double[] numeros) {
    double sumaTotal = 0;
    for (int indice = 0; indice < numeros.length; indice++) {
        sumaTotal += numeros[indice];
    }
    return sumaTotal / numeros.length;
}
```

## Eliminar Código Muerto / Almacenamiento muerto 

En programación, se conoce como código muerto a una parte del código fuente que se ejecuta pero sus resultados nunca se usan.​ La ejecución de este tipo de código consume tiempo de computo en algo que jamás se utiliza.

```java
int suma (int numero1, int numero2) {
    int resultado = numero1 * numero2;       // Esta línea puede eliminarse
    return numero1 + numero2;
}
```

## Código inalcanzable

En programación, el código inalcanzable es una parte del código fuente que nunca podrá ser ejecutado porque no existe ningún camino dentro de las estructuras de control en el resto del programa para llegar a este código.

```java
int multiplica(int numero1, int numero2) {
    return numero1 * numero2;
    int  = numero1 / numero2;     // Esta línea puede eliminarse
}
```


## Eliminar Código Redundante
En programación, se conoce como código redundante a cualquier parte del código fuente que tenga algún tipo de redundancia tales como recalcular un valor que ha sido calculado previamente y todavía está disponible.​

```java
int suma (int numero1, int numero2) {
    return numero1 + numero2;
    int resultado = numero1 + numero2;       // Esta línea puede eliminarse
}
```

## Reemplazar Número Mágico con Constante Simbólica

```java
// Código original
public double calcularDescuento(double precio) {
    return precio * 0.1;   // 0.1 es un número mágico que representa el 10% de descuento
}

// Refactorizado
private static final double DESCUENTO_PORCENTUAL = 0.1;

public double calcularDescuento(double precio) {
    return precio * DESCUENTO_PORCENTUAL;
}
```

```java
// Código original
public double CalcularAreaCirculo(double radio) {
    return 3.14 * radio * radio;
}

// Refactorizado
public double calcularAreaCirculo(double radio) {
    return Math.PI * radio * radio;
}
```


## Simplificación de expresiones condicionales

Simplifica las expresiones condicionales complejas para mejorar la legibilidad del código y reducir la posibilidad de errores.

```java
// Código original
public String obtenerResultadoExamen(int puntaje) {
    if (puntaje >= 70) {
        return "Aprobado";
    } else {
        return "Reprobado";
    }
}

// Refactorizado
public String obtenerResultadoExamen(int puntaje) {
    return puntaje >= 70 ? "Aprobado" : "Reprobado";
}
```

```java
// Código original
public String obtenerMensaje(boolean esSaludo) {
    if (esSaludo) {
        return "Hola";
    } else {
        return "Adiós";
    }
}

// Refactorizado
public String obtenerMensaje(boolean esSaludo) {
    return esSaludo ? "Hola" : "Adiós";
}
```


## Método inline

```java
// Código original
public boolean esMayorDeEdad(int edad) {
    return edad >= 18;
}

// Código refactorizado
// Dado que el método esMayorDeEdad es muy simple y se usa en pocos lugares,
// puede ser innecesario, y es mejor utilizar la expresión directamente donde se necesite.
```

## Extraer Clase

```java
// Código original
public class Estudiante {
    private String nombre;
    private int edad;
    private String direccion;

    // métodos para acceder y modificar atributos
}

// Refactorizado
public class Estudiante {
    private DatosPersonales datosPersonales;

    // métodos para acceder y modificar los datos personales
}

public class DatosPersonales {
    private String nombre;
    private int edad;
    private String direccion;

    // métodos para acceder y modificar los atributos
}
```


## Reemplazar Condicional con Polimorfismo

```java
// Código original
public class Forma {
    private String tipo;

    public double calcularArea() {
        if (tipo.equals("círculo")) {
            return Math.PI * radio * radio;
        } else if (tipo.equals("cuadrado")) {
            return lado * lado;
        }
        // más casos...
    }
}

// Refactorizado
public abstract class Forma {
    public abstract double calcularArea();
}

public class Circulo extends Forma {
    private double radio;

    @Override
    public double calcularArea() {
        return Math.PI * radio * radio;
    }
}

public class Cuadrado extends Forma {
    private double lado;

    @Override
    public double calcularArea() {
        return lado * lado;
    }
}
```
