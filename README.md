# Microjuego Asteroids

## Descripción 

Este proyecto es un juego 2D de tipo **arcade espacial** inspirado en el clásico Asteroids. El jugador controla una nave espacial que debe destruir meteoritos que caen desde la parte superior de la pantalla. Al destruir un meteorito, este se divide en fragmentos más pequeños, y el jugador gana puntos. Si un meteorito impacta contra la nave, el jugador pierde.

El juego incluye un sistema de puntuación, un menú de pausa, y una dificultad progresiva que aumenta la frecuencia de aparición de meteoritos con el tiempo.

## Arquitectura

### Diseño y Comunicación

El proyecto sigue una arquitectura basada en componentes típica de Unity, donde cada objeto del juego (nave, bala, meteorito) es un `GameObject` con scripts independientes que gestionan su comportamiento. 

La comunicación entre objetos se realiza mediante:

- **Colisiones físicas** (`OnCollisionEnter`) para detectar impactos.

- **Variables estáticas** (`Player.SCORE`) para compartir la puntuación global.

- **Referencias directas entre componentes** (por ejemplo, el `Player` instancia balas desde un `bulletPrefab`).

### Funcionamiento

#### Jugador (`Player`):
  
  - Se mueve con fuerzas físicas (`Rigidbody.AddForce`) aplicadas en la dirección `transform.right`.
  
  - Rota con las teclas de dirección horizontal.
  
  - Dispara balas al presionar `Espacio`.
  
  - Si colisiona con un enemigo, reinicia la escena y resetea la puntuación.

#### Bala (`Bullet`):
 
  - Se mueve en línea recta en la dirección `targetVector`.
  
  - Se destruye automáticamente después de `maxLifeTime` segundos.
  
  - Al colisionar con un enemigo, incrementa la puntuación y destruye ambos objetos.

#### Meteorito (`Meteor`):
  
  - Tiene un tamaño (`tamaño`) que determina si se divide al ser impactado.
  
  - Si `tamaño > 1`, al recibir un impacto de bala se divide en dos meteoritos más pequeños con direcciones aleatorias.
  
  - Se destruye al salir de la pantalla o tras un tiempo límite.

#### Spawner de enemigos (`EnemySpawner`):
 
  - Genera meteoritos en posiciones aleatorias en el eje X, en la parte superior.
  
  - Aumenta gradualmente la tasa de aparición (`spawnRatePerMinute`) con el tiempo.

#### Menú de pausa (`MenuPausa`):
 
  - Pausa el juego con la tecla `P`, mostrando un panel y texto de pausa.
  
  - Reanuda el juego con la misma tecla.

#### Puntuación:
  
  - Se muestra en un `Text` de UI.
  
  - Se actualiza cada vez que una bala destruye un enemigo.

### Tecnologías

- Lenguaje: **C#**
- Motor Gráfico: **Unity**

## Estructura del proyecto

```plaintext
.
├── Assets/                            
│   ├── Prefabs/
│   │   ├── Bullet.prefab                   # Prefab de la bala
│   │   ├── Bullet.prefab.meta
│   │   ├── Meteor.prefab                   # Prefab del meteorito
│   │   └── Meteor.prefab.meta
│   │   
│   ├── Scenes/
│   │   ├── SampleScene.unity               # Escena principal del juego
│   │   └── SampleScene.unity.meta
│   │
│   ├── Script/
│   │   ├── Bullet.cs                       # Comportamiento de la bala
│   │   ├── Bullet.cs.meta
│   │   ├── EnemySpawner.cs                 # Generador de meteoritos
│   │   ├── EnemySpawner.cs.meta
│   │   ├── MenuPausa.cs                    # Menú de pausa
│   │   ├── MenuPausa.cs.meta
│   │   ├── Meteor.cs                       # Comportamiento del meteorito
│   │   ├── Meteor.cs.meta
│   │   ├── Player.cs                       # Control del jugador
│   │   └── Player.cs.meta
│   │    
│   │
│   ├── Sprites/
│   │    ├── Bullet.png                      # Sprite de la bala
│   │    ├── Bullet.png.meta
│   │    ├── Meteor.png                      # Sprite del meteorito
│   │    ├── Meteor.png.meta
│   │    ├── Ship.png                        # Sprite de la nave
│   │    ├── Ship.png.meta
│   │    ├── Space.jpg                       # Fondo espacial
│   │    └── Space.jpg.meta
│   │      
│   ├── DefaultVolumeProfile.asset
│   ├── DefaultVolumeProfile.asset.meta
│   ├── Prefabs.meta
│   ├── Scenes.meta 
│   ├── Script.meta  
│   ├── Sprites.meta
│   ├── UniversalRenderPipelineGlobalSettings.asset
│   └── UniversalRenderPipelineGlobalSettings.asset.meta
│
├── INSTRUCTIONS.md                          # Instrucciones de instalación y ejecución del proyecto
└── README.md                                # Descripción del proyecto
```

## Instalación y ejecución

Ver [INSTRUCTIONS.md](INSTRUCTIONS.md)
