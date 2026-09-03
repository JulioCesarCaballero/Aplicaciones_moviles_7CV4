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

### Hallazgos del Proceso de Instalación y Configuración
* **Gestión de licencias del SDK:** La instalación automática de herramientas de línea de comandos en versiones recientes puede generar advertencias en la verificación de licencias. La solución óptima requiere la instalación manual de `Android SDK Command-line Tools` estable desde el SDK Manager para asegurar la compatibilidad total con herramientas multiplataforma como Flutter.
* **Políticas de ejecución del sistema:** Windows restringe por defecto la ejecución de scripts en PowerShell (`RemoteSigned`), lo que interfiere con herramientas basadas en Node/npm. Ajustar la directiva a nivel de usuario (`CurrentUser`) resuelve este conflicto sin comprometer la seguridad global del equipo.
* **Integración del entorno móvil:** La configuración de un entorno nativo demanda una sincronización estricta entre versiones de JDK, Gradle, extensiones del IDE y variables de entorno del sistema (`ANDROID_HOME`, `PATH`), siendo fundamental validar la infraestructura antes de compilar código.

---

### Comparativa Técnica entre los Tres Enfoques

| Criterio | Android Views (XML) | Jetpack Compose | Flutter |
| :--- | :--- | :--- | :--- |
| **Paradigma** | Imperativo tradicional | Declarativo nativo | Declarativo multiplataforma |
| **Lenguaje de desarrollo** | XML (diseño) + Kotlin (lógica) | Kotlin al 100% | Dart al 100% |
| **Curva de aprendizaje** | Media: requiere mapeo de vistas (`findViewById` / ViewBinding) | Media-baja para desarrolladores Kotlin modernos | Media: exige comprender la jerarquía de widgets y estados |
| **Velocidad de iteración** | Lenta (reconstrucción y recarga de Activity) | Rápida con Live Edit y `@Preview` | Muy alta gracias a *Stateful Hot Reload* |
| **Rendimiento e integración** | Nativo directo del framework de Android | Nativo optimizado con menos sobrecarga | Alto rendimiento vía motor gráfico propio (Skia/Impeller) |
| **Portabilidad** | Exclusivo de Android | Multiplataforma incipiente (Compose Multiplatform) | Totalmente multiplataforma (Android, iOS, Web, Desktop) |

---

### Conclusiones
* **Android Views (XML):** Sigue siendo el estándar histórico con amplia base de código y soporte maduro. No obstante, mantener archivos de vista desacoplados de la lógica de negocio añade complejidad, duplicidad de referencias y mayor mantenimiento en aplicaciones con interfaces dinámicas.
* **Jetpack Compose:** Representa el estándar moderno y la dirección prioritaria de Android. Al eliminar completamente los layouts en XML y unificar el desarrollo en Kotlin, reduce drásticamente las líneas de código, previene errores de ciclo de vida y optimiza el manejo reactivo del estado de la interfaz.
* **Flutter:** Es la opción más eficiente cuando se requiere desplegar en múltiples plataformas desde un único código base. Aunque el empaquetado inicial del binario APK es de mayor tamaño debido a su motor gráfico integrado, el dinamismo en tiempo de desarrollo y la consistencia visual entre dispositivos lo convierten en una alternativa altamente competitiva para el desarrollo móvil contemporáneo.