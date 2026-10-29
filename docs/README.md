# Documentación del Proyecto Integrador: Juego Educativo de Pesca (Veracruz)

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

    UC3 -.->|include| UC4
