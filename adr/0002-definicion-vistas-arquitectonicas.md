# ADR-02: Adopción de 4 Vistas Arquitectónicas con Mermaid JS

| Campo | Valor |
| :--- | :--- |
| **Autor** | Jorge Emilio Batun Alcocer |
| **Fecha** | 05/06/2026 |
| **Estado** | Aceptado |

**Contexto**
Estamos construyendo TaskQuest, un sistema web de gestión de tareas con una UI inspirada en videojuegos. El sistema utiliza C# y el patrón ASP.NET MVC. Actualmente, el almacenamiento es temporal en memoria RAM. Como parte del ciclo de desarrollo y los entregables académicos, necesitamos documentar formalmente la arquitectura para que cualquier integrante del equipo pueda comprender cómo se comunican las clases, cómo se procesan las peticiones del usuario y cómo se despliega el prototipo actual en el servidor. La restricción principal es que los diagramas deben estar en un formato compatible con el repositorio (Mermaid o draw.io).

**Decisión**
Decidimos documentar el sistema utilizando 4 de las vistas arquitectónicas (Lógica, de Procesos, Física y de Despliegue) e implementar los diagramas directamente utilizando **Mermaid JS** incrustado en los archivos Markdown de GitHub.

**¿Por qué?**
Mermaid interpreta texto plano para renderizar gráficos directamente en la interfaz de GitHub. Esta característica concreta resuelve el problema del versionado: al estar en texto, si agregamos una nueva clase al `TaskService` en el futuro, podemos modificar una sola línea de código en el diagrama y el cambio quedará registrado claramente en un *Pull Request*, a diferencia de un archivo binario de imagen donde es imposible ver qué cambió exactamente.

**Alternativas consideradas**

| Alternativa | Por qué ladescarté |
| :--- | :--- |
| **Modelado UML en StarUML** | Los archivos generados no son amigables con el control de versiones de Git, lo que dificulta revisar los cambios visuales durante las revisiones de código en equipo. |
| **Solo usar Diagramas C4** | Aunque el Nivel 1 y 2 del modelo C4 son excelentes para el contexto, no detallan el comportamiento en tiempo de ejecución (procesos) ni la topología de hardware (física) que exige el entregable actual. |
| **Draw.io exportado a PNG** | Requiere mantener archivos fuente (`.drawio`) separados de las imágenes renderizadas, y el texto dentro de los diagramas PNG no es indexable ni permite búsquedas rápidas en el repositorio. |

**Consecuencias**

**Lo que gano:**
* **Consecuencia técnica:** La documentación se vuelve más fácil de mantener; los diagramas evolucionan al mismo ritmo que el código utilizando las mismas herramientas (Git).
* **Consecuencia de proceso:** Obliga al equipo a tener claridad total sobre cómo interactúan el Modelo, la Vista y el Controlador antes de iniciar la programación de nuevos módulos.

**Lo que sacrifico o asumo:**
* **Limitación técnica:** La herramienta Mermaid diagrama automáticamente, por lo que perdemos el control preciso sobre la posición en píxeles de los elementos que sí tendríamos en draw.io.
* **Deuda o riesgo:** Existe una pequeña curva de aprendizaje inicial; los integrantes del equipo deberán familiarizarse con la sintaxis de Mermaid para leer y actualizar los diagramas de secuencia y clases.

**Declaración de uso de IA**
*(Nota: El formato y la generación de la sintaxis base de los diagramas de este ADR contaron con asistencia de Inteligencia Artificial como herramienta de apoyo a la redacción técnica, siendo el análisis arquitectónico, los componentes del patrón MVC y la revisión de exactitud de autoría propia).*