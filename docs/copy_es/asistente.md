# Copy ES · Preguntar con IA (`/[lang]/asistente/`)

> **Estado (08-11-2026).** Página nueva, pedida por el investigador: el sitio no presentaba el conector MCP de la base.
> Sigue la página «Herramientas» de ParlaIbero (`parlaibero_site/src/pages/[lang]/herramientas.astro`, copy §9) y el
> LÉAME de `luz-tools` (`2REP/luz_tools/README.md`, paquete `luz-mcp` 0.5.0 en PyPI). Cada herramienta que se nombra
> existe en el servidor (`src/luz_mcp/server.py`).
>
> **Cómo se lee.** Formato de ParlaIbero: `<!-- clave -->` abre cada texto; `<!-- ↺ clave -->` repite una frase fija o
> un rótulo de `comun.md`; `> [nota de diseño]` no es texto para el lector.
>
> **Lo que no dice, y por qué.** Ninguna cifra del LÉAME (filas, sesiones, firmas, MB de la descarga): no salen del
> exportador. Los ejemplos dan la pregunta, lo que hace el asistente y la herramienta, sin resultados: un resultado
> sería una cifra sin base. No habla de ediciones (principio 7), así que omite la advertencia del LÉAME sobre los
> números de fila de las bibliotecas. Dataverse ya no pide formulario (08-11-2026), y por eso el conector descarga por su API. Las preguntas no pasan por el proyecto, pero sí por el proveedor del
> asistente: el copy dice lo primero y no afirma que «no salen de su equipo».

---

## Metadatos

<!-- asistente.meta.titulo -->
Preguntar con IA

<!-- asistente.meta.descripcion -->
Consulte los debates y las firmas de las Cortes desde un asistente de IA, con un conector abierto: qué pedirle, cómo instalarlo y qué no hace.

## Índice lateral

<!-- asistente.indice.pedir -->
Lo que puede pedirle

<!-- asistente.indice.ejemplos -->
Preguntas de ejemplo

<!-- asistente.indice.instalar -->
Instalarlo

<!-- asistente.indice.limites -->
Lo que conviene saber

<!-- asistente.indice.citar -->
Licencia y cita

## Cabecera

<!-- asistente.antetitulo -->
`luz-mcp` · código abierto · licencia MIT

<!-- asistente.titulo -->
¿Y si se lo pregunta a un asistente de IA?

<!-- asistente.entrada -->
Un asistente de IA, como Claude, puede consultar la base por usted. Escriba la pregunta con sus palabras: el asistente busca, cuenta y le devuelve cifras, pasajes y gráficos.

<!-- asistente.entrada.2 -->
Lo hace con un conector abierto, `luz-mcp`. MCP es el estándar con el que los asistentes usan herramientas externas. Funciona con Claude, ChatGPT de escritorio, Cursor, Antigravity, OpenCode y otros.

> [nota de diseño] Cabecera a dos columnas: al margen, el bloque de instalación en una línea (`asistente.cabeza.*`) con
> [Ver cómo instalarlo] → `#instalar`.

<!-- asistente.cabeza.rotulo -->
En Claude Code, una línea

<!-- asistente.cabeza.codigo -->
```bash
claude mcp add luz -s user -- uvx luz-mcp
```

<!-- asistente.cabeza.accion -->
[Ver cómo instalarlo]

## 1 · Lo que puede pedirle (`#pedir`)

<!-- asistente.pedir.titulo -->
Lo que puede pedirle

<!-- asistente.pedir.entrada -->
El conector trabaja con las dos bases depositadas, Luz y Taquígrafos y Afinidades Elegidas, y las cruza: de una iniciativa salta al debate en que se defendió.

<!-- asistente.pedir.discurso.titulo -->
Sobre lo que se dijo

<!-- asistente.pedir.discurso -->
- Cuántas veces se dice una palabra o una frase, año a año, por legislatura o por familia política.
- Qué palabras distinguen a dos grupos, con la Presidencia o sin ella.
- Cuánto habla cada familia política frente a sus escaños.
- Los pasajes en su contexto, la intervención entera y la sesión de la que sale.

<!-- asistente.pedir.red.titulo -->
Sobre quién firmó con quién

<!-- asistente.pedir.red -->
- Las iniciativas firmadas en común, quién las firmó y el debate en que se leyeron.
- La red de coautorías de cada legislatura: quién firma con quién y quién hace de puente entre partidos.
- Cuánto se cierra cada partido, familia o distrito sobre sí mismo.
- Si los diputados que articulan la red hablan distinto en el pleno.

<!-- asistente.pedir.llevar.titulo -->
Para llevárselo

<!-- asistente.pedir.llevar -->
- Redes de palabras, de personas mencionadas y de quién nombra a quién, sobre los debates que usted elija.
- La serie lista para R o Python, su gráfico y la cita de cada conjunto con su DOI.
- Una nota de métodos con todo lo que el asistente ha ejecutado.

## 2 · Preguntas de ejemplo (`#ejemplos`)

<!-- asistente.ejemplos.titulo -->
Preguntas de ejemplo

<!-- asistente.ejemplos.entrada -->
Escritas como las escribiría usted. Debajo de cada una, lo que hace el asistente y la herramienta del conector que usa.

<!-- asistente.ej1.pregunta -->
«¿Cómo evoluciona “reforma agraria” frente a “orden público” entre 1931 y 1936?»

<!-- asistente.ej1.hace -->
Cuenta las dos expresiones año a año, en proporción a todo lo que se dijo, y dibuja una línea para cada una.

