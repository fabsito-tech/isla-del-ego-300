# Isla del Ego — Centro de alto rendimiento

Simulador web original de gestión y desarrollo de futbolistas ficticios. Construí tu quinteto, entrená a los jugadores y competí por la cima de un complejo de cinco divisiones en una isla 3D.

**Demo:** https://fabsito-tech.github.io/isla-del-ego-300/

## Cómo jugar

Abrí la demo en un navegador moderno. Para ejecutar localmente, cloná el repositorio y levantá un servidor estático desde la carpeta del proyecto, por ejemplo:

```bash
python3 -m http.server 8000
```

Después abrí `http://localhost:8000`. El render 3D usa Three.js desde CDN, así que la primera carga requiere conexión a internet. La partida se guarda en el almacenamiento local del navegador.

## MVP implementado

- Isla 3D con complejo pentagonal de cinco sectores; cámara orbital con giro y zoom y sectores seleccionables.
- 300 futbolistas originales distribuidos en cinco divisiones de 60 y 12 quintetos por división.
- Fichas de jugador con posición, estadísticas, energía de 50, ego, historial, entrenamientos, victorias, rivalidad y evolución.
- Entrenamientos con 50 rutinas diferentes y mejoras estadísticas específicas.
- Energía, descanso y sueño. Cada sesión de entrenamiento consume energía y el rendimiento de partido pondera el cansancio.
- Descanso obligatorio al completar bloques de 25 entrenamientos: 10 minutos antes de retomar entrenamiento intenso.
- Progreso offline calculado al volver, limitado a ocho horas por sesión, con resumen de actividad y recuperación.
- Partidos importantes cada 100 entrenamientos por jugador (o con quinteto disponible para facilitar la prueba), resultado base cercano al 50/50 y recompensas.
- Monedas del juego y seis entrenadores con beneficios distintos. Sin compras con dinero real.
- Ranking de 300 jugadores, quinteto ideal, rivalidades, despertar temporal, evoluciones, cambios manuales de división e historial.
- Diseño responsive y guardado local automático.

## Estructura

- `index.html`: estructura de vistas y navegación.
- `styles.css`: interfaz adaptable.
- `src/data.js`: datos de divisiones, jugadores, estadísticas, 50 entrenamientos y entrenadores.
- `src/game.js`: dominio y reglas de simulación, guardado, progreso offline, energía, partidos y ranking.
- `src/world.js`: isla y edificios 3D con Three.js.
- `src/main.js`: interfaz y conexión de los sistemas.
- `manifest.webmanifest`, `sw.js`: metadatos PWA y caché básica.

## Controles

- Arrastrá sobre la isla para girar la cámara; usá la rueda o pellizco para acercar/alejar.
- Hacé clic en un sector para filtrar sus jugadores.
- Abrí **Jugadores**, elegí un jugador, seleccioná una rutina y entrenalo; también podés descansar, dormir o iniciar una rivalidad.
- **Simular 1 hora** avanza las actividades automáticas del centro.
- **Partido importante** disputa un encuentro con los jugadores que ya tienen entrenamientos.
- **Entrenadores** permite contratar personal usando monedas ganadas jugando.

## Diseño y alcance

Los 300 nombres se generan combinando nombres y apellidos ficticios para esta partida. Los personajes y equipos son originales; el proyecto toma como referencia general la idea de una competencia de fútbol de alto rendimiento, sin reproducir personajes oficiales, ilustraciones ni marcas de terceros. El render utiliza edificios y elementos geométricos placeholder, listos para reemplazar por modelos 3D y animaciones propios.

El guardado es local al navegador y al dispositivo, no hay cuentas ni sincronización en servidor todavía. Para mantener la demo ligera, el ranking muestra la primera página de 100 posiciones; los cálculos se mantienen sobre los 300 jugadores.

## Próximas tareas

- [ ] Completar navegación interior/explorable para dormitorios, comedor, descanso y canchas.
- [ ] Añadir modelos de personaje, navegación entre zonas y animaciones de actividad con mixer/estados.
- [ ] Mejorar simulación de partidos: alineación editable, rivales por división, táctica y probabilidad explicable.
- [ ] Aplicar promociones y descensos automáticos por ciclo, con posibilidad de remontar.
- [ ] Añadir persistencia en nube/exportar-importar partida y pruebas automatizadas del balance.
- [ ] Mostrar tabla completa del ranking con filtros, búsqueda y paginación.
- [ ] Profundizar personalidad, egos, habilidades desbloqueables y rivalidades con efectos jugables.
- [ ] Optimizar render y caché/offline completo de dependencias externas.
- [ ] Añadir localización, accesibilidad, sonido y tutorial inicial.
