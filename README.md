# Ejercicio #1

## Subsidio Familiar en C++

Escriba una aplicación en c++ y Python para resolver el siguiente enunciado. El gobierno ha implementado como parte de su programa social, un subsidio familiar bajo la siguiente reglamentación: Las familias que tienen hasta 2 hijos, reciben Q. 70.00, las que tienen hasta 3 y 5 reciben Q. 90.00 y las que tienen 6 o más reciben Q. 120 mensual. Por cada hijo en edad escolar reciben Q. 10.00 adicionales.

Se considera la edad escolar entre 6 y 18 años. Si la madre de familia fuera viuda, la familia recibe Q.20.00 adicionales. Determinar el monto mensual que recibirá una familia de acuerdo a su realidad familiar a través de una función llamada calcularSubsidio.
##
En el siguiente algoritmo se le da la bienvenida al usuario y le va a pedir que ingrese los datos en base a las preguntas establecidas.

<a href="https://imgbb.com/"><img src="https://i.ibb.co/0ZBZpyc/zc.png" alt="zc"border="0" /></a>

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

<a href="https://imgbb.com/"><img src="https://i.ibb.co/G05L8Dd/0q.png" alt="0q" border="0" /></a>

Usuario ingresa 2 hijos con la edad entre 6 a 18 años siendo la madre viuda. 

<a href="https://imgbb.com/"><img src="https://i.ibb.co/kDXBwPg/image.png" alt="image" border="0" /></a>

Usuario ingresa el rango de 3 a 5 hijos con la edad escolar entre  6 a 18 años no siendo la madre viuda.

<a href="https://imgbb.com/"><img src="https://i.ibb.co/7Nqsv5g/image.png" alt="image" border="0" /></a>

Usuario ingresa mas de 6 hijos fuera de la edad escolar siendo la madre viuda:

<a href="https://imgbb.com/"><img src="https://i.ibb.co/PmynVjK/image.png" alt="image" border="0" /></a>

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
