# DOSW_LABORATORIO_3_CarlosCristianJulian

Laboratorio 3 - DOSW 2026-2
Asignatura: Desarrollo y Operaciones de Software (DOSW)
Modalidad: Equipos - 3 personas

Integrantes del equipo:
- Carlos Sanchez
- Cristian Moreno
- Julian Morales

Objetivo del laboratorio:
Aplicar herramientas de definicion y analisis de requerimientos a partir de un caso de estudio practico, y herramientas de planeacion usando el framework Agile Scrum con Jira. El sistema definido es la base del proyecto de API que se construira durante el segundo corte.

Workspace de Jira:
- Enlace al proyecto: https://carlossanchez8.atlassian.net/jira/software/projects/DOSW2026/boards/2/backlog

---

# Parte 1 - Preguntas sobre Pull Requests en GitHub

## Que es un Pull Request en GitHub?

Un Pull Request (PR) es una solicitud formal para integrar los cambios de una rama origen a una rama destino. Permite que otros miembros del equipo revisen el codigo, dejen comentarios, propongan mejoras y validen que se cumplen los estandares de calidad antes de incorporar los cambios a la rama principal.

## Como se crea un Pull Request en GitHub?

1. Crear una rama de trabajo a partir de develop y realizar los cambios correspondientes.
2. Hacer commit de las modificaciones y subirlas con git push al repositorio remoto.
3. Ingresar al repositorio en GitHub y navegar a la pestaña Pull requests.
4. Hacer clic en el boton New pull request.
5. Seleccionar la rama de origen (feature) y la rama de destino (develop o main).
6. Escribir un titulo representativo y una descripcion detallada de los cambios.
7. Seleccionar Create pull request.

## Como se aprueba un Pull Request en GitHub?

1. Entrar al Pull Request asignado para revision.
2. Ir a la pestaña Files changed y examinar detenidamente las diferencias de codigo.
3. Si se requiere agregar comentarios puntuales en lineas especificas, hacerlo.
4. Hacer clic en el boton Review changes.
5. Seleccionar la opcion Approve y escribir un comentario de aprobacion.
6. Confirmar la revision con Submit review.
7. Una vez aprobado por los revisores requeridos, se realiza el Merge pull request para integrar los cambios y se elimina la rama origen.

---

# Parte 7 - Preguntas Reflexivas sobre Planning Poker

## Cual fue la mayor dificultad a la hora de estimar?

La principal dificultad consistio en calibrar la incertidumbre tecnica frente a la complejidad funcional de las historias de usuario. Específicamente, genero debate diferenciar el esfuerzo entre los componentes de interfaz de usuario (como el selector accesible de terminos de coccion) y la logica de negocio en el backend con validacion concurrente de inventario y estado. Adicionalmente, costo dimensionar el impacto tecnico de cumplir con los requerimientos no funcionales, tales como la actualizacion del tablero de cocina en tiempo real en menos de 2 segundos.

## Fue facil llegar a un consenso?

En su mayoria si, debido a que el desglose previo en subtareas tecnicas realizado en la Parte 5 sirvio como referencia objetiva del alcance real de cada historia. Para historias con alcance puntual y aislado, como el bloqueo de platos con insumos agotados (HU-02), el consenso fue directo en 3 puntos. En cambio, para historias que conectan varios modulos (como la recepcion de pedidos en cocina), se requirio una ronda adicional de argumentacion para acordar el nivel de esfuerzo adecuado.

## Como resolvieron las discrepancias grandes?

Se aplico la dinamica estandar de Planning Poker: cuando aparecieron votos distantes entre los integrantes (por ejemplo, una votacion entre 3 y 8 puntos), quienes emitieron los puntajes extremos expusieron sus motivos tecnicos. Quien voto mas alto señalo los retos de implementar comunicacion asincrona o WebSockets para el tiempo real, mientras que quien voto mas bajo supuso una consulta periodica basica. Una vez aclarados los supuestos de diseno y el alcance minimo viable para el MVP, el equipo llego a un punto medio consensuado dentro de la serie de Fibonacci (5 puntos).

---

# Bibliografia

- Atlassian. (s. f.). Que es un pull request. Atlassian Git Tutorial. https://www.atlassian.com/es/git/tutorials/making-a-pull-request
- Cohn, M. (2005). Agile Estimating and Planning. Prentice Hall.
- GitHub. (s. f.). About pull requests. GitHub Docs. https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests
- GitHub. (s. f.). Creating a pull request. GitHub Docs. https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request
- Schwaber, K., & Sutherland, J. (2020). La Guia de Scrum. Scrum.org.
