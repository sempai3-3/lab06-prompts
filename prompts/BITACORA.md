# Bitacora de prompts

Laboratorio 06: Fundamentos de Ingenieria de Prompts.

Herramienta de IA usada: ChatGPT

## Ejercicio 2: Tokens y ventana de contexto

### Conteo de tokens

| Texto                              | Caracteres | Tokens |
| ---------------------------------- | ---------: | -----: |
| Los estudiantes programan en Java. |         34 |      7 |
| The students program in Java.      |         29 |      6 |
| desafortunadamente                 |         18 |      4 |

### Observación

La frase en español utilizó más tokens que la frase en inglés. También se puede observar que la palabra "desafortunadamente", aunque tiene una sola palabra, fue dividida en varios tokens. Esto demuestra que los tokens no necesariamente corresponden a palabras completas.


## Ejercicio 3: Temperatura

## Pruebas del simulador de temperatura

Se realizaron pruebas con diferentes valores de temperatura para observar cómo cambia la probabilidad de selección de las opciones.

### Temperatura 0.2

- BiblioTec: 91.8%
- LibroYa: 7.5%
- PrestaLibro: 0.6%
- Las demás opciones tuvieron una probabilidad cercana a 0%.

Resultado: el simulador se concentra principalmente en la opción con mayor puntaje.

### Temperatura 1.0

- BiblioTec: 44.5%
- LibroYa: 27.0%
- PrestaLibro: 16.4%
- LectoGo: 6.0%
- PaginaLibre: 3.7%
- NubeDeTinta: 2.4%

Resultado: existe una mayor variedad de opciones.

### Temperatura 2.0

- BiblioTec: 30.5%
- LibroYa: 23.8%
- PrestaLibro: 18.5%
- LectoGo: 11.2%
- PaginaLibre: 8.8%
- NubeDeTinta: 7.2%

Resultado: las probabilidades se encuentran más distribuidas.

### Temperatura 5.0

- BiblioTec: 21.9%
- LibroYa: 19.8%
- PrestaLibro: 18.0%
- LectoGo: 14.7%
- PaginaLibre: 13.3%
- NubeDeTinta: 12.3%

Resultado: las probabilidades son bastante similares entre las opciones.

### Temperatura 10.0

- BiblioTec: 19.2%
- LibroYa: 18.3%
- PrestaLibro: 17.4%
- LectoGo: 15.7%
- PaginaLibre: 15.0%
- NubeDeTinta: 14.4%

Resultado: las probabilidades se acercan mucho entre sí.

### Temperatura 0

BiblioTec obtuvo 100% de probabilidad y fue seleccionada en los cinco intentos.

### Temperatura -1

BiblioTec obtuvo 100% de probabilidad y fue seleccionada en los cinco intentos.

## Observación

Al aumentar la temperatura, las probabilidades de las opciones se vuelven más similares y se obtiene mayor variedad. Con temperaturas bajas, el simulador favorece principalmente las opciones con mayor puntaje.

## Conclusión

La temperatura permite controlar el nivel de variedad de las respuestas del simulador. Una temperatura baja produce resultados más predecibles, mientras que una temperatura alta distribuye las probabilidades entre más opciones.
## Ejercicio 4: Prompt vago vs estructurado
| Criterio | Prompt vago | Prompt estructurado |
|----------|-------------|---------------------|
| Menciona el objetivo del sistema | No | Si |
| Menciona a los usuarios principales | No | Si |
| Tiene exactamente 3 funcionalidades | No | Si |
| Esta en 3 parrafos | No | Si |
| Lo usaria en un informe real | No | Si |


## Ejercicio 5: Anatomia de un prompt

### Componentes del prompt final

| Componente | Texto de mi prompt |
|------------|--------------------|
| Rol | Actua como desarrollador Java. |
| Instruccion | Crea un programa en Java. |
| Contexto | para gestionar los productos de una tienda usando una clase Producto con los atributos codigo, nombre, precio y stock. |
| Ejemplo | Usa este estilo para los metodos: getPrecio(), setPrecio(double precio). |
| Formato | Explica primero la estructura de la clase y luego presenta el codigo Java. |

### Cambios por nivel

- **Nivel 1:** La IA crea un programa en Java sin tener especificaciones concretas.
- **Nivel 2:** Al agregar el rol, la respuesta se orienta al trabajo de un desarrollador Java.
- **Nivel 3:** Al agregar el contexto, el programa se enfoca en gestionar productos de una tienda.
- **Nivel 4:** Al agregar la instrucción específica, se indica que debe usar la clase Producto con codigo, nombre, precio y stock.
- **Nivel 5:** Al agregar el formato, la IA explica primero la estructura de la clase y después muestra el código Java.
- **Ejemplo:** Al agregar el ejemplo, se indica el estilo que deben tener los métodos getter y setter.


## Ejercicio 6: Del prompt basico al profesional

### Evaluación del prompt profesional

| Qué revisar | Cumple (Sí / No) |
|-------------|------------------|
| ¿Está escrito en Java y usa Swing? | Sí |
| ¿Pide correo y contraseña? | Sí |
| ¿Explica el funcionamiento antes o después del código? | Sí |
| ¿El código está organizado en clases? | Sí |
| ¿Valida los datos que ingresa el usuario? | No |

### Observación

El prompt profesional produce una respuesta más específica que el prompt básico porque indica que se debe utilizar Java Swing, solicitar correo y contraseña, explicar el funcionamiento y organizar el código en clases.

### Prompt final

```text
Actua como desarrollador Java. Crea un ejemplo de login para una aplicacion de escritorio utilizando Swing. El usuario debe ingresar correo y contrasena. Explica brevemente el funcionamiento y presenta el codigo organizado por clases.

Mejora el codigo anterior con estas restricciones: no uses librerias externas, valida que el correo contenga @ y que la contrasena tenga al menos 8 caracteres, y muestra los mensajes con JOptionPane.