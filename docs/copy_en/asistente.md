# Copy EN · Ask with AI (`/[lang]/asistente/`)

> Traducción de `docs/copy_es/asistente.md` (08-11-2026). Mismas claves, en el mismo orden. Inglés británico
> (glosario `docs/03a_GLOSARIO_es-en.md`).

---

## Metadata

<!-- asistente.meta.titulo -->
Ask with AI

<!-- asistente.meta.descripcion -->
Query the debates and signatures of the Cortes from an AI assistant through an open connector: what to ask, how to install it and what it does not do.

## Side index

<!-- asistente.indice.pedir -->
What you can ask

<!-- asistente.indice.ejemplos -->
Sample questions

<!-- asistente.indice.instalar -->
Installing it

<!-- asistente.indice.limites -->
Worth knowing

<!-- asistente.indice.citar -->
Licence and citation

## Header

<!-- asistente.antetitulo -->
`luz-mcp` · open source · MIT licence

<!-- asistente.titulo -->
What if you asked an AI assistant?

<!-- asistente.entrada -->
An AI assistant such as Claude can query the dataset for you. Write the question in your own words: the assistant searches, counts and returns figures, passages and charts.

<!-- asistente.entrada.2 -->
It does so through an open connector, `luz-mcp`. MCP is the standard that assistants use to call external tools. It works with Claude, ChatGPT desktop, Cursor, Antigravity, OpenCode and others.

<!-- asistente.cabeza.rotulo -->
In Claude Code, one line

<!-- asistente.cabeza.codigo -->
```bash
claude mcp add luz -s user -- uvx luz-mcp
```

<!-- asistente.cabeza.accion -->
[See how to install it]

## 1 · What you can ask (`#pedir`)

<!-- asistente.pedir.titulo -->
What you can ask

<!-- asistente.pedir.entrada -->
The connector works with the two deposited datasets, Luz y Taquígrafos and Afinidades Elegidas, and links them: from a measure it jumps to the debate where it was defended.

<!-- asistente.pedir.discurso.titulo -->
About what was said

<!-- asistente.pedir.discurso -->
- How often a word or phrase is said, year by year, by legislature or by political family.
- Which words set two groups apart, with or without the Chair.
- How much each political family speaks compared with its seats.
- Passages in context, the whole intervention and the session it comes from.

<!-- asistente.pedir.red.titulo -->
About who signed with whom

<!-- asistente.pedir.red -->
- The jointly signed measures, who signed them and the debate where they were read.
- The co-sponsorship network of each legislature: who signs with whom and who bridges parties.
- How far each party, family or district keeps to itself.
- Whether the deputies who hold the network together speak differently on the floor.

<!-- asistente.pedir.llevar.titulo -->
To take away

<!-- asistente.pedir.llevar -->
- Networks of words, of people mentioned and of who names whom, over the debates you choose.
- The series ready for R or Python, its chart and the citation of each dataset with its DOI.
- A methods note with everything the assistant has run.

## 2 · Sample questions (`#ejemplos`)

<!-- asistente.ejemplos.titulo -->
Sample questions

<!-- asistente.ejemplos.entrada -->
Written as you would write them. Under each one, what the assistant does and the connector tool it uses.

<!-- asistente.ej1.pregunta -->
‘How does “agrarian reform” evolve against “public order” between 1931 and 1936?’

<!-- asistente.ej1.hace -->
It counts both phrases year by year, relative to everything that was said, and draws one line for each.

<!-- asistente.ej1.herramienta -->
`ngram_viewer`

<!-- asistente.ej2.pregunta -->
‘Which political families speak more than their seats would suggest in the Constituent Cortes?’

<!-- asistente.ej2.hace -->
It compares each family's share of the words with its share of the seats.

<!-- asistente.ej2.herramienta -->
`share_of_voice`

<!-- asistente.ej3.pregunta -->
‘Which words set the Socialists apart from the conservatives, leaving out the Chair?’

<!-- asistente.ej3.hace -->
It compares the vocabulary of both groups and leaves out the turns of whoever presides, which only give the floor.