<!-- asistente.ej1.herramienta -->
`ngram_viewer`

<!-- asistente.ej2.pregunta -->
«¿Qué familias políticas hablan más de lo que les corresponde por escaños en las Constituyentes?»

<!-- asistente.ej2.hace -->
Compara la parte de las palabras que dice cada familia con su parte de los escaños.

<!-- asistente.ej2.herramienta -->
`share_of_voice`

<!-- asistente.ej3.pregunta -->
«¿Qué palabras distinguen a los socialistas de los conservadores, sin la Presidencia?»

<!-- asistente.ej3.hace -->
Compara el vocabulario de los dos grupos y deja fuera los turnos de quien preside, que darían la palabra y nada más.

<!-- asistente.ej3.herramienta -->
`distinctive_words`

<!-- asistente.ej4.pregunta -->
«Busca las enmiendas de tema agrario defendidas en el pleno y enséñame el debate.»

<!-- asistente.ej4.hace -->
Encuentra las iniciativas por su tema y abre cada una con la sesión en que se leyó y se defendió.

<!-- asistente.ej4.herramienta -->
`search_measures` · `get_measure`

<!-- asistente.ej5.pregunta -->
«¿Quién hace de puente entre partidos al firmar iniciativas, en cada legislatura?»

<!-- asistente.ej5.hace -->
Calcula desde las firmas los papeles de intermediario y la parte de las cofirmas que cruza de partido.

<!-- asistente.ej5.herramienta -->
`brokerage_roles` · `transpartisan_cosigning`

<!-- asistente.ej6.pregunta -->
«¿Hablan distinto en el pleno los diputados que articulan la red y los que se quedan en su partido?»

<!-- asistente.ej6.hace -->
Reúne los discursos de cada papel en la red y compara su vocabulario.

<!-- asistente.ej6.herramienta -->
`speech_by_network` · `distinctive_words`

## 3 · Instalarlo (`#instalar`)

<!-- asistente.instalar.titulo -->
Instalarlo

<!-- asistente.instalar.entrada -->
Necesita `uv`, un instalador gratuito de Python. No hace falta descargar el código: el conector está en PyPI.

<!-- asistente.instalar.claude.rotulo -->
Claude Code

<!-- asistente.instalar.claude -->
```bash
claude mcp add luz -s user -- uvx luz-mcp
```

<!-- asistente.instalar.codex.rotulo -->
ChatGPT de escritorio y Codex

<!-- asistente.instalar.codex -->
```bash
codex mcp add luz -- uvx luz-mcp
```

<!-- asistente.instalar.json.rotulo -->
Claude Desktop, Cursor, Antigravity, Gemini CLI y la mayoría de los demás

<!-- asistente.instalar.json -->
```json
{
  "mcpServers": {
    "luz": { "command": "uvx", "args": ["luz-mcp"] }
  }
}
```

<!-- asistente.instalar.reiniciar -->
Reinicie el programa después de cambiar su configuración. Si el conector no arranca, cambie `uvx` por la ruta completa que da `which uvx`.

<!-- asistente.instalar.web -->
ChatGPT en la web solo admite conectores remotos, y este se ejecuta en su equipo: allí no funciona.

<!-- asistente.instalar.datos -->
La primera vez, pida al asistente que descargue los datos. Vienen de Harvard Dataverse, se comprueban archivo a archivo y se guardan en su equipo.

<!-- asistente.instalar.otros -->
El LÉAME del repositorio trae la configuración de cada programa, OpenCode incluido.

<!-- asistente.instalar.accion -->
[Ver el repositorio ↗] [Ver el paquete en PyPI ↗]

## 4 · Lo que conviene saber (`#limites`)

<!-- asistente.limites.titulo -->
Lo que conviene saber

<!-- asistente.limites.entrada -->
El conector conoce los límites de las dos bases y los dice. Estos son los que más cambian una respuesta.

<!-- asistente.limites.lista -->
- **Cuenta y busca; no interpreta.** La lectura de cada resultado es de quien pregunta.
- **No todo es discurso.** El sumario de cada sesión, los documentos leídos y las votaciones se apartan para estudiar lo que se dijo.
- **No hay variable de sexo** en ninguna de las dos bases: nada se puede desglosar por sexo.
- **Dos juegos de etiquetas de partido.** Para comparar voz y escaños, el conector usa las del registro de Afinidades, que comparte la lista de diputados.
- **Las métricas de red son las publicadas.** Cuando calcula una medida desde las firmas, lo dice y explica cómo.
- **Algunas listas de firmas están truncadas en el Diario**, y a esas iniciativas les faltan vínculos.

<!-- asistente.limites.privacidad -->
Sus preguntas no pasan por nosotros: las procesa el asistente que usted use, con sus condiciones. Los datos se consultan en su equipo.

## 5 · Licencia y cita (`#citar`)

<!-- asistente.citar.titulo -->
Licencia y cita

<!-- asistente.citar.entrada -->
El código es abierto, con licencia MIT. Si usa una respuesta en un trabajo, cite cada base con su DOI; el asistente le da la cita con la herramienta `how_to_cite`.

<!-- asistente.citar.cierre -->
Cada cifra que le devuelva se puede comprobar contra el Diario. Lea el pasaje en el explorador o descargue la base y repita la cuenta.

> [nota de diseño] La página termina en el Diario, el explorador o el depósito (principio 1): tras el cierre,
> [Abrir el explorador ↗] y [Descargar los datos] (rótulos únicos de `comun.md` § 3).
