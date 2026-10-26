# open-montage

## META
- id: open-montage
- owner: EduBalderas
- visibility: public
- idioma: en
- estado: estable
- tipo: producto
- nivel: L3
  - L0=gobernanza/política
  - L1=marca/metodología
  - L2=flujo/arquitectura
  - L3=producto ejecutable
  - L4=herramienta
- familia: ninguna
- origen: fork
- experimento: no
- nacido_de: calesthio/OpenMontage
- orquestado_por: agente
- brief_desde: N/A

## OBJETIVO
Sistema open source que convierte un asistente de código en un estudio de producción de video: el agente lee manifiestos y skills, y lleva un brief en lenguaje natural hasta un corte renderizado.

## QUE_CONTIENE
- `pipeline_defs/`: 12 pipelines de producción (`animated-explainer`, `animation`, `avatar-spokesperson`, `character-animation`, `cinematic`, `clip-factory`, `documentary-montage`, `hybrid`, `localization-dub`, `podcast-repurpose`, `screen-demo`, `talking-head`) y el arnés `framework-smoke`.
- `skills/`: 157 markdown de directores de etapa, técnicas creativas, skills core y meta (`reviewer`, `checkpoint-protocol`, `onboarding`, `video-reference-analyst`).
- `.agents/skills/`: 578 markdown de conocimiento técnico vendorizado (HyperFrames, Remotion, FLUX, TTS, Three.js, GSAP, Manim y otros).
- `tools/`: más de 100 clases `BaseTool` en video, audio, graphics, enhancement, analysis, avatar, subtitle, character, capture y publishers; descubrimiento en `tools/tool_registry.py`.
- `schemas/`: JSON Schema de artefactos (`brief`, `research_brief`, `script`, `scene_plan`, `asset_manifest`, `edit_decisions`, `decision_log`, `cost_log`, `render_report`, `publish_log`), pipelines, playbooks y tools.
- `styles/`: playbooks `clean-professional`, `flat-motion-graphics`, `minimalist-diagram`, `anime-ghibli`, `premium-minimalist`.
- `remotion-composer/`: compositor React/Remotion (escenas, charts, captions, TalkingHead).
- `backlot/`: tablero local de la producción (`python -m backlot`).
- `ink-theater/`: motor SVG/GSAP de animación en tinta para el camino atelier de HyperFrames.
- `lib/`: config, checkpoints, loader de pipelines, perfiles de medio, scoring y costo.
- `tests/` y CI en `.github/workflows/ci.yml` (Python 3.11, FFmpeg, `make install-dev`).
- Operación: `AGENT_GUIDE.md`, `PROJECT_CONTEXT.md`, `docs/ARCHITECTURE.md`, `docs/PROVIDERS.md`, `PROMPT_GALLERY.md`. La guía larga en chino sigue en `README_zh-CN.md`.
- Paquete Python `openmontage` 0.1.0 (`setup.py`). Licencia GNU AGPLv3 (`LICENSE`).

## CARACTERISTICAS
- El agente de código es el orquestador: lee el manifiesto YAML y el director de etapa, llama herramientas y deja el estado en checkpoints. Python cubre herramientas y persistencia.
- Flujo base documentado: idea → script → scene_plan → assets → edit → compose → publish. Research y proposal entran en los pipelines que los declaran.
- Tres runtimes de composición, fijados como `render_runtime`: Remotion, HyperFrames y FFmpeg.
- Ruta local sin claves de pago: Piper TTS, metraje de Archive.org, NASA y Wikimedia, composición Remotion o HyperFrames, y FFmpeg. Pexels, Pixabay y Unsplash usan claves de desarrollador gratuitas.
- Proveedores de pago opcionales en `.env`: fal.ai, Atlas Cloud, Kling, Seedance, Veo, Runway, HeyGen, ElevenLabs, OpenAI, Google, Suno, xAI y otros listados en `docs/PROVIDERS.md`.
- Selector de proveedor con puntuación en 7 dimensiones y `decision_log` append-only.
- Presupuesto en `config.yaml`: modo `warn`, tope `total_usd` 10.00, reserva 10 %, aprobación por acción de pago desde 0.50 USD (`tools/cost_tracker.py`).
- Gates de aprobación humana, validación previa al compose y auto-revisión posterior al render (ffprobe, frames, audio, promesa de entrega).
- Arranque desde un video de referencia (YouTube, Short, Reel, TikTok o archivo local) con `skills/meta/video-reference-analyst.md`.
- Perfiles en `lib/media_profiles.py`: YouTube 1920×1080 y 4K, Shorts, Instagram Reels, feed 1080×1080, TikTok, LinkedIn, cinemático 2560×1080 y HD genérico.
- Instalación: Python 3.10+ (`.python-version`), FFmpeg, Node.js 18+, `make setup`.
- Contratos de asistente: Claude Code (`CLAUDE.md`), Cursor (`CURSOR.md`), Copilot (`COPILOT.md`), Codex (`CODEX.md`), Windsurf (`.windsurfrules`).

## FUERA_DE_ALCANCE
- La publicación de este repo empaqueta en local con `export_bundle` y un `publish_log`; la subida a plataformas queda fuera.
- Backlot lee `projects/` y muestra el tablero; no edita el corte.
- Las decisiones creativas, la revisión y la política de etapas viven en YAML y Markdown, no en un orquestador Python.
- El README de producto marca el LLM local (Ollama, LM Studio) como pendiente.
- `framework-smoke` es arnés de prueba, no un pipeline de entrega.

## RELACIONES
- Upstream: https://github.com/calesthio/OpenMontage
- Sitio: https://www.openmontage.video/
- Discusiones: https://github.com/calesthio/OpenMontage/discussions
- Issues: https://github.com/calesthio/OpenMontage/issues
- Canal: https://www.youtube.com/@OpenMontage
- Contrato del agente: `AGENT_GUIDE.md` y `PROJECT_CONTEXT.md`
- Motores: Remotion (`remotion-composer/`), HyperFrames (`npx hyperframes`), FFmpeg
- Asistentes: Claude Code, Cursor, Copilot, Codex, Windsurf

## ETIQUETAS
- produccion-video
- agente
- pipeline
- fork
- agpl-3.0
- python
- remotion
- hyperframes
- ffmpeg

## TOPICS_GITHUB
- agent
- agentic-ai
- ai
- claude
- copilot
- cursor
- elevenlabs
- ffmpeg
- flux
- hyperframes
- image-generation
- open-source
- openai
- python
- remotion
- stable-diffusion
- text-to-speech
- text-to-video
- video-generation
- video-production
