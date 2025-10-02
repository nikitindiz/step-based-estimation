# Metodología Step-Based Estimation (SBE)

## Descripción de la metodología

**Step-Based Estimation** es un enfoque de planificación de desarrollo donde cada tarea se descompone en pasos de ejecución detallados y concretos, seguido de un análisis de dependencias y una comparación retrospectiva opcional del plan versus la realidad.

Además de los Criterios de Aceptación, que típicamente representan una vista declarativa de la tarea, los Pasos de Implementación proporcionan una descripción imperativa de cómo exactamente se implementará la tarea.

### Proceso SBE:

**Organización del trabajo:**

- **Sesión de Refinement**: Estimación estándar de tareas a través de agile poker
- **Sesión de Step Estimation**: Reunión separada para descomposición detallada

**Selección de tareas para detallar**: Las tareas se llevan a Step Estimation basándose en los resultados de votación del equipo

**Etapas de trabajo de la tarea:**

1. **Descomposición**: Dividir la tarea en pasos concretos ("Agregar campo X al formulario Y", "Actualizar función Z en módulo W", "Crear repositorio para fuente de datos Y").
2. **Descubrimiento de subtareas ocultas**: Identificar pasos que pueden extraerse en tareas separadas.
3. **Estimación**: Evaluar la tarea por el número total de pasos (usando Fibonacci).
4. **Retrospectiva** _(opcional)_: Comparar los pasos planificados con los realmente completados, identificar patrones de divergencia, tener en cuenta para futuras estimaciones.

---

## Comparación de enfoques de estimación

| Aspecto               | Refinement (optimista)                                                                                                      | Step Estimation (pesimista)                                                                                                                                                                                                                                                                                                                                                  |
| --------------------- | --------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Carácter**          | Alto nivel, rápido, basado en comprensión general                                                                           | Detallado, basado en pasos concretos de implementación                                                                                                                                                                                                                                                                                                                       |
| **Cuándo ocurre**     | • En la etapa de planificación inicial<br>• Durante el primer encuentro con la tarea<br>• Basado en Criterios de Aceptación | • Después del Refinement, antes del inicio del sprint<br>• Para tareas complejas/riesgosas<br>• Basado en Pasos de Implementación                                                                                                                                                                                                                                            |
| **Ventajas**          | ✓ Rápido                                                                                                                    | ✓ Considera detalles<br>✓ Revela pasos ocultos<br>✓ Más realista                                                                                                                                                                                                                                                                                                             |
| **Desventajas**       | ⚠ Propenso a subestimar la complejidad<br>⚠ No tiene en cuenta detalles de implementación<br>⚠ Pierde pasos "ocultos"       | ⚠ Requiere más tiempo<br>⚠ Requiere experiencia técnica                                                                                                                                                                                                                                                                                                                      |
| **Preguntas típicas** | • "¿Es esto más o menos como esa tarea?"<br>• "Suena como 5 puntos"<br>• "Los Criterios de Aceptación parecen simples"      | • "¿Qué clases, módulos y funciones necesitan cambiarse?"<br>• "¿Qué repositorios y fuentes de datos se ven afectados?"<br>• "¿Qué estados deben considerarse?"<br>• "Si tratamos la entidad de software como una caja negra, ¿qué interfaz describe los argumentos y el valor de retorno?"<br>• "Si hay tareas dependientes, ¿cómo se integran después de la finalización?" |

---

## Sinergia de dos enfoques

### Problema clásico (solo Refinement)

```
Equipo en Refinement: "¡Agregar filtros de tabla — 3 puntos!"

Realidad durante el sprint:
- Día 1: "Oh, necesitamos rediseñar la estructura de la base de datos"
- Día 2: "Oh, necesitamos agregar índices para rendimiento"
- Día 3: "Oh, necesitamos manejar casos extremos con datos vacíos"
- Día 4: "Oh, necesitamos adaptar la UI para dispositivos móviles"
- Día 5: "Oh, necesitamos escribir 15 pruebas en lugar de 5"

Resultado: 3 SP se convirtieron en 8 SP, la tarea no cupo en el sprint
```

### Con aplicación de SBE (Refinement + Step Estimation)

```
Refinement (optimista): 3 SP
↓
Votación del equipo: llevar a Step Estimation
↓
Step Estimation (pesimista): el detalle revela:
- 12 pasos en lugar de los 5 asumidos
- Se necesita migración de base de datos
- Requerirá 15 pruebas
- 6 clases afectadas
↓
Corrección: 3 SP → 5 SP
↓
Resultado: estimación más realista, la tarea cabe en el sprint
```

### Psicología de la estimación

**Refinement (optimismo):**

- El equipo se enfoca en el "camino feliz"
- "Hemos hecho algo similar antes, será rápido"
- La subestimación de la complejidad es un error cognitivo natural

**Step Estimation (realismo):**

- El detalle obliga a pensar en problemas
- "¿Qué pasa si...?", "Necesitamos considerar..."
- Descubrimiento de complejidades ocultas

**Balance:**
Estimación optimista en Refinement → planificación rápida del backlog
Estimación pesimista en Step Estimation → planificación realista del sprint

