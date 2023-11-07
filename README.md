# APICLIENT_JAVA_DAD_DAM
Interfaz gráfica de usuario que consulta una api y obtiene información, es un ejemplo practico para la obtención de información a través de una api


# Proyecto de Ejemplo MVC con Principios SOLID

Este proyecto es un ejemplo práctico de una aplicación de escritorio para la gestión de empleados que consulta una API para obtener datos y los presenta en una interfaz de usuario. Se ha diseñado siguiendo el patrón Modelo-Vista-Controlador (MVC) y los principios SOLID para garantizar que el código sea mantenible, escalable y fácil de entender.

Este proyecto básico se podría ampliar para obtener un CRUD completo hacía una API, este repositorio parte del modulo de la asignatura DAD (Desarrollo de Interfaces) del Ciclo Superior DAM (Desarrollo de Aplicaciones Multiplataformas), donde el profesor "JJ" nos ha reiterado la importancia de crear codigo, siguiente siempre buenas practicas, siguendo patrones con los principios de SOLID y CLEAN CODE.

Les hablaré por encima del proyecto y algunos conceptos y dejare un repositorios sin las clases comentadas y otras con las clases comentadas para fines de entenidmiento y educativos.

## Inyección de Dependencias (DI)

### ¿Qué es la Inyección de Dependencias?
La Inyección de Dependencias es un patrón de diseño que permite a un objeto recibir sus dependencias desde fuera en lugar de crearlas por sí mismo. Esto se puede lograr mediante la construcción de objetos, métodos setter, o directamente en los campos.

### Beneficios de la DI
- **Desacoplamiento**: Los objetos no están fuertemente vinculados a las implementaciones de sus dependencias.
- **Facilidad de prueba**: Facilita la sustitución de las dependencias reales por mocks o stubs en las pruebas unitarias.
- **Flexibilidad y mantenibilidad**: Facilita el cambio y la evolución de la aplicación al permitir que los detalles de las implementaciones de dependencias puedan cambiar sin afectar a los consumidores de esas dependencias.

### Ejemplo de código:
```java
public class MainController {
    private final MainView view;
    private final IAPIClient apiClient;

    public MainController(MainView view, IAPIClient apiClient) {
        this.view = view;
        this.apiClient = apiClient;
        // Lógica de inicialización aquí...
    }
}
```

## Inversión de Dependencias (Principio 'D' de SOLID)

### ¿Qué es la Inversión de Dependencias?
La Inversión de Dependencias es un principio que establece que las clases de alto nivel no deben depender de clases de bajo nivel, sino de abstracciones. Además, estas abstracciones no deben depender de detalles, sino que los detalles deben depender de las abstracciones.

### Beneficios de la Inversión de Dependencias
- **Fomenta el diseño modular**: Al depender de abstracciones, el diseño de la aplicación es más modular.
- **Mejora la escalabilidad**: El sistema se vuelve más escalable al no estar limitado por implementaciones concretas.
- **Promueve la reutilización del código**: Las abstracciones pueden ser reutilizadas en diferentes partes del sistema sin depender de implementaciones específicas.

### Ejemplo de código:
```java
public interface IAPIClient {
    // Métodos que se deben implementar por cualquier cliente de API.
}

public class APIClient implements IAPIClient {
    // Implementación concreta de la interfaz IAPIClient.
}
```

En este proyecto, hemos aplicado tanto la Inyección de Dependencias como la Inversión de Dependencias para asegurar que nuestro código sigue las mejores prácticas y se adhiere a los principios SOLID.

---

## Estructura del Proyecto

El proyecto se estructura en varios paquetes y clases que separan las responsabilidades de la aplicación:

- `app`: Contiene la clase `MainApp` que sirve como punto de entrada a la aplicación.
- `controller`: Incluye `MainController` y `EventController` para manejar la lógica de negocio y los eventos de la interfaz.
- `view`: Contiene `MainView`, la clase que define la interfaz gráfica de usuario.
- `model`: Compuesto por las clases `Employee` y `EmployeeDataWrapper` que representan la información de los empleados y su envoltura.
- `API`: Incluye la interfaz `IAPIClient` y su implementación `APIClient`, que manejan las llamadas a la API de empleados.
- `exceptions`: Define `APIClientException`, una excepción personalizada para errores relacionados con la API.

## Principios y Patrones

### MVC
El patrón Modelo-Vista-Controlador se implementa de la siguiente manera:
- **Modelo (`model`)**: `Employee` y `EmployeeDataWrapper`.
- **Vista (`view`)**: `MainView`.
- **Controlador (`controller`)**: `MainController` y `EventController`.

### SOLID
- **S**: Cada clase tiene una única responsabilidad.
- **O**: El sistema está abierto a la extensión pero cerrado a la modificación, facilitado por el uso de interfaces como `IAPIClient`.
- **L**: Las clases derivadas pueden ser sustituidas por sus clases base (uso de `APIClientException`).
- **I**: Se separan las interfaces (`IAPIClient`) para que las implementaciones no dependan de métodos que no utilizan.
- **D**: Las dependencias de alto nivel no dependen de las de bajo nivel, sino de abstracciones.

### Clean Code
Se ha puesto un énfasis especial en la claridad y la simplicidad del código, siguiendo prácticas como nombres de variables descriptivos, métodos pequeños y específicos, y el manejo adecuado de excepciones.

## Comentarios en el Código

Cada clase e interfaz del proyecto tiene comentarios detallados que explican su propósito y funcionamiento para facilitar la comprensión a desarrolladores de todos los niveles.

## Cómo Contribuir

Si deseas contribuir a este proyecto, por favor considera los siguientes pasos:

1. Fork el repositorio.
2. Crea una nueva rama para tus cambios.
3. Haz tus cambios y escribe pruebas cuando sea posible.
4. Asegúrate de que tu código sigue los principios y prácticas mencionados.
5. Envía un pull request con una descripción detallada de tus cambios.

En principo es un proyecto a modo de ejemplo, quizas se desarrolle más adelante el CRUD completo, pero ahora solo es consulta a la api a
