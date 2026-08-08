# autoshare-078

Prompt repository for the n8n content automation pipeline
("Insight Brain -> Writer -> Judge -> Image Engine -> Facebook").

## Structure

- `/prompts/` — one `.md` file per agent per version. Never edit a file in place; add a new version file instead.
- `/config/active_versions.json` — single source of truth for which prompt version is currently live per agent. The n8n workflow fetches this file first, then fetches the specific versioned prompt file it points to.
- `/brand.json` — shared brand bible (tone, word count, hashtag rules, quality gate thresholds). Every agent prompt is combined with this at runtime.

## Versioning rule

1. Never overwrite an existing `*_vN.md` file.
2. To change a prompt, create `*_vN+1.md`.
3. Update `config/active_versions.json` to point to the new file.
4. Old versions remain in the repo for rollback/audit — this is what makes prompt changes safe to test without breaking a production run mid-flight.