---

## Beneficios del enfoque

### 1. **Mejora de la precisión de estimaciones**

- El detalle revela subtareas ocultas en la etapa de planificación
- Acumula base de conocimiento sobre el esfuerzo real de pasos típicos
- Reduce el impacto del optimismo y sesgos cognitivos

### 2. **Mejor planificación del sprint**

- Capacidad de paralelizar pasos independientes
- Identificación de ruta crítica del proyecto
- Carga más uniforme del equipo

### 3. **Retrospectiva estructurada** _(opcional)_

- Datos concretos en lugar de sentimientos subjetivos
- Identificación de problemas sistémicos del proceso
- Material para mejorar futuras estimaciones

### 4. **Reducción de riesgos**

- Identificación temprana de dependencias de tareas
- Prevención de pasos "olvidados"
- Capacidad de replanificación temprana cuando ocurren desviaciones

### 5. **Transparencia del progreso**

- Seguimiento más detallado de la preparación de tareas
- Identificación temprana de bloqueadores y problemas

### 6. **Evaluación preliminar de cobertura de pruebas**

- Estimación superficial del volumen de pruebas unitarias requeridas
- Planificación del esfuerzo de pruebas en la etapa de estimación

---

## Organización del proceso

### Sesión de Refinement (principal)

**Objetivo:** Estimación inicial de tareas del backlog

**Participantes:** Todo el equipo de desarrollo

**Proceso:**

1. Product Owner presenta la tarea
2. Discusión de Criterios de Aceptación
3. Preguntas aclaratorias
4. Estimación a través de agile poker (Planning Poker)
5. Registro de estimación en story points

**Duración:** 1-2 horas

**Carácter de estimación:** Optimista, rápido, de alto nivel

### Sesión de Step Estimation (adicional)

**Objetivo:** Descomposición detallada de tareas complejas

**Participantes:**

- Requerido: desarrolladores que trabajarán en la tarea
- Deseable: Tech Lead, QA Engineer
- Opcional: Product Owner (para aclaración de requisitos)

**Selección de tareas para detallar:**
El equipo vota por las tareas que necesitan detalle:

- Tareas con incertidumbre intuitiva
- Tareas de 5+ story points
- Tareas que afectan componentes críticos
- Tareas con riesgos técnicos (breaking changes, integraciones externas)
- Tareas donde la estimación en Refinement causó disputas

**Proceso:**

1. Selección de tarea para detallar (basada en resultados de votación)
2. Descomposición en Pasos de Implementación
3. Estimación de cantidad de pruebas requeridas
4. Identificación de dependencias entre pasos
5. Opción de ajustar la estimación inicial
6. Pasar a la siguiente tarea

**Duración:** 1-1.5 horas (3-5 tareas detalladas)

**Frecuencia:** Una vez por sprint o según sea necesario

**Carácter de estimación:** Pesimista, detallado, realista

---

## Ejemplos prácticos

### Ejemplo 1: Efecto de optimismo vs realismo

**Tarea:** "Agregar autenticación de dos factores"

**Refinement (estimación optimista):**

```
Discusión (5 minutos):
Dev 1: "Necesitamos agregar campo de base de datos, crear formulario, conectar biblioteca TOTP"
Dev 2: "Sí, suena como una tarea media"
Dev 3: "Hemos hecho algo similar con confirmación de correo"
PO: "Los Criterios de Aceptación son simples: habilitar, deshabilitar, usar en inicio de sesión"

Votación: 5, 5, 5, 8
Consenso: 5 SP

Pensamiento: "La funcionalidad principal es clara, la biblioteca hará todo"
```

**Step Estimation (estimación pesimista):**

```
Detalle (20 minutos):

Pasos de Implementación:
1. Crear migración para campo two_factor_secret en tabla users
2. Agregar campo two_factor_enabled (boolean)
3. Agregar métodos enable2FA/disable2FA al modelo User
4. Instalar biblioteca para generación de códigos TOTP
5. Estudiar documentación de biblioteca para casos extremos
6. Crear controlador TwoFactorController
7. Implementar generación de código QR para configuración
8. Agregar verificación TOTP en el inicio de sesión en AuthController
9. Manejar caso cuando el usuario perdió el dispositivo
10. Crear sistema de códigos de respaldo de recuperación
11. Crear UI para habilitar/deshabilitar 2FA
12. Crear UI para mostrar código QR
13. Crear UI para mostrar códigos de respaldo
14. Agregar rate limiting para intentos de entrada de código
15. Escribir pruebas unitarias para modelo User (4 pruebas)
16. Escribir pruebas para TwoFactorController (5 pruebas)
17. Escribir pruebas para BackupCodeService (3 pruebas)
18. Escribir pruebas de integración (3 pruebas)
19. Actualizar documentación de API
20. Probar en diferentes dispositivos
21. Probar integración con aplicaciones móviles

Pruebas: ~15 unitarias + 3 integración = 18 pruebas

Discusión:
Dev 1: "Oh, olvidé los códigos de respaldo en la primera estimación"
Dev 2: "Y tampoco pensé en rate limiting"
Dev 3: "Las pruebas tomarán más tiempo del que pensé"
Tech Lead: "Además necesitamos considerar seguridad y casos extremos"

Re-estimación: 5 SP → 8 SP

Pensamiento: "Cuando empiezas a detallar, entiendes el alcance real del trabajo"
```

