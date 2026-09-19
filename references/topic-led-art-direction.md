# Topic-led art direction

Read for every campaign before choosing scenes or writing image prompts. The goal is a distinctive, topic-relevant visual world with coherence and restraint. Do not reproduce a previous campaign's appearance for unrelated brands. Originality is a design objective, not a guarantee of global uniqueness or legal clearance.

## Derive rather than decorate

Extract from the user's current brief:
- What the product, service or subject actually is, and what facts are supported.
- Who it addresses and what this audience should feel or understand.
- Specific visual properties: material, process, form, environment, use ritual, movement, light transmission, texture or other relevant qualities.
- Supplied brand constraints and references. Keep proposed choices distinct from existing brand facts.

Develop a few genuinely different art-direction candidates briefly in the working notes. Different candidates should change the visual idea, materials, light and photographic grammar, not merely colors. Choose the strongest topic-specific direction unless the user asks to compare options. Do not introduce a routine approval gate when creation has already been authorized.

Write a concise chosen-direction brief covering:
1. A central visual idea that belongs to this subject.
2. A restrained palette with a reason for each color.
3. A small set of compatible materials/environments.
4. Lighting, contrast and color-treatment logic.
5. Product/brand invariants that must remain consistent.
6. A varied vocabulary of scenes, crops, scales and viewpoints.
7. Copy density and typography appropriate to the actual campaign.

For services or abstract topics, derive imagery from their real process, tools, setting or a clearly conceptual metaphor. Never fabricate clients, results, products or proof to make the feed look convincing.

## Constrain identity, allow composition

For combined previews, fix a shared visual world and request distinct crops/scales without assigning every scene to a numbered cell. Preserve compositional freedom: give the model a strong set of relevant scene possibilities, require exactly twelve distinct related tiles, and let it compose their arrangement. Use a fixed storyboard only when the user's narrative or exact content order requires it.

Mix subject views, material details, use/process scenes and quiet space as appropriate. Do not prescribe the same numerical mix or tile positions for every brand. Strong images need not all contain copy or a logo. Commercial conversion campaigns may need more copy than an editorial identity preview.

Avoid default luxury shorthand: beige/black/gold, marble, linen, fruit, serif type, cinematic shadows and sculptural bottles are not universal premium ingredients. Use them only when the chosen direction justifies them. Likewise avoid default problem/solution/proof/CTA copy on every editorial tile.

Before generation ask: if the logo disappeared, would the imagery still belong to this topic? Could this brief be reused for an unrelated brand by replacing only the name? If yes, make the visual idea more specific.

When previous work is available in the current task, compare it with the proposed direction and avoid accidental reuse of its scene sequence, props and visual metaphor. Do not search unrelated private client work or claim to have checked all past generations. If the user wants a consistent ongoing series, preserve its identity while varying scenes.

## Combined editorial preview

Use when the user asks for one 12-tile preview or concept feed rather than separate production posts.

1. Generate one text-free 3-column × 4-row composite with the built-in image tool. Set overall and tile proportions intentionally. Request consistent gutters, coherent identity, varied scenes, blank package labels and quiet areas for later typography. Do not pass unrelated brand images as references.
2. Inspect the actual output: twelve cells, visual rhythm, relevance, distinct scenes, credible anatomy/materials, product consistency and usable typography space. Repair specific defects; do not accept an image merely because the tool succeeded.
3. Overlay exact copy and supplied/proposed logo deterministically using an available renderer. The existing production renderer is not assumed to accept composite images; a task-local overlay script is appropriate. Keep the raw image and editable overlay source.
4. Place text based on actual image bounds and contrast, not inherited coordinates. Inspect Turkish glyphs and package-label fit at enlarged scale. Account for label perspective; avoid visibly pasted-on branding.
5. Deliver the requested preview with honest dimensions and QA status. A composite with small cells is not twelve full-resolution production posts. If those are requested later, generate production assets using the accepted visual world.

Prompt scaffold, adapted to the chosen topic:

“Create one [overall aspect ratio] campaign preview with exactly twelve [tile proportions] panels in three columns and four rows. [Actual subject and audience]. Shared visual world: [central idea, palette, materials/environment]. [Product/brand invariants]. Include distinct but related scenes such as [topic-specific scene vocabulary], varying crops, scale and viewpoint. [Light and treatment]. Compose a coherent rhythm with [appropriate gutters] and quiet areas for later typography. Blank package labels where applicable. No text, letters, numbers, logos, watermarks, signatures or interface. Avoid [direction-specific clichés and defects].”

This is a compositional framework, not a reusable aesthetic prompt. Do not merely substitute nouns in a previous campaign prompt.

## Production delivery

For twelve separate posts, use this same topic-led art direction and then follow the existing production manifest, anchor and rendering contracts. Do not silently change script schemas. Read [content-architecture.md](content-architecture.md) for required fields. Separate production files should retain campaign coherence; a different crop alone is not enough variety across all twelve.

## Save the recipe and report honestly

Keep the current brief, chosen art direction, exact generation prompt, selected output, overlay source and material corrections in the task workspace. This supports later reuse and investigation without inventing the process after the fact.

Report technical rendering and visual inspection separately. Do not claim commercial performance, uniqueness across the internet, specific model versions not exposed by the tool, or future output quality from a single attractive example.
