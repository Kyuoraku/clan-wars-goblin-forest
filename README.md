# Bosque Ciénaga

Recreación en JavaScript de las mecánicas de *Clan Wars: Goblin Forest* (Agame, ~2010),
un **lane battler / tug-of-war** al estilo *Age of War*. Canvas 2D puro, sin dependencias.

El juego original es Flash y nunca publicó su tabla de balance. Las mecánicas acá están
reconstruidas desde fuentes públicas; **todos los números son de diseño propio**. Assets
originales, ninguno. Nada del SWF original se reutiliza.

## Correr

Abrí `index.html` en el navegador. No hay build ni servidor.

## Controles

| Acción | Tecla |
|---|---|
| Entrenar Bruto | `1` o el botón |
| Entrenar Arquero | `2` o el botón |
| Mover cámara | `←` `→` o `A` / `D`, o el mouse en los bordes |

## Mecánicas de la v1

- **Bounty por posición** — la recompensa por muerte escala de `0.5x` en tu base a `3.0x`
  en la enemiga. Es la mecánica que define al juego: castiga quedarte defendiendo.
  También cobrás un consuelo cuando muere tu propia gente, como el original.
- **Línea de frente sin física** — las unidades de cada bando se ordenan por avance y se
  propaga un `wallX`: el de adelante se frena al entrar en rango y los de atrás respetan
  `SPACING`. Así se forman bloques en vez de amontonarse en el mismo píxel.
- **Fixed timestep** a 60Hz con acumulador, render desacoplado. La simulación es
  determinista aunque caiga el frame rate.
- Dos unidades (Bruto melee, Arquero ranged), cañones en ambas bases con proyectil de
  viaje real, cola de entrenamiento de a uno, pop cap, ingreso pasivo e IA rival que
  aprieta con el tiempo.

## Afuera por ahora

XP y reputación · upgrades · hechizos · héroe (el Chief, a 6.000 XP en el original) ·
terreno con altura. Para lo último el hueco ya está: `GROUND_Y` es constante y habría que
reemplazarlo por un `heightAt(x)`.

## Dónde tocar el balance

Todo vive arriba de `index.html`: el objeto `UNITS`, `BASE`, `POP_CAP`, `INCOME` y las
constantes `BOUNTY_MIN` / `BOUNTY_MAX`.