### Ejemplo 2: Corrección después del detalle

**Tarea:** "Agregar exportación de informes a PDF y Excel"

**Refinement (optimista):**

```
Equipo: "Las bibliotecas para PDF y Excel están listas,
solo conectamos y agregamos botón de exportación"

Estimación: 3 SP
```

**Step Estimation (pesimista):**

```
El detalle reveló:

1. Selección de bibliotecas (investigación):
   - Comparar 3 bibliotecas PDF
   - Comparar 2 bibliotecas Excel
   - Verificar licencias

2. Exportación PDF (8 pasos):
   - Configurar biblioteca
   - Configurar fuentes (más allá del latín)
   - Manejar tablas
   - Manejar gráficos
   - Configurar paginación
   - Agregar estilos de empresa (logo, colores)
   - Optimizar tamaño de archivo
   - Pruebas (4 pruebas)

3. Exportación Excel (6 pasos):
   - Configurar biblioteca
   - Exportar datos de tabla
   - Formato de celdas
   - Fórmulas para filas totales
   - Protección de hojas
   - Pruebas (3 pruebas)

4. UI e integración (5 pasos):
   - Agregar botones de exportación
   - Agregar selección de formato
   - Barra de progreso para informes grandes
   - Manejo de errores
   - Pruebas de UI (2 pruebas)

5. Rendimiento (3 pasos):
   - Generación en segundo plano para archivos grandes
   - Límites de tamaño de datos
   - Limpieza de archivos temporales

6. Documentación y casos extremos (3 pasos):
   - Actualizar documentación de usuario
   - Pruebas con volúmenes de datos límite
   - Pruebas con varios navegadores

Total: 25+ pasos, 9+ pruebas

Discusión:
Dev: "Oh, olvidé completamente otros idiomas en PDF..."
QA: "¿Y cómo manejamos la situación con un millón de filas?"
Tech Lead: "Necesitaremos procesamiento en segundo plano, esa es una tarea separada"

Decisión: Dividir en 2 tareas:
- "Exportación PDF" - 5 SP
- "Exportación Excel" - 3 SP
En lugar de los 3 SP iniciales para todo
```

---

## Niveles de aplicación de la metodología

SBE puede aplicarse con diferentes grados de detalle dependiendo de las necesidades del equipo:

### Nivel básico (implementación mínima)

**Lo que hacemos:**

- Realizamos sesiones de Refinement + Step Estimation
- Descomponemos tareas en pasos concretos
- Analizamos dependencias para paralelización
- Estimamos las pruebas requeridas

**Lo que obtenemos:**

- Estimaciones más precisas
- Mejor planificación del sprint
- Previsibilidad del volumen de pruebas
- Balance entre optimismo de Refinement y realismo de Step Estimation

**Esfuerzo:** +10-15% de tiempo de planificación (1.5 horas adicionales de Step Estimation)

### Nivel avanzado (con retrospectiva)

**Adicionalmente hacemos:**

- Registramos pasos realmente completados
- Comparamos plan con realidad
- Analizamos patrones de divergencia
- Creamos plantillas para tareas típicas

**Adicionalmente obtenemos:**

- Mejora continua de precisión de estimaciones
- Base de conocimiento del equipo sobre tareas típicas
- Identificación de problemas sistémicos del proceso

**Esfuerzo adicional:** +5-10% de tiempo para retrospectiva

---

## Implementación de la metodología

### Etapa inicial (1-2 sprints) - Nivel básico

**Cambios organizacionales:**

- Agregar sesión de Step Estimation al calendario del equipo (1-1.5 horas/sprint)
- Definir criterios para votación de tareas
- Crear plantilla para registro de Pasos de Implementación

**Proceso:**

- Seleccionar 2-3 tareas para Step Estimation por votación
- Enfoque en descomposición y análisis de dependencias
- Estimar cobertura de pruebas requerida
- Comparar estimaciones optimistas y pesimistas

### Desarrollo (3-6 sprints) - Puede agregar retrospectiva

- Expandir número de tareas detalladas (hasta 5-7)
- Crear plantillas para tipos de tareas recurrentes
- _(Opcional)_ Comenzar a recopilar datos: planificado vs real
- _(Opcional)_ Analizar patrones de divergencia

---

## Retorno de inversión de la metodología

### Nivel básico

**Inversión:** +10-15% de tiempo de planificación (1.5 horas adicionales de Step Estimation)

**Retorno:**

- Reducción de sobrecostos
- Mejora de planificación de pruebas
- Mayor previsibilidad de plazos

### Nivel avanzado

**Inversión:** +15-25% de tiempo para planificación y retrospectiva

**Retorno:**

- Reducción adicional de sobrecostos
- Mejora continua del proceso
- Acumulación de base de conocimiento del equipo
- Reducción de tiempo para tareas similares en el futuro
