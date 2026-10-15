# ADR 0001: Diseño Estructural y de Flujos para el Sistema FitZone

## Contexto
El gimnasio FitZone requiere la automatización de su gestión operativa, específicamente en el control de accesos, gestión de membresías y reservación de clases[cite: 5]. Actualmente operan de manera manual, lo que genera inconsistencias en los ingresos y una alta incidencia de lugares vacíos por *No-Shows*[cite: 5]. En la Fase 2 del diseño arquitectural[cite: 2], es necesario definir la estructura orientada a objetos (clases) y mapear los flujos de comunicación entre componentes para los escenarios más críticos.

## Decisión
Se ha decidido documentar la estructura del sistema utilizando diagramas UML (Clases y Secuencia) generados a partir de los requerimientos funcionales (BRD y User Stories)[cite: 3, 9]. 

1. **Diagrama de Clases:** Se definieron entidades clave del dominio como `Socio`, `Membresia`, `ClaseEspecial` y `Reserva` para mantener un control estricto sobre el aforo y la vigencia[cite: 21, 22].
2. **Diagramas de Secuencia:** Se seleccionaron los dos flujos operativamente más complejos según el BPMN[cite: 23]:
   - **Reserva de Clase:** Gestiona validaciones de membresía, cobros por servicios fuera de plan y la delegación de cupos a la lista de espera[cite: 23].
   - **Control de Acceso y No-Shows:** Automatiza el registro de entradas, la penalización de reservas abandonadas y la reasignación en tiempo real a usuarios en lista de espera[cite: 23].

## Consecuencias
- **Positivas:** Permite a los desarrolladores visualizar claramente qué componentes interactúan durante las validaciones de recepción y las reglas de negocio, garantizando que no se sobrepase la capacidad máxima[cite: 21, 22].
- **Negativas:** Obliga a que la base de datos (que diseñará otro integrante en el modelo de dominio) coincida exactamente con las propiedades estipuladas en el diagrama de clases para evitar discrepancias arquitectónicas.