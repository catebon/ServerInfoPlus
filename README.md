# ServerInfoPlus v2.2.0 📊

![Version](https://img.shields.io/badge/version-2.2.0-blue)
![Java](https://img.shields.io/badge/java-17%2B-orange)
![Platform](https://img.shields.io/badge/platform-Spigot%20%7C%20Paper%20%7C%20Folia-lightgrey)

**ServerInfoPlus** es la solución definitiva para el monitoreo de servidores de Minecraft. Diseñado tanto para administradores novatos como expertos, este plugin te permite visualizar el estado de tu servidor en tiempo real, detectar causas de lag (como máquinas de redstone o plugins pesados) y recibir alertas automáticas antes de que los problemas afecten a tus jugadores.

Todo esto con una interfaz moderna, soporte para colores hexadecimales y una configuración flexible.

---

## 📑 Índice
1. [Instalación Rápida](#-instalación-rápida)
2. [Características y Ejemplos Prácticos](#-características-y-ejemplos-prácticos)
    - [Monitoreo en Tiempo Real](#1-monitoreo-en-tiempo-real)
    - [Detector de Lag de Redstone](#2-detector-de-lag-de-redstone)
    - [Analizador de Rendimiento de Plugins](#3-analizador-de-rendimiento-de-plugins)
    - [Sistema de Alertas Automáticas](#4-sistema-de-alertas-automáticas)
    - [Menús Interactivos (GUIs)](#5-menús-interactivos-guis)
3. [Comandos y Permisos](#-comandos-y-permisos)
4. [Variables (Placeholders)](#-variables-placeholders)
5. [Configuración](#-configuración)

---

## 🚀 Instalación Rápida

Sigue estos 4 pasos sencillos para tener el plugin funcionando en menos de 2 minutos:

1.  **Descargar**: Baja el archivo `ServerInfoPlus-2.2.0.jar`.
2.  **Instalar**: Arrastra el archivo a la carpeta `plugins` de tu servidor.
3.  **Dependencias**: Asegúrate de tener instalado [PlaceholderAPI](https://www.spigotmc.org/resources/placeholderapi.6245/) (¡Es muy recomendado para aprovechar todas las funciones!).
4.  **Reiniciar**: Enciende o reinicia tu servidor.

> **Nota**: El plugin creará automáticamente una carpeta `ServerInfoPlus` con los archivos de configuración.

---

## ✨ Características y Ejemplos Prácticos

Aquí es donde ServerInfoPlus brilla. A continuación, explicamos cada función con ejemplos de la vida real.

### 1. Monitoreo en Tiempo Real
Visualiza métricas críticas como TPS (Ticks por Segundo), uso de CPU, Memoria RAM y Ping de los jugadores.

**💡 Ejemplo Práctico:**
Un jugador se queja de "lag". Tú escribes `/si` en el chat o consola.
*   **Resultado**: Ves que el TPS está en **19.98** (Perfecto) pero el Ping del jugador es **300ms**.
*   **Conclusión**: El problema es la conexión a internet del jugador, no tu servidor. ¡Has ahorrado tiempo buscando problemas inexistentes!

### 2. Detector de Lag de Redstone
Encuentra automáticamente zonas donde se está abusando de la redstone, lo cual es una de las causas más comunes de lag en servidores Survival o Skyblock.

**💡 Ejemplo Práctico:**
El servidor empieza a ir lento (TPS baja a 15).
1.  Escribes `/si redstone` para ver el reporte.
2.  El plugin te dice: `⚡ Hotspot encontrado en World: survival, X: 100, Z: -500 (Actividad: 50 eventos/seg)`.
3.  Haces click en la alerta o escribes `/si redstone tp survival 100 -500`.
4.  **Resultado**: Te teletransportas y encuentras un reloj de redstone masivo que un jugador olvidó apagar. Lo rompes y el TPS vuelve a 20.

### 3. Analizador de Rendimiento de Plugins
¿Sientes que el servidor va lento pero no es por construcciones? Puede ser un plugin mal optimizado.

**💡 Ejemplo Práctico:**
Instalaste 3 plugins nuevos ayer y hoy el servidor va lento.
1.  Escribes `/si pluginperf`.
2.  El plugin analiza qué procesos están tardando más.
3.  **Resultado**: Muestra que "RandomTeleport" está consumiendo el 40% del tiempo del tick.
4.  **Acción**: Ya sabes exactamente qué plugin borrar o configurar para arreglar el lag.

### 4. Sistema de Alertas Automáticas
No necesitas estar conectado las 24 horas mirando la pantalla. Configura alertas para que el plugin te avise (a ti o a Discord) cuando algo va mal.

**💡 Ejemplo Práctico de Configuración:**
Quieres que te avise si la memoria RAM se llena.
En `config.yml`:
```yaml
alerts:
  memory:
    enabled: true
    above: 90.0  # Avisar si se usa más del 90%
    message: "&c¡Cuidado! La memoria está al 90%."
```
*   **Resultado**: Cuando el servidor alcanza el 91% de uso de RAM, todos los administradores (con permiso `serverinfo.admin`) reciben el aviso en el chat.

### 5. Menús Interactivos (GUIs)
Olvídate de comandos complicados. Usa menús gráficos tipo cofre para gestionar todo.

**💡 Ejemplo Práctico:**
Quieres ver qué mundos hay cargados y teletransportarte a uno.
1.  Escribes `/si gui`.
2.  Se abre un inventario con iconos.
3.  Haces click en el icono de "Mundos".
4.  **Resultado**: Ves una lista de todos los mundos (Nether, End, mundos de recursos).
5.  Haces click en "Recursos_V2" y te teletransportas instantáneamente allí.

---

## 💻 Comandos y Permisos

| Comando | Alias | Descripción | Permiso Requerido |
| :--- | :--- | :--- | :--- |
| `/serverinfo` | `/si`, `/stats` | Muestra el estado general del servidor. | `serverinfo.use` |
| `/si help` | | Lista todos los comandos disponibles. | `serverinfo.use` |
| `/si gui` | | Abre el panel de control gráfico. | `serverinfo.gui.main` |
| `/si redstone` | | Muestra fuentes de lag de redstone. | `serverinfo.redstone` |
| `/si pluginperf` | | Analiza el impacto de los plugins. | `serverinfo.pluginperf` |
| `/si reload` | | Recarga la configuración del plugin. | `serverinfo.reload` |
| `/si test <papi>` | | Prueba si un placeholder funciona. | `serverinfo.admin` |

**Nota de Permisos**: Si eres OP, tienes acceso a todo automáticamente. Para rangos (como Moderadores), dales `serverinfo.use` y `serverinfo.gui.main`.

---

## 🧩 Variables (Placeholders)

Si usas plugins como **Scoreboard**, **TabList** o **Holograms**, puedes usar estas variables para mostrar datos de ServerInfoPlus en ellos.

| Variable | Descripción | Ejemplo de Salida |
| :--- | :--- | :--- |
| `%serverinfo_tps%` | TPS actual formateado con colores. | <span style="color:green">20.00</span> |
| `%serverinfo_cpu%` | Uso de CPU del servidor. | 4.5% |
| `%serverinfo_memory_percent%` | Porcentaje de RAM usada. | 45% |
| `%serverinfo_ram_used%` | Cantidad exacta de RAM usada. | 2048 MB |
| `%serverinfo_ram_max%` | RAM total asignada al servidor. | 8192 MB |
| `%serverinfo_ping%` | Ping del jugador que mira. | 45ms |
| `%serverinfo_uptime%` | Tiempo desde que se encendió el servidor. | 2d 4h 12m |

**💡 Ejemplo Práctico en un Scoreboard:**
En la config de tu plugin de scoreboard:
```yaml
lines:
  - "&eEstado del Servidor:"
  - "TPS: %serverinfo_tps%"
  - "RAM: %serverinfo_memory_percent%%"
  - "Ping: %serverinfo_ping% ms"
```

---

## ⚙️ Configuración

El archivo `config.yml` está completamente comentado en español para facilitarte la vida. Aquí tienes los aspectos más importantes que puedes cambiar:

*   **Mensajes y Colores**: Usa códigos hexadecimales (`&#RRGGBB`) o gradientes para que coincidan con la estética de tu servidor.
*   **Umbrales de Alerta**: Define qué consideras "lag" (por ejemplo, bajar de 18 TPS) para ajustar cuándo saltan las alarmas.
*   **Base de Datos**: Puedes guardar el historial de rendimiento en SQLite (archivo local, por defecto) o conectar una base de datos MySQL si tienes una red de servidores (Bungeecord/Velocity).

---

### ¿Necesitas Ayuda?
Si tienes problemas o sugerencias, únete a nuestro [Discord de Soporte](https://discord.gg/3eEpJXqUak).

*Desarrollado con ❤️ para la comunidad de Minecraft.*
