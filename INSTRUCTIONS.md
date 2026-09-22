# Instrucciones de instalación y ejecución

## Requisitos

- **Unity Hub**
- **Unity Editor**, Recomendado: **Unity 6 (6000.x LTS)**

## Instalación

### 1. Clonar el repositorio

```bash
git clone https://github.com/tu-usuario/microjuego-asteroids.git
```

### 2. Abrir el proyecto en Unity

1. Abre **Unity Hub**.

2. Pulsa **Add → Add project from disk**.

3. Selecciona la carpeta raíz del proyecto (donde está `Assets/`).

4. Si Unity avisa de que falta la versión del editor, instálala desde el propio Hub.

5. Abre el proyecto. La primera importación puede tardar varios minutos.

## Ejecución

### Ejecutar dentro del editor (modo desarrollo)

1. En Unity, abre la escena:
   ```
   Assets/Scenes/SampleScene.unity
   ```

2. Pulsa el botón **Play** en la parte superior del editor.

3. El juego comenzará en la ventana **Game**.

### Ejecutar una build (versión compilada)

Si ya tienes una build generada:

- **Windows:** ejecuta `Asteroids.exe`.

- **macOS:** abre `Asteroids.app`.

- **Linux:** ejecuta `./Asteroids.x86_64`.

Si quieres **generar tu propia build**:

1. En Unity: **File → Build Settings…**

2. Selecciona la plataforma destino (Windows, macOS, Linux, WebGL…).

3. Pulsa **Build** y elige una carpeta de salida.

4. Ejecuta el binario generado.

## Cómo jugar

### Objetivo

Sobrevive el mayor tiempo posible destruyendo meteoritos. Cada meteorito destruido otorga puntos, y los meteoritos grandes se dividen en fragmentos más pequeños al ser impactados.

### Reglas básicas

1. **Dispara** a los meteoritos para destruirlos.

2. Los meteoritos **grandes** (`tamaño > 1`) se **dividen en dos** más pequeños al recibir un impacto.

3. Los meteoritos **pequeños** (`tamaño = 1`) se destruyen por completo.

4. Cada impacto suma **puntos** a tu marcador.

5. Si un meteorito **colisiona con tu nave**, pierdes y la escena se reinicia.

6. La **dificultad aumenta** con el tiempo: aparecen más meteoritos por minuto.

### Consejos

- Muévete constantemente para no ser un blanco fácil.

- Los meteoritos divididos salen en direcciones aleatorias: mantén distancia.

- Usa los bordes de la pantalla como "teletransporte" (la nave reaparece al otro lado).

- Dispara con antelación a los meteoritos grandes para fragmentarlos lejos.

## Controles

| Acción | Tecla principal | Tecla alternativa |
|--------|-----------------|-------------------|
| Rotar a la izquierda | ← (izquierda) | A |
| Rotar a la derecha | → (derecha) | D |
| Acelerar (impulso) | ↑ (arriba) | W |
| Frenar / no acelerar | ↓ (abajo) | S |
| Disparar | Espacio | — |
| Pausar / Reanudar | P | — |

### Notas sobre los controles

- La nave funciona con **inercia física**: al dejar de acelerar, sigue moviéndose.

- **No hay fricción**, así que la nave no se detiene sola.

- Al salir por un borde, la nave **reaparece por el lado opuesto**.
