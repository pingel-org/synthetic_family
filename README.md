# Family History Demo Dataset

## Running with Semiont

Explore this dataset using [Semiont](https://github.com/The-AI-Alliance/semiont), an open-source knowledge base platform for annotation and knowledge extraction.

### Backend

### Prerequisites

- **Container runtime** — [Apple Container](https://github.com/apple/container), [Docker](https://www.docker.com/), or [Podman](https://podman.io/)
- **Inference provider** — an `ANTHROPIC_API_KEY` (cloud) or [Ollama](https://ollama.com/) running locally
- **Neo4j** — a free cloud instance at [Neo4j Aura](https://neo4j.com/cloud/aura/) or Neo4j running locally

Set these environment variables before running:

```bash
export NEO4J_URI=<your-neo4j-uri>
export NEO4J_USERNAME=<your-neo4j-username>
export NEO4J_PASSWORD=<your-neo4j-password>
export NEO4J_DATABASE=<your-neo4j-database>
export ANTHROPIC_API_KEY=<your-api-key>
```

### Backend

```bash
.semiont/scripts/local_backend.sh
```

Starts PostgreSQL and the Semiont backend in containers. The script stays attached and streams logs — open a separate terminal for the frontend. Press Ctrl+C to stop.

To run in the background instead: `.semiont/scripts/local_backend.sh &`

Open **http://localhost:4000** to verify.

### Frontend

In a separate terminal:

```bash
.semiont/scripts/local_frontend.sh
```

Same as the backend — stays attached and streams logs. Press Ctrl+C to stop.

Open **http://localhost:3000**.

### Logging in

Enter **http://localhost:4000** as the knowledge base URL. Log in with the username and password created during backend setup.

### Using Semiont

Semiont organizes work around seven composable flows. The ones most relevant to this dataset:

- **Mark** — Annotate documents by selecting text manually or using AI-assisted detection (the ✨ button). Annotations follow the [W3C Web Annotation](https://github.com/The-AI-Alliance/semiont/blob/main/specs/docs/W3C-WEB-ANNOTATION.md) standard and can be highlights, comments, tags, or entity references.
- **Bind** — Resolve entity references by linking annotations to other resources in the knowledge graph. The resolution wizard (🕸️🧙) searches for matching candidates and scores them.
- **Yield** — Generate new resources from annotations. AI agents can produce summaries or new content from annotated passages.
- **Match** — Search the knowledge base for candidates during entity resolution. Uses composite scoring across name similarity, entity type, graph connectivity, and optional LLM re-ranking.
- **Gather** — Assemble surrounding context (text, metadata, graph neighborhood) to improve detection, resolution, and generation quality.

A typical workflow: upload documents → detect entities with AI → resolve references to build the knowledge graph → generate summaries or new resources from what you've found.

For deeper understanding, see the [architecture overview](https://github.com/The-AI-Alliance/semiont/blob/main/docs/ARCHITECTURE.md), the [project layout](https://github.com/The-AI-Alliance/semiont/blob/main/docs/PROJECT-LAYOUT.md), and the individual [flow docs](https://github.com/The-AI-Alliance/semiont/tree/main/docs/flows). The [API reference](https://github.com/The-AI-Alliance/semiont/blob/main/specs/docs/API.md) covers all HTTP endpoints.

Other example knowledge bases: [gutenberg-kb](https://github.com/The-AI-Alliance/gutenberg-kb) (public domain literature) and [semiont-workflows](https://github.com/The-AI-Alliance/semiont-workflows) (end-to-end pipeline).

---

## About This Dataset

This directory contains **synthetic family history documents** created for demonstration purposes. All names, dates, locations, and events are fictional, though they are designed to be historically plausible and representative of typical American family histories from the mid-19th to early 20th centuries.

## Purpose

These materials are crafted to:
- Be relatable to general audiences interested in genealogy and family history
- Demonstrate the annotation and knowledge extraction capabilities of Semiont
- Provide realistic examples of biographical narratives and historical documentation
- Show how family relationships, timelines, and historical contexts can be annotated and linked

## Contents

The synthetic documents include:
- **Biographical narratives** - Life stories of fictional Turner family members
- **Historical photographs** - Representative images that could appear in family collections
- **Timeline entries** - Key life events presented in chronological format

## Historical Context

While the Turner family is entirely fictional, their stories reflect real historical experiences:
- Civil War service and its impact on families
- Westward expansion and homesteading under the Homestead Act
- Agricultural challenges like the 1870s locust plagues
- The transition from agricultural to industrial economies
- Small-town American life in the late 1800s and early 1900s

## Usage

These materials are ideal for:
- Testing entity recognition (people, places, dates, events)
- Exploring relationship mapping between family members
- Demonstrating temporal annotation and timeline construction
- Showing how historical context can enrich family narratives
- Training annotation models on genealogical content

## Note on Authenticity

While these documents aim for historical plausibility, they should not be used as actual historical references. They are educational tools designed to demonstrate information extraction and annotation techniques on familiar, accessible content that many people can relate to through their own family histories.
