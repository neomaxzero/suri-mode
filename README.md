# Suri Mode

Una skill para Codex que organiza trabajo técnico no trivial en cambios pequeños, verificables y ajustados al contexto.

## Qué hace

- Elige un flujo para investigación, bugs, features o refactors.
- Pide decisiones humanas cuando cambian producto, arquitectura o alcance.
- Usa especialistas solo cuando aportan valor real.
- Verifica resultados desde la experiencia del usuario.
- Incluye un `sleep mode` local que se activa únicamente de forma explícita.

## Instalación

```bash
git clone https://github.com/neomaxzero/suri-mode.git ~/.codex/skills/suri-mode
```

Reinicia Codex después de instalarla.

## Uso

La skill puede activarse automáticamente en tareas técnicas complejas. También puedes invocarla directamente:

```text
$suri-mode investigá este bug y proponé el cambio más pequeño que lo resuelva
```

`sleep mode` requiere esa frase exacta y una entrevista previa antes de modificar código.

## Estructura

```text
suri-mode/
├── SKILL.md
├── agents/openai.yaml
└── references/
    ├── day-workflows.md
    ├── decision-review.md
    ├── sleep-mode.md
    └── verification.md
```

## Licencia

MIT
