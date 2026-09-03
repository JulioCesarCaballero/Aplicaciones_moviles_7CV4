# Práctica 1: Configuración del Entorno Móvil y Comparativa de Enfoques de Interfaz

**Institución:** Instituto Politécnico Nacional (IPN)  
**Unidad Académica:** Escuela Superior de Cómputo (ESCOM)  
**Programa Académico:** Ingeniería en Sistemas Computacionales (Plan 2020)  
**Unidad de Aprendizaje:** Desarrollo de aplicaciones móviles nativas  
**Estudiante:** Julio César Caballero Pérez  
**Boleta:** 2023630158  
**Grupo:** 7CV4  

---

## 1. Descripción del Entorno y Herramientas Instaladas

A continuación se detallan las herramientas configuradas en el sistema operativo Windows 11 para dar soporte a los tres entornos de desarrollo solicitados:

| Herramienta | Versión Instalada | Propósito en el Entorno de Desarrollo |
| :--- | :--- | :--- |
| **Java Development Kit (JDK)** | OpenJDK 21 | Compilación de código Kotlin/Java y ejecución del motor de compilación Gradle. |
| **Android Studio** | Ladybug 1.1306 | Entorno de desarrollo integrado (IDE), administración de SDKs y emulación. |
| **Android SDK Command-line Tools** | v17.0 (SDK Platforms 35) | Empaquetado de aplicaciones (`aapt2`), firma de binarios y aceptación de licencias. |
| **Git** | 2.x | Sistema de control de versiones distribuido para el seguimiento de la práctica. |
| **Flutter SDK** | 3.47.2  | Framework multiplataforma de UI reactiva impulsado por el lenguaje Dart. |
| **Node.js & npm** | Node v24.20.0  | Entorno de ejecución JavaScript y gestor de dependencias para tooling auxiliar. |
| **Docker** | 27.x *(si aplica)* | Contenedores para aislamiento de servicios o entornos de prueba. |

---

## 2. Descripción de los Proyectos Desarrollados

Se implementaron tres versiones de la aplicación "Hola Mundo" mostrando los datos del estudiante:

1. **`hola_mundo_xml` (Android Nativo con Views):**
   - **Enfoque:** Imperativo clásico.
   - **Estructura de UI:** Definida en formato XML mediante un contenedor raíz `ConstraintLayout` que aloja un `LinearLayout` vertical con múltiples componentes `TextView`.
   - **Lógica:** Separada en `MainActivity.kt` inflando la vista a través de `setContentView(R.layout.activity_main)`.

2. **`hola_mundo_compose` (Android Nativo con Jetpack Compose):**
   - **Enfoque:** Declarativo y reactivo nativo en Kotlin.
   - **Estructura de UI:** Implementada mediante una función composable modular (`DatosEstudiante()`) utilizando `Surface`, `Column` con alineación centrada y componentes `Text`.
   - **Estilos:** Se aplicaron modificadores (`Modifier.padding()`, `Modifier.fillMaxSize()`) y tipografías/colores directos sin requerir archivos XML adicionales. Permite previsualización en el IDE mediante la anotación `@Preview`.

3. **`hola_mundo_flutter` (Multiplataforma con Flutter):**
   - **Enfoque:** Declarativo multiplataforma basado en widgets inmutables.
   - **Estructura de UI:** Diseñada en `lib/main.dart` utilizando el árbol estándar `MaterialApp` > `Scaffold` > `Center` > `Column` > `Text`.
   - **Renderizado:** Dibuja la interfaz de forma nativa e independiente del sistema a través de su propio motor gráfico (Skia/Impeller).

