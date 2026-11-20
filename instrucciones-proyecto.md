# Robot profesor de inglés — Instrucciones del proyecto

## Qué es
Proyecto construido en público durante un mes: un robot con pantalla que actúa como tutor de inglés conversacional. Escucha, habla, muestra palabras, imágenes y textos en pantalla, y recuerda el progreso de cada usuario. Se documenta paso a paso en Twitter/X y todo (código y diseños 3D) se publica en un repositorio público de GitHub para que cualquiera pueda replicarlo.

## Objetivo del mes (MVP)
Robot que: (1) conversa en inglés por voz, (2) muestra en pantalla palabras, frases, imágenes y quizzes controlados por Claude, (3) guarda el progreso del usuario entre sesiones, (4) vive en una carcasa impresa en 3D.
Fuera del MVP ("temporada 2"): evaluación real de pronunciación, modo niño completo, multiusuario avanzado, servos/movimiento.
Si algo nuevo no encaja en el MVP, avisar del coste en tiempo antes de meterlo.

## Stack (provisional, cambiar aquí cuando se decida)
- Hardware: Raspberry Pi 5 (8 GB), pantalla táctil 7", micrófono USB (array), altavoz + amplificador. Impresión 3D: Anycubic Kobra S1 + ACE 2 Pro (multicolor).
- Voz: wake word (openWakeWord) → VAD → STT en la nube → Claude API → TTS con voz británica.
- Pantalla: web local en Chromium kiosk (cara animada + tarjetas). Claude la controla con tools: show_text, show_image, word_card, quiz, save_session.
- Datos: SQLite local por usuario; sincronización opcional con Notion al final de la sesión.
- Desarrollo: primero en PC, después en la Pi.

## Pedagogía
Base: un kit de tutoría de inglés en Notion (protocolo de enseñanza, hoja de progreso del alumno y currículo de 182 lecciones).
Adaptaciones para el robot: perfil y lección los inyecta el código (no se consulta Notion en tiempo real); logging vía tool save_session; reglas de uso de pantalla; sin referencias a teclear. Prompt adaptado en prompts/ del repo.

## Reglas del repositorio público
- Nunca secretos en el repo: claves solo en .env (en .gitignore), con .env.example. Revisar cada cambio antes de commit.
- Nunca datos personales reales (progreso, sesiones, enlaces privados, rutas locales); solo perfiles de ejemplo.
- Licencias: MIT para código, CC BY-SA 4.0 para diseños 3D (pendiente de confirmar).
- Privacidad por defecto: no guardar audio; el README explica qué datos van a cada API.
- Estructura: software/, prompts/, hardware/ (BOM, cableado), cad/ (STEP + STL), docs/ (diario semanal).

## Diseño 3D
- Diseñar con medidas reales de los componentes, no de fichas técnicas sin verificar.
- Versiones finales en cad/ del repo (STEP + STL).

## Plan de 4 semanas
- Semana 0: repo, README, BOM, pedido de componentes. Tuit de lanzamiento.
- Semana 1: prototipo en PC (voz ↔ Claude ↔ pantalla). Vídeo del primer diálogo + hilo de arquitectura.
- Semana 2: montaje en mesa sobre la Pi, medir latencia y coste por sesión. Publicar números.
- Semana 3: diseño e impresión de la carcasa. Renders, timelapses, fallos.
- Semana 4: integración, demo final, README replicable. Hilo resumen.

## Contenido para Twitter/X
- Cada post con algo visual (vídeo, foto, diagrama, captura de código).
- Contar también los fallos y los números reales (latencia, coste, horas).
- Al cerrar cada hito, proponer el borrador del tuit/hilo correspondiente.

## Cómo trabajar con Claude
- Respuestas breves, en español, directas y orientadas a acción; planes priorizados con acciones concretas.
- Cuestionar premisas y avisar si algo no cabe en el mes o desvía del MVP.
- Distinguir lo verificado (precios, specs, APIs: buscar antes de afirmar) de lo estimado.
- Código y documentación del repo en inglés; conversación en español.

## Decisiones pendientes
- Público objetivo del MVP: niños, adultos o ambos.
- Idioma de los tuits.
- Proveedores concretos de STT y TTS (calidad vs coste vs latencia).
- Confirmar licencias.
