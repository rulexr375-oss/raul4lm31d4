# Documentación del Proyecto Integrador: Veracruz Oddysee

## 1. Introducción
Este documento presenta el modelado UML (Casos de Uso y Diagramas de Clases) para el desarrollo del videojuego educativo enfocado en la conservación ambiental y la pesca sustentable en el estado de Veracruz.

## 2. Diagrama de Casos de Uso General
El diagrama general describe los flujos interactivos entre el usuario estudiante, el sistema y las reglas de concientización ambiental implementadas.

```mermaid
graph LR
    subgraph Sistema de Juego Educativo - Veracruz
        UC1[Iniciar / Configurar Partida]
        UC2[Explorar Zona de Pesca en Veracruz]
        UC3[Lanzar Cordel / Capturar Especie]
        UC4[Consultar Enciclopedia y Leyes de Veda]
        UC5[Ver Estadísticas de Conservación]
        UC6[Gestionar Base de Datos de Especies]
    end

    Jugador((Jugador / Estudiante)) --> UC1
    Jugador --> UC2
    Jugador --> UC3
    Jugador --> UC4
    Jugador --> UC5

    Admin((Administrador / Docente)) --> UC6
    Admin --> UC4

    UC3 -.->|include| UC4
```

## 3. Diagrama de Clases del Módulo Principal
El diagrama de clases detalla la estructura orientada a objetos para gestionar las reglas de veda, tallas mínimas, zonas protegidas y el progreso del jugador.

```mermaid
classDiagram
    class Jugador {
        +String idJugador
        +String nombreUsuario
        +int puntajeTotal
        +int nivelConciencia
        +iniciarPartida()
        +consultarEnciclopedia()
    }

    class Partida {
        +String idPartida
        +String fechaInicio
        +int puntuacionActual
        +finalizarPartida()
    }

    class ZonaDePesca {
        +String idZona
        +String nombreUbicacion
        +String descripcionEcologica
        +verificarRestricciones()
    }

    class EspecieMarina {
        +String nombreComun
        +String nombreCientifico
        +boolean enPeligroExtincion
        +float tamanioMinimoLegal
        +boolean temporadaVedaActiva
        +validarCapturaSustentable()
    }

    class Captura {
        +String idCaptura
        +float pesoCapturado
        +float tamanioCapturado
        +boolean esLegal
        +String mensajeFeedbackEcologico
        +registrarCaptura()
    }

    Jugador "1" --> "*" Partida : juega
    Partida "1" --> "*" Captura : registra
    Captura "*" --> "1" EspecieMarina : involucra
    Captura "*" --> "1" ZonaDePesca : realizadaEn
    ZonaDePesca "1" --> "*" EspecieMarina : habitaEn
```

## 4. Herramientas Utilizadas
- **Mermaid:** Modelado colaborativo integrado directamente en Markdown y control de versiones en GitHub.