<!-- asistente.ej3.herramienta -->
`distinctive_words`

<!-- asistente.ej4.pregunta -->
‘Find the amendments on agrarian matters defended on the floor and show me the debate.’

<!-- asistente.ej4.hace -->
It finds the measures by topic and opens each one with the session where it was read and defended.

<!-- asistente.ej4.herramienta -->
`search_measures` · `get_measure`

<!-- asistente.ej5.pregunta -->
‘Who bridges parties when signing measures, in each legislature?’

<!-- asistente.ej5.hace -->
It computes from the signatures the brokerage roles and the share of co-signatures that cross party lines.

<!-- asistente.ej5.herramienta -->
`brokerage_roles` · `transpartisan_cosigning`

<!-- asistente.ej6.pregunta -->
‘Do the deputies who hold the network together speak differently on the floor from those who stay within their party?’

<!-- asistente.ej6.hace -->
It gathers the speeches of each network role and compares their vocabulary.

<!-- asistente.ej6.herramienta -->
`speech_by_network` · `distinctive_words`

## 3 · Installing it (`#instalar`)

<!-- asistente.instalar.titulo -->
Installing it

<!-- asistente.instalar.entrada -->
You need `uv`, a free Python installer. There is no code to download: the connector is on PyPI.

<!-- asistente.instalar.claude.rotulo -->
Claude Code

<!-- asistente.instalar.claude -->
```bash
claude mcp add luz -s user -- uvx luz-mcp
```

<!-- asistente.instalar.codex.rotulo -->
ChatGPT desktop and Codex

<!-- asistente.instalar.codex -->
```bash
codex mcp add luz -- uvx luz-mcp
```

<!-- asistente.instalar.json.rotulo -->
Claude Desktop, Cursor, Antigravity, Gemini CLI and most others

<!-- asistente.instalar.json -->
```json
{
  "mcpServers": {
    "luz": { "command": "uvx", "args": ["luz-mcp"] }
  }
}
```

<!-- asistente.instalar.reiniciar -->
Restart the program after changing its configuration. If the connector does not start, replace `uvx` with the full path that `which uvx` returns.

<!-- asistente.instalar.web -->
ChatGPT on the web only accepts remote connectors, and this one runs on your computer: it does not work there.

<!-- asistente.instalar.datos -->
The first time, ask the assistant to download the data. They come from Harvard Dataverse, are checked file by file and are stored on your computer.

<!-- asistente.instalar.otros -->
The repository README has the configuration for each program, OpenCode included.

<!-- asistente.instalar.accion -->
[See the repository ↗] [See the package on PyPI ↗]

## 4 · Worth knowing (`#limites`)

<!-- asistente.limites.titulo -->
Worth knowing

<!-- asistente.limites.entrada -->
The connector knows the limits of both datasets and states them. These are the ones that most change an answer.

<!-- asistente.limites.lista -->
- **It counts and searches; it does not interpret.** Reading each result is up to whoever asks.
- **Not everything is speech.** Each session's summary, documents read out and votes are set aside to study what was said.
- **There is no sex variable** in either dataset: nothing can be broken down by sex.
- **Two sets of party labels.** To compare voice and seats, the connector uses those of the Afinidades register, which shares the list of deputies.
- **The network metrics are the published ones.** When it computes a measure from the signatures, it says so and explains how.
- **Some signature lists are truncated in the Diario**, and those measures lack some ties.

<!-- asistente.limites.privacidad -->
Your questions do not pass through us: the assistant you use processes them, under its own terms. The data are queried on your computer.

## 5 · Licence and citation (`#citar`)

<!-- asistente.citar.titulo -->
Licence and citation

<!-- asistente.citar.entrada -->
The code is open, under the MIT licence. If you use an answer in your work, cite each dataset with its DOI; the assistant gives you the citation with the `how_to_cite` tool.

<!-- asistente.citar.cierre -->
Every figure it returns can be checked against the Diario. Read the passage in the explorer, or download the dataset and repeat the count.
