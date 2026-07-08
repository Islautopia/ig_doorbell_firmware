# 🐚 IG Doorbell — Firmware

Este repositorio guarda los binarios de firmware publicados para **IG Doorbell**, el
videoportero de [Islautopia](https://islautopia.com). Aquí no vive el código fuente (ese sigue
en un repositorio privado) — esto es únicamente el punto de distribución: el propio dispositivo
y la app móvil vienen aquí a mirar "¿hay algo más nuevo que lo que tengo instalado?".

## ¿Cómo funciona?

Cada fila de la tabla de [Releases](../../releases) es una versión real que en algún momento ha
corrido en un IG Doorbell de verdad. El nombre de la versión (`0.<fase>.<subfase>`, por ejemplo
`0.26.0`) es el mismo número que el propio dispositivo devuelve en `GET /api/firmware_info` —
así que comparar "¿mi versión instalada es menor que la última publicada aquí?" es una
comparación directa de cadenas, sin trucos.

Cada release incluye:
- El binario, nombrado `ig_doorbell-hw<hw_version>.bin` (por ejemplo `ig_doorbell-hw1.0.1.bin`),
  listo para flashear por OTA. **La versión de hardware va en el propio nombre del fichero a
  propósito** — el día que exista más de una revisión de placa, una misma release puede traer
  varios binarios (uno por `hw_version` compatible), y quien consuma esto (la app) debe elegir
  el asset cuyo nombre contenga el `hw_version` que el propio dispositivo reporta en
  `GET /api/firmware_info` — nunca asumir que "el último asset" es válido para todo el parque.
- Notas de la versión — qué cambió, en lenguaje llano, no un `git log` en crudo.

Cuando hay una versión nueva, el propio dispositivo (con tu permiso, nunca solo) se descarga el
`.bin` de aquí directamente por HTTPS y se actualiza él mismo. Nadie sube nada a mano al
dispositivo — el dispositivo viene a buscarlo.

## ¿Por qué es público si el código no lo es?

Porque el propio IG Doorbell necesita poder descargar el binario sin ninguna credencial
guardada dentro de su propio firmware — guardar tokens de terceros dentro de un dispositivo
físico es justo el tipo de cosa que este proyecto ha evitado siempre. Que el binario compilado
sea descargable no es lo mismo que el código fuente sea abierto: siguen siendo cosas bien
distintas, ver la licencia abajo.

## Licencia

Todos los derechos reservados © Islautopia. La publicación de estos binarios en un repositorio
público **no concede ningún derecho** de uso, copia, modificación, ingeniería inversa o
redistribución, salvo el uso previsto: actualizar por OTA un dispositivo IG Doorbell legítimo.
No hay ninguna licencia de código abierto asociada a este repositorio.

---

<sub>Mantenido automáticamente junto al firmware — si algo aquí no cuadra con lo que tu
dispositivo reporta, dínoslo.</sub>
