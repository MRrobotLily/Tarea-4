# Ejercicio #1

## Subsidio Familiar en C++ y Python

Escriba una aplicación en c++ y Python para resolver el siguiente enunciado. El gobierno ha implementado como parte de su programa social, un subsidio familiar bajo la siguiente reglamentación: Las familias que tienen hasta 2 hijos, reciben Q. 70.00, las que tienen hasta 3 y 5 reciben Q. 90.00 y las que tienen 6 o más reciben Q. 120 mensual. Por cada hijo en edad escolar reciben Q. 10.00 adicionales.

Se considera la edad escolar entre 6 y 18 años. Si la madre de familia fuera viuda, la familia recibe Q.20.00 adicionales. Determinar el monto mensual que recibirá una familia de acuerdo a su realidad familiar a través de una función llamada calcularSubsidio.
##
En el siguiente algoritmo se le da la bienvenida al usuario y le va a pedir que ingrese los datos en base a las preguntas establecidas.

[![Whats-App-Image-2023-10-05-at-21-25-52-b4c391c8.jpg](https://i.postimg.cc/cCfHkC8Y/Whats-App-Image-2023-10-05-at-21-25-52-b4c391c8.jpg)](https://postimg.cc/30JYdK1J)

- *Informacion del usuario*:

 Solicita al usuario ingresar un listado de información la cual esta compuesta por: 
  * Numero de hijos
  * Edad escolar de los hijos 
  * Si la madre es viuda o no

  - En base a la informacion ingresada se hace una serie de pasos en la cual si el usuario tiene menos de dos hijos se le estara mostrando la cantidad de Q90 si tiene de 3 a 5 se mostrara 90 y si tiene de 6 o mas se mostrara Q120. Esto se guarda.
* Luego el algoritmo verifica si la edad el niño esta dentro del rango establecido de 6 a 18, si esto es valido el programa mostrara Q10 por cada hijo del usuario. De lo contrario mostrara la cantidad Q0.

* Verifica si la madre es viuda se le agrega otra cantidad de 20 quetzales de lo contrario mostrara Q0.

* Por ultimo el algoritmo sumara el resultado de cada pregunta para mostrar el subcidio familiar de la familia. 
    en caso que el usuario coloque 0 o no este dentro del rango establecido .

*Ejemplos:*

Usuario ingresa 0 en hijos y responde las preguntas con un rango establecido, al final el programa mostrara un mensaje que no tiene hijos por lo tanto el monto es de 0 quetzales. 

[![Whats-App-Image-2023-10-05-at-22-55-46-04f255cb.jpg](https://i.postimg.cc/KYkCXHm7/Whats-App-Image-2023-10-05-at-22-55-46-04f255cb.jpg)](https://postimg.cc/sBzT7KQ1)

Usuario ingresa 2 hijos con la edad entre 6 a 18 años siendo la madre viuda. 

[![Whats-App-Image-2023-10-05-at-22-55-46-f5c3f165.jpg](https://i.postimg.cc/tTGSKRSy/Whats-App-Image-2023-10-05-at-22-55-46-f5c3f165.jpg)](https://postimg.cc/8FwmWGgn)

Usuario ingresa el rango de 3 a 5 hijos con la edad escolar entre  6 a 18 años no siendo la madre viuda.

[![Whats-App-Image-2023-10-05-at-23-02-43-22313f96.jpg](https://i.postimg.cc/wjJDSXSy/Whats-App-Image-2023-10-05-at-23-02-43-22313f96.jpg)](https://postimg.cc/5X4HzC9b)

Usuario ingresa mas de 6 hijos fuera de la edad escolar siendo la madre viuda:

[![Whats-App-Image-2023-10-05-at-23-04-48-368e6d77.jpg](https://i.postimg.cc/T3rWkRDn/Whats-App-Image-2023-10-05-at-23-04-48-368e6d77.jpg)](https://postimg.cc/TK3w1vQP)

##
# Codigo Fuente C++

```
#include <iostream>

using namespace std;

// Función para calcular el subsidio familiar
int calcularSubsidio(int numeroHijos, int edadEscolar, bool madreViuda) {
	    if (numeroHijos == 0) {
        cout << "No tiene hijos, el monto es 0 quetzales." << endl;
        return 0;
    }
    
    int montoBase = 0;

    // Determinar el monto base según la cantidad de hijos
    if (numeroHijos <= 2) {
        montoBase = 70;
        cout << "Monto base por hasta 2 hijos: " << montoBase << " quetzales." << endl;
    } else if (numeroHijos >= 3 && numeroHijos <= 5) {
        montoBase = 90;
        cout << "Monto base por 3 a 5 hijos: " << montoBase << " quetzales." << endl;
    } else {
        montoBase = 120;
        cout << "Monto base por 6 o mas hijos: " << montoBase << " quetzales." << endl;
    }

    // Agregar monto adicional por hijos en edad escolar (si están en el rango de edad)
    int montoPorEdadEscolar = (edadEscolar >= 6 && edadEscolar <= 18) ? (numeroHijos * 10) : 0;
    if (montoPorEdadEscolar > 0) {
        cout << "Monto adicional por hijos en edad escolar: " << montoPorEdadEscolar << " quetzales." << endl;
    }

    // Agregar monto adicional por madre viuda o establecer en 0 si no es viuda
    int montoPorMadreViuda = madreViuda ? 20 : 0;
    if (madreViuda) {
        cout << "Monto adicional por madre viuda: 20 quetzales." << endl;
    } else {
        cout << "No es madre viuda, el monto es 0 quetzales." << endl;
    }

    // Calcular el monto total
    int montoTotal = montoBase + montoPorEdadEscolar + montoPorMadreViuda;

    return montoTotal;
}

int main() {
    int numeroHijos, edadEscolar;
    bool madreViuda;

	cout << "**BIENVENIDO AL SUBSIDIO FAMILIAR**" << endl;
	cout << "Responda las siguientes preguntas:" << endl;
    cout << "Ingrese el numero de hijos: ";
    cin >> numeroHijos;

    cout << "Ingrese la edad escolar de los hijos: ";
    cin >> edadEscolar;

    cout << "La madre es viuda? (1 para si, 0 para no): ";
    cin >> madreViuda;

    // Calcular el monto mensual de subsidio familiar
    int montoSubsidio = calcularSubsidio(numeroHijos, edadEscolar, madreViuda);

    // Mostrar el monto mensual de subsidio familiar
    cout << "El monto mensual de subsidio familiar es: " << montoSubsidio << " quetzales." << endl;

    return 0;
}
```

# Codigo Fuente Python
```
# Función para calcular el subsidio familiar
def calcular_subsidio(numero_hijos, edad_escolar, madre_viuda):
    if numero_hijos == 0 or (numero_hijos == 0 and edad_escolar == 0 and not madre_viuda):
        print("No cumple con los requisitos para recibir subsidio. Monto: 0 quetzales.")
        return 0

    monto_base = 0

    # Determinar el monto base según la cantidad de hijos
    if numero_hijos <= 2:
        monto_base = 70
        print(f"Monto base por hasta 2 hijos: {monto_base} quetzales.")
    elif 3 <= numero_hijos <= 5:
        monto_base = 90
        print(f"Monto base por 3 a 5 hijos: {monto_base} quetzales.")
    else:
        monto_base = 120
        print(f"Monto base por 6 o más hijos: {monto_base} quetzales.")

    # Agregar monto adicional por hijos en edad escolar (si están en el rango de edad)
    monto_por_edad_escolar = (edad_escolar >= 6 and edad_escolar <= 18) * numero_hijos * 10
    if monto_por_edad_escolar > 0:
        print(f"Monto adicional por hijos en edad escolar: {monto_por_edad_escolar} quetzales.")

    # Agregar monto adicional por madre viuda
    monto_por_madre_viuda = 20 if madre_viuda else 0
    if madre_viuda:
        print("Monto adicional por madre viuda: 20 quetzales.")

    # Calcular el monto total
    monto_total = monto_base + monto_por_edad_escolar + monto_por_madre_viuda

    return monto_total

# Programa principal
numero_hijos = int(input("Ingrese el número de hijos: "))
edad_escolar = int(input("Ingrese la edad escolar de los hijos: "))
madre_viuda = bool(int(input("¿La madre es viuda? (1 para sí, 0 para no): ")))

# Calcular el monto mensual de subsidio familiar
monto_subsidio = calcular_subsidio(numero_hijos, edad_escolar, madre_viuda)

# Mostrar el monto mensual de subsidio familiar
print(f"El monto mensual de subsidio familiar es: {monto_subsidio} quetzales.")
```
*Ejemplos de captura de pantalla en Python:*

El usurio ingreso 0 hijos, por lo tanto el subsidio es de 0 quetzales.

<a href="https://imgbb.com/"><img src="https://i.ibb.co/qjbTzJK/image.png" alt="image" border="0" /></a>

El usuario ingreso 2 hijos fuera del rango de la edad escolar establecida no siendo la madre viuda. 

<a href="https://imgbb.com/"><img src="https://i.ibb.co/G96RrZX/image.png" alt="image" border="0" /></a>

El usuario ingreso la cantidad de 5 hijos fuera del rango de la edad escolar establecida siendo la madre viuda. 

<a href="https://imgbb.com/"><img src="https://i.ibb.co/rsgB0fk/image.png" alt="image" border="0" /></a>

El usuario ingreso la cantidad de 6 o + hijos dentro del rango de la edad escolar siendo la madre viuda. 

<a href="https://imgbb.com/"><img src="https://i.ibb.co/D1zSK0M/image.png" alt="image" border="0" /></a>

# Ejercicio #2

## Suma de Vectores en C++ y Python

Escribir una aplicación que solicite al usuario un número que será la longitud de dos 
vectores que se deben llenar aleatoriamente, sume los valores e indique si ocurre cualquiera de los 
siguientes escenarios. a) Son iguales, b) vector A es menor a B, c) vector B es menor a A.
##
En el siguiente algoritmo se le pedira al usario ingresar un numero para la longitud de los vectores, el algoritmo mostrar los numeros aleatorios dependiendo del numero de la longitud ingresada. El numero de la longitud ira para ambos vectores. Y el sistema automaticamente hara una suma de los valores de ambos vectores para finalizar comparando los resultados de ambos vectores, si el vector A es menor que B, o viceversa o si estos son iguales. 

*Ejemplos con capturas:*

Se le pide al usuario que ingrese un numero que sera la longitud de los vectores:

[![Whats-App-Image-2023-10-05-at-23-19-14-f2b639cf.jpg](https://i.postimg.cc/hP92mQrB/Whats-App-Image-2023-10-05-at-23-19-14-f2b639cf.jpg)](https://postimg.cc/PP5bsx93)

En este ejemplo se puede observar que el usuario ingreso el numero 5, mostrando 5 valores aleatorios en el vector A y 5 en el vector B, mostrando los resultados: 

[![Whats-App-Image-2023-10-05-at-23-19-43-b89d5512.jpg](https://i.postimg.cc/cLLfJvkT/Whats-App-Image-2023-10-05-at-23-19-43-b89d5512.jpg)](https://postimg.cc/xcBXx12b)

En este ejemplo se puede observar que el usuario ingreso el numero 9, mostrando 9 valores aleatorios en el vector A y 9 en el vector B, mostrando los siguientes resultados: 

[![Whats-App-Image-2023-10-05-at-23-20-54-0bf02c2b.jpg](https://i.postimg.cc/DyH7SDBD/Whats-App-Image-2023-10-05-at-23-20-54-0bf02c2b.jpg)](https://postimg.cc/ykmM5fqX)

En este ejemplo el usuario ingreso solo 1 longitud de los vectores mostrando los siguientes resultados:

[![Whats-App-Image-2023-10-05-at-23-22-45-d110210d.jpg](https://i.postimg.cc/52sTHF4t/Whats-App-Image-2023-10-05-at-23-22-45-d110210d.jpg)](https://postimg.cc/ZWyV2nyk)

##
# Codigo Fuente C++

```
#include <iostream>
#include <vector>
#include <cstdlib> // Para rand() y srand()
#include <ctime>   // Para time()

using namespace std;

// Función para generar un vector de tamaño 'length' con valores aleatorios entre 0 y 100
vector<int> generateRandomVector(int length) {
    vector<int> vec(length);
    for (int i = 0; i < length; i++) {
        vec[i] = rand() % 101; // Genera un número aleatorio entre 0 y 100
    }
    return vec;
}

int main() {
    srand(time(0)); // Inicializa números aleatorios

    int length;
    cout << "Introduce la longitud de los vectores: ";
    cin >> length;

    vector<int> vectorA = generateRandomVector(length);
    vector<int> vectorB = generateRandomVector(length);

    int sumA = 0, sumB = 0;
    for (int i = 0; i < length; i++) {
        sumA += vectorA[i];
        sumB += vectorB[i];
    }

    cout << "Vector A: ";
    for (int i = 0; i < vectorA.size(); i++) cout << vectorA[i] << " ";
    cout << "\nSuma de Vector A: " << sumA << endl;

    cout << "Vector B: ";
    for (int i = 0; i < vectorB.size(); i++) cout << vectorB[i] << " ";
    cout << "\nSuma de Vector B: " << sumB << endl;

    if (sumA == sumB) {
        cout << "Son iguales." << endl;
    } else if (sumA < sumB) {
        cout << "Vector A es menor a Vector B." << endl;
    } else {
        cout << "Vector B es menor a Vector A." << endl;
    }

    return 0;
}
```
##
# Codigo Fuente Python

```
import random

def generate_random_vector(length):
    """Genera una lista de números aleatorios entre 0 y 100."""
    return [random.randint(0, 100) for _ in range(length)]

def main():
    length = int(input("Introduce la longitud de los vectores: "))

    vectorA = generate_random_vector(length)
    vectorB = generate_random_vector(length)

    sumA = sum(vectorA)
    sumB = sum(vectorB)

    print(f"Vector A: {' '.join(map(str, vectorA))}")
    print(f"Suma de Vector A: {sumA}")

    print(f"Vector B: {' '.join(map(str, vectorB))}")
    print(f"Suma de Vector B: {sumB}")

    if sumA == sumB:
        print("Son iguales.")
    elif sumA < sumB:
        print("Vector A es menor a Vector B.")
    else:
        print("Vector B es menor a Vector A.")

if __name__ == '__main__':
    main()
```
*Ejemplos con capturas de pantallas:*

[![image.png](https://i.postimg.cc/nzbyZfVK/image.png)](https://postimg.cc/t1kStfx7)

[![image.png](https://i.postimg.cc/rw7bC246/image.png)](https://postimg.cc/TKqCfSQQ)

# Ejercicio #3

## Estadistica descriptiva en C++ y Python

En estadística descriptiva, se define el rango de un conjunto de datos reales como la 
diferencia entre el mayor y el menor de los datos.

Por ejemplo, si los datos son: [5.96, 6.74, 7.43, 4.99, 7.20, 0.56, 2.80], entonces el rango es 7.43 − 0.56 
= 6.87.

Escriba un programa que:
* a) Pregunte al usuario cuántos datos serán ingresados,
* b) Pida al usuario ingresar los datos uno por uno, y
Entregue como resultado el rango de los datos.

*Se mostraran capturas de pantalla de C++*

[![Whats-App-Image-2023-10-05-at-23-56-55-4ce2a823.jpg](https://i.postimg.cc/vB63Y0HW/Whats-App-Image-2023-10-05-at-23-56-55-4ce2a823.jpg)](https://postimg.cc/wyghFcNv)

[![Whats-App-Image-2023-10-05-at-23-58-40-33b9810d.jpg](https://i.postimg.cc/s2b4N591/Whats-App-Image-2023-10-05-at-23-58-40-33b9810d.jpg)](https://postimg.cc/PLzDLp7k)

En la parte de abajo encontrara el codigo de C++ y Python
##
# Codigo Fuente C++

```
#include <iostream>
#include <vector>

int main() {
    int n;
    std::cout << "Ingrese la cantidad de datos: ";
    std::cin >> n;

    // Verificar si n es válido (debe ser al menos 2 para calcular el rango)
    if (n < 2) {
        std::cerr << "Debe ingresar al menos 2 datos para calcular el rango." << std::endl;
        return 1;  // Salir con un código de error
    }

    std::vector<double> datos;
    double dato;

    // Pedir al usuario ingresar los datos uno por uno
    for (int i = 0; i < n; ++i) {
        std::cout << "Ingrese el dato " << i + 1 << ": ";
        std::cin >> dato;
        datos.push_back(dato);
    }

    // Encontrar el valor máximo y mínimo en el conjunto de datos
    double maximo = datos[0];
    double minimo = datos[0];
    for (int i = 1; i < n; ++i) {
        if (datos[i] > maximo) {
            maximo = datos[i];
        }
        if (datos[i] < minimo) {
            minimo = datos[i];
        }
    }

    // Calcular el rango
    double rango = maximo - minimo;

    // Mostrar el resultado como "Rango Menor - Rango Mayor = Resultado"
    std::cout << "Rango Menor (" << minimo << ") - Rango Mayor (" << maximo << ") = " << rango << std::endl;

    return 0;  // Salir con éxito
}

```
##
# Codigo Fuente Python

```
# Preguntar al usuario cuántos datos serán ingresados
n = int(input("Ingrese la cantidad de datos: "))

# Verificar si n es válido (debe ser al menos 2 para calcular el rango)
if n < 2:
    print("Debe ingresar al menos 2 datos para calcular el rango.")
else:
    # Inicializar una lista para almacenar los datos
    datos = []

    # Pedir al usuario ingresar los datos uno por uno
    for i in range(n):
        dato = float(input(f"Ingrese el dato {i + 1}: "))
        datos.append(dato)

    # Encontrar el valor máximo y mínimo en el conjunto de datos
    maximo = max(datos)
    minimo = min(datos)

    # Calcular el rango
    rango = maximo - minimo

    # Mostrar el resultado como "Rango Menor - Rango Mayor = Resultado"
    print(f"Rango Menor ({minimo}) - Rango Mayor ({maximo}) = {rango}")
```
*Capturas de pantalla Python:*

[![image.png](https://i.postimg.cc/XvttkGrk/image.png)](https://postimg.cc/v1LPQmL4)

[![image.png](https://i.postimg.cc/CM2nHw7L/image.png)](https://postimg.cc/bdQvqc4K)


# Ejercicio #4

## Cuadrado de asteriscos C++ y Python

Solicite al usuario ingresar un número que será el lado de un cuadrado y escriba un 
programa que dibuje dicho cuadrado.

El siguiente programa mostrara un cuadrado hecho de triangulos dependiendo del numero que el usuario ingrese. 

*Ejemplos de captura de pantalla en C++*

[![Whats-App-Image-2023-10-06-at-00-50-59-9d7b6a93.jpg](https://i.postimg.cc/zGhhfvsR/Whats-App-Image-2023-10-06-at-00-50-59-9d7b6a93.jpg)](https://postimg.cc/0z8jWk28)

[![Whats-App-Image-2023-10-06-at-00-51-29-87cb7ef3.jpg](https://i.postimg.cc/y6wcC05z/Whats-App-Image-2023-10-06-at-00-51-29-87cb7ef3.jpg)](https://postimg.cc/237V4LrH)

[![Whats-App-Image-2023-10-06-at-00-51-58-9a197899.jpg](https://i.postimg.cc/SNfs18bd/Whats-App-Image-2023-10-06-at-00-51-58-9a197899.jpg)](https://postimg.cc/rKzMKDmR)

##
# Codigo Fuente C++

```
#include <iostream>

int main() {
    int lado;

    // Solicitar al usuario el tamaño del lado del cuadrado
    std::cout << "Ingrese el tamanio del lado del cuadrado: ";
    std::cin >> lado;

    // Verificar si el tamaño del lado es válido (debe ser mayor que 1)
    if (lado <= 1) {
        std::cerr << "El tamanio del lado debe ser mayor que 1." << std::endl;
        return 1;  // Salir con un código de error
    }

    // Dibujar el cuadrado vacío
    for (int i = 0; i < lado; ++i) {
        for (int j = 0; j < lado; ++j) {
            if (i == 0 || i == lado - 1 || j == 0 || j == lado - 1) {
                // Imprimir un asterisco en los bordes del cuadrado
                std::cout << "*";
            } else {
                // Imprimir un espacio en blanco en el interior del cuadrado
                std::cout << " ";
            }
        }
        // Cambiar de línea para la siguiente fila
        std::cout << std::endl;
    }

    return 0;  // Salir con éxito
}
```
##
# Codigo Fuente Python

```
# Solicitar al usuario el tamaño del lado del cuadrado
lado = int(input("Ingrese el tamaño del lado del cuadrado: "))

# Verificar si el tamaño del lado es válido (debe ser mayor que 1)
if lado <= 1:
    print("El tamaño del lado debe ser mayor que 1.")
else:
    # Dibujar el cuadrado vacío
    for i in range(lado):
        for j in range(lado):
            if i == 0 or i == lado - 1 or j == 0 or j == lado - 1:
                # Imprimir un asterisco en los bordes del cuadrado
                print("*", end="")
            else:
                # Imprimir un espacio en blanco en el interior del cuadrado
                print(" ", end="")
        # Cambiar de línea para la siguiente fila 
        print()
```
*Capturas de Pantalla en Python:*

[![image.png](https://i.postimg.cc/qqk8WrqZ/image.png)](https://postimg.cc/dkxkTz88)

[![image.png](https://i.postimg.cc/V6T8VfKz/image.png)](https://postimg.cc/ygFtJHqG)

[![image.png](https://i.postimg.cc/MGfNpCxG/image.png)](https://postimg.cc/XZ3Q2DrM)






