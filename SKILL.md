---
name: ascii-type-poster
description: Create spacious Swiss-inspired ASCII and halftone posters from an uploaded image, a described subject, or exact supplied text. Use when Codex must choose a generative image transform, an explicitly pixel-safe transform, or a type-led composition while preserving source authority, exact typography, sparse composition, and auditable prompt/recipe consistency.
---

# ASCII Halftone Poster

Create one minimal raster poster from one primary authority: an uploaded image, a generated pictorial subject, or supplied text. Return the final poster when rendered, the exact final prompt, and a recipe that records only what was requested and completed.

## Mode and source authority

Select exactly one mode and keep its authority throughout:

1. Select `Image Transform` when the user supplies an image. Treat that image as the sole pictorial source; extra text may direct treatment, layout, and type but may not replace, reinterpret, or supplement it with a new primary subject.
2. Select `Subject Generate` without an image when the user describes a pictorial subject.
3. Select `Type-led` without an image when supplied text is intended to be the visual object.

Ask one concise question only when the image role, mode, exact required text, or another material interpretation is genuinely ambiguous. Preserve title, metadata, and user copy verbatim: never translate, rewrite, complete, or invent them unless authorized.

## Material Contracts (blocking)

Lock the mode-appropriate contract immediately after primary authority and before the composition thesis. `Image Transform` and `Subject Generate` use the Pictorial Material Contract; `Type-led` uses both the Type Material Contract and the shared mark prohibitions.

### Pictorial Material Contract

- For `Image Transform` and `Subject Generate`, the primary pictorial subject **must by default be reconstructed exclusively** from discrete, solid, individually distinguishable circular dots. Mark-only does not mean every internal region is filled: purposeful mark-free/open zones are allowed when they clarify the form.
- Express source colors only through mark fill/background, and source identity only through silhouette, pose, key landmarks, and requested details. Preserve primary color relationships; omit secondary texture and background noise unless requested.
- Forbid `continuous photo pixels/underlay`, `smooth painted/tonal regions` or `continuous gradients`, `fine stippling`, `print texture overlay`, `engraving`, `crosshatching`, any unrequested mark family, and `random-symbol mosaic`. If the original or any continuous layer is visible beneath the marks, fail.
- Use one coherent base screen/pitch/angle per subject or major mass. Let radius or occupancy carry tone at roughly fixed pitch; allow only a few gentle macro bends or phase changes. Do not build separate screens for every edge, joint, fold, grain, or background speck, and do not use unstructured random scatter.
- Verify separated circular dots at normal poster size. At thumbnail, check silhouette, key landmarks, and halftone reading—not every dot. A rigid global grid, perfectly straight rows through meaningful contours, or uniform spacing/diameter across unrelated regions is forbidden unless the user explicitly requests a mechanical grid. Only an explicit user request may replace circles with another discrete mark family; adapt the geometry-specific clauses while keeping exclusive reconstruction and no continuous underlay.
- A generative restyle may use an available discrete-dot post-process/renderer, but it is optional; if the capability cannot satisfy this contract, do not deliver an image.

### Type Material Contract

- `Type-led` has no pictorial subject, but it is not exempt from material enforcement. The supplied title itself must be visibly constructed from the selected ASCII/halftone marks across the primary letterforms; default to solid filled circular dots unless another discrete mark family is explicitly requested.
- A conventional solid/vector glyph, solid glyph with dots merely overlaid or placed behind it, or a mark field limited to the background/outline while glyph interiors remain continuous fails. The font skeleton may guide contours, counters, and reading order, but the final primary letterform surface must be mark-based and the selected creative engine must operate on that mark field.
- Preserve exact glyph identity, counters, strokes, and order through mark density, spacing, flow, fragmentation, or controlled fade. Supporting copy remains ordinary, clear text and is not subject to this title-material requirement.

## Normalized Poster Spec

Create one `Normalized Poster Spec` before composing. Treat it as the single record from which prompt, render, and recipe are derived; do not maintain conflicting versions. Record at least:

```yaml
mode: Image Transform | Subject Generate | Type-led
primary_authority: uploaded_image | generated_subject | supplied_text
visual_material_contract: pictorial contract for Image Transform/Subject Generate or shared mark prohibitions for Type-led; default discrete solid circular dots or one explicitly requested alternative mark family; mark-only with purposeful open zones; source colors via mark fill/background; identity via silhouette/pose/key landmarks/requested details; coherent base rhythm; normal-size mark evidence and thumbnail silhouette/halftone evidence
type_material_contract: for Type-led, primary title letterforms are mark-constructed; no solid/vector glyph or dots merely overlaid/behind; font skeleton guides contours/counters/order; selected engine operates on the mark field; supporting copy stays clear
source: identifier, dimensions, hash when strict
execution_path: Generative Restyle | Pixel-safe / Strict Raster Transform
subject_and_preserved_details: silhouette, pose, key identity landmarks, requested details, primary color relationships; secondary texture/background noise omitted by default
title: exact verbatim text
title_relation: counterweight | continuation | interruption | containment | bridge | depth | structural_echo
title_layer: foreground, above image
title_image_ratio_target: 0.4-0.6 calibration for visual-subject modes
title_transition: none | specified region, mark family, axis, anchor rule
font_personality: width, weight, contour, rhythm, terminals, script coverage, rationale
creative_engine: one Type-led engine or none
supporting_copy: required | allowed | forbidden; exact text, provenance, line count
canvas_and_quiet_space: ratio chosen for thesis; external quiet target about 55%-65%
background: edge_evidence -> inferred canvas; negative-space areas
color_roles: role, color, and authority for each color
halftone: mark system, size/occupancy, coherent base pitch/angle, limited macro flow, purposeful open zones, background polarity
mass_profile: optical ledger covering shape/area+contour/crop, luminance/contrast, saturation/temperature, dot radius/density/spacing/flow, typography width/weight/line count/script complexity/axis, semantic salience (face/eyes/text), edge leverage, direction vectors, negative-space shape
overlap_profile: region, depth, direction, title block axis, edge pressure, and critical details kept clear
qg_evidence: actual visual observations for blocking Material Gate and Balance Gate; executed/pass/failure evidence and retry outcome
constraints: task-relevant prohibitions
```

If a field is unknown, resolve it from the user or mark it unresolved; do not silently fill it. Copy the same values into the prompt, render decisions, and recipe. A mismatch between spec, prompt, recipe, or output is a failure.

## Execution Path

Choose the path immediately after mode selection and state it in the recipe.

### Image Transform

- Select **Generative Restyle** by default. Use ImageGen or another generative image capability, declare that redraw is allowed, preserve semantic identity, major composition, perspective, pose, and requested details **within mark-only reconstruction** as faithfully as the capability permits, and never claim exact pixels. Use an available discrete-mark post-process/renderer when useful, but never assume it is available or required.
- Select **Pixel-safe / Strict Raster Transform** only when the user explicitly requires `exact pixels`, `no redraw`, or equivalent pixel preservation. Use deterministic extraction, crop, contrast, color, and circular-dot halftone operations on the supplied raster; the renderer must still satisfy the Pictorial Material Contract. A script is optional, not required. Record source identifier/path, dimensions, and SHA-256 (or available content hash), embed the complete source or use only a user-approved crop, and do not invoke ImageGen or any generative redraw.
- If the strict capability, complete source, approved crop, or deterministic renderer is unavailable, state plainly that the strict transform cannot be completed. Stop with prompt, recipe, and recommended specifications; never silently fall back to generative restyle.

### Subject Generate and Type-led

Use generative capability by default. For `Type-led`, preserve supplied text as the primary visual and add no pictorial subject. If the required capability is unavailable, return a prompt and recipe without claiming a rendered image.

## Creative decision and composition thesis

Write one composition-thesis sentence before using any percentage. State the anchor and why it dominates, the primary/secondary scale hierarchy, direction or action, the viewing path (`eye first lands on anchor → what carries it away and brings it back`), the quiet-space shape, edge pressure, and the asymmetric counterweight that makes the cluster intentional. Use optical judgment, not a pure mathematical centroid.

Record a concise optical mass ledger in `mass_profile`: shape/area plus contour and crop; luminance/contrast; saturation/temperature; dot radius/density/spacing/flow; typography width/weight/line count/script complexity/axis; semantic salience (face, eyes, text); edge leverage; direction vectors; and negative-space shape. Before rendering, run a balance pass with only a few gray blocks/dot fields to estimate anchor, title, point-field, and quiet-shape weights. Define `overlap_profile` (region, depth, direction, and title-block axis), then confirm at thumbnail, squint, and grayscale that the first focus and eye path hold.

For `Image Transform` and `Subject Generate`:

- Put the title in the foreground layer, above the image, and make it physically cross into the image/halftone outer edge. Do not leave it only below, beside, or behind the image. Overlap the outer mark field, not identity-defining eyes, facial features, anatomy, logos, or other critical source details.
- Calibrate title visual mass relative to image around `0.4–0.6`; use this only as a check after the thesis, never as a template or guarantee of balance. Keep the title/image relationship active rather than arranging two independent blocks.
- Keep roughly `55%–65%` of the *external canvas* visually quiet around the cluster; this is calibration, not a guarantee. Record the quiet-space shape. Black or dark areas that carry no marks count as negative space; internal holes, counters, and subject voids do not.

For `Type-led`, let exact text occupy a thesis-appropriate share of the canvas while retaining substantial surrounding quiet. Do not prescribe a fixed `3:4`, middle-lower, two-line uppercase, cyan, or right-edge-fade treatment; choose ratio, lineation, axis, and color from the spec.

Use a single coherent image–type cluster. Vary scale, position, orientation, stage, crop, or directional movement when the subject calls for it; do not make equal-weight duplicate icons. Keep quiet space around the cluster rather than as a dead gap between image and title. Do not add frames, panels, mockups, paper edges, paper texture, or decorative color blocks.

## Typography and image–type fusion

Choose the font from the theme's material, action, contour, title semantics, and composition direction. Select and state a personality such as grotesk, geometric, condensed, humanist, blunt display, or another justified family. In the recipe explain its **width, weight, contour, rhythm, terminals, and script coverage**, plus why those traits serve the subject and thesis. If replacing it with a generic neutral sans would preserve the same theme, relationship, and motion, the typography decision fails; choose again.

Support every supplied glyph, including CJK and other Unicode scripts. Inspect for tofu, missing glyphs, incorrect CJK forms, garbling, clipped strokes, substitutions, and reading-order errors. Treat exact title identity, punctuation, metadata, and glyph order as hard requirements.

Choose one explicit image–type relationship: `counterweight`, `continuation`, `interruption`, `containment`, `bridge`, `depth`, or `structural echo`. Align to visual mass and directional tension rather than a default side. For `Image Transform` and `Subject Generate`, keep title text clean and solid by default, then apply the local transition below only when it strengthens the selected relationship. For `Type-led`, apply the Type Material Contract to the whole primary title and never render a conventional solid/vector title.

### Selective title raster transition

- Keep the title always above the image. For `Image Transform` and `Subject Generate`, 80%–90% of the total title ink area remains continuous solid glyphs; only 10%–20% of the total title ink area, measured as `transition ink area ÷ total title ink area`, may be rasterized into the same halftone/ASCII marks in a specified interaction/overlap region. Do not rasterize the whole title unless the user explicitly requests it. Only the specified local region may receive the image's point field.
- In that region, convert local title marks to the **same** halftone/ASCII mark family as the image. Let mark size, spacing, and density gradually fade along an axis chosen by the composition (diagonal, radial, contour-following, or another justified axis), never a fixed right or bottom axis.
- Preserve at least one solid or otherwise legible glyph anchor per word unless the recorded text treatment explicitly permits a more abstract wordform. Keep the exact text identity even when local display legibility becomes expressive or faded.
- Prohibit blur, opacity haze, glow, soft-focus wash, and any transition that reads as mist. Do not let image marks enter title glyphs outside the specified transition region.

## Type-led creative engines

For every `Type-led` recipe, select exactly one main engine from the following according to the text's semantics, and explain that choice. The engine operates on a mark-constructed title, not on a solid/vector glyph; it changes mark density, flow, spacing, fragmentation, or counters while preserving exact glyph structure. Keep the supplied words primary and add no pictorial subject:

- `weave/interlock` — cross letter stems or counters as semantic linkage;
- `compression` — tighten width/spacing to enact pressure, density, or urgency;
- `erosion/fade` — remove marks along a meaningful semantic loss or decay axis;
- `echo/repetition` — repeat controlled offsets to enact memory, sound, or recurrence;
- `flow` — bend baseline, rhythm, or mark direction to enact motion;
- `fragment/reassemble` — separate and reconnect exact glyph fragments around a readable path;
- `counterfield/void` — let counters and negative space carry the semantic force;
- `modular stack` — stack exact glyph modules to enact system, hierarchy, or accumulation;
- `semantic gesture` — make one justified stroke, tilt, cut, or rhythm enact the verb or idea.

Do not let an engine collapse into unrelated random texture or a conventional title over a texture.

## Supporting copy states

Classify supporting dates, names, locations, captions, and footer copy as exactly one state in the spec and recipe:

- `required`: render the user-supplied copy verbatim, with no correction or translation;
- `allowed`: render at most one or two supporting lines, and record whether each is `user-provided` or `authorized-generated`; do not generate without that authorization;
- `forbidden`: omit it and do not invent filler, CTA, branding, logo, watermark, or tool signature.

Keep supporting copy clear, complete, and correctly ordered. Never apply ASCII/halftone fade, blur, haze, glow, or expressive illegibility to support text.

## ASCII / halftone material

For `Image Transform` and `Subject Generate`, default to `solid filled circular halftone`: every subject mark must be a discrete, solid, individually distinguishable circular dot. Use square-dot halftone, line screen, character ASCII, hollow/ring marks, or another mark family only when the user explicitly requests it; then use that one family exclusively and adapt the material checks without permitting a continuous image underneath. Never substitute fine stippling, engraving, crosshatching, print texture, smooth tone, or random symbols for the selected system. For `Type-led`, the title letterforms themselves must be reconstructed from the selected marks; it has no pictorial subject, but it still runs the Type Material Gate.

Use one coherent base screen/pitch/angle per subject or major mass, changing it gently only in a few macro zones. Keep a small set of size bands; at roughly fixed pitch, let one primary variable—dot radius or occupancy—carry tone. Local flow may follow large contour, pose, or action, but never give every edge, joint, fold, grain, or background speck its own field. Mark-only allows purposeful open zones and does not mean every region is filled. On a dark background, shadows are open/sparser and marks carry highlights; on a light background, highlights are open and dots carry shadows. Never make shadows both larger and denser by default.

At normal poster size verify separated dots; at thumbnail inspect silhouette, key landmarks, and halftone reading, not individual-dot visibility. Avoid high coverage, near-touching or merged bubble/cell/perforation clusters, many adjacent sizes, and any subject with no internal breathing room. Preserve recognition in this order: source identity or exact letterforms, silhouette/contour, pose and direction, key internal structure, then secondary texture and background detail (which are omitted by default). Use the same mark family in a title transition, with parameters recorded rather than guessed.

## Color roles and authority

Assign each chosen color a role (`background`, `primary visual`, `title`, `supporting type`, `accent`, or another named role) and record why it exists. Apply this authority order:

1. explicit user color instructions;
2. `Image Transform` source colors and optical tone/lighting restoration;
3. material appropriateness and recognition;
4. high-saturation colors that carry the theme;
5. neutral contrast such as black text on white or white text on black;
6. other auxiliary colors needed by a named role.

Delete any fixed three-color ceiling and any Type-led two-saturated-color ceiling. With no source image, high saturation plus black/white may be a tendency, not a mechanical obligation. Preserve source colors when identity-bearing or requested **within mark-only reconstruction**: express them only as selected-mark fill and/or background. Visual-mode title color must be selected from the already established active palette/source/subject color roles, including existing neutral black or white; choose it to serve contrast, optical balance, and theme, never introduce a new title accent without a role. A local title raster transition inherits or bridges the image mark colors it touches and does not invent another accent. Supporting copy uses an existing neutral role. If colors reduce title visibility, change type color only within the active roles, then position, overlap, local space, or mark density before adding outlines. Never introduce a random accent or unassigned color.

## Background inference for Image Transform

Before defaulting to white, inspect the source edges and surrounding structure. Record the evidence and inference in the recipe as `edge evidence → background`: continuous dark edge, tube, dark frame, or vignette may naturally extend into a black/dark canvas while retaining a central bright region. Extend the existing field; do not create a second circular ring, artificial frame, or isolated vignette. Treat resulting black quiet areas as valid external negative space. Use white only when edge evidence and the thesis support it.

## No white edge and text priority

Explicitly prohibit `thin white keyline`, `inner stroke`, `outer stroke`, `matte fringe`, `halo`, `glow`, `faux knockout`, a white gap cut out for contrast, outline-like bright anti-aliased edges, and shadows. Keep text edge color identical to its fill; do not fake separation with a light border. If contrast fails, permit local unreadability, change color, position, overlap, mark density, local halftone treatment, or transition extent, but never add a stroke or bright edge.

Keep **exact text identity** immutable. For display text, choose `clear` or `expressive/faded` legibility; `Image Transform` and `Subject Generate` may sacrifice local display readability for fusion, while `Type-led` may become artistic only when it remains tied to exact glyph structure and the selected engine, never unrelated random texture. Keep supporting copy always clear. If the user says recognizability is not the priority, prioritize no-edge fusion and the thesis, but do not alter exact text identity or source authority.

## Prompt compiler and recipe

Compile one coherent production prompt from the Normalized Poster Spec. Make the first sentence the exact composition thesis. For `Image Transform` and `Subject Generate`, make the **second sentence** a concise abstraction/sampling plan: preserve silhouette, pose, key landmarks, requested details, and primary color relationships; omit secondary texture/background noise; allow purposeful open zones; use one coherent base rhythm and background-polarity tone mapping. Follow it with the short non-negotiable material sentence: `The primary pictorial subject must be reconstructed exclusively from discrete, solid circular dots with no continuous photo pixels/underlay; keep dots separated at normal poster size and check silhouette, key landmarks, and halftone reading at thumbnail; use no random scatter, bubble/cell clusters, or unrequested mark family.` For `Type-led`, state `The supplied title itself must be reconstructed from discrete, solid, individually distinguishable circular dots in a locally adaptive, structure-driven field; no conventional solid/vector glyph, dots merely overlaid or behind solid glyphs, or continuous glyph interiors; preserve exact contours, counters, strokes, and reading order; operate the selected creative engine on the mark field.` Only when the user explicitly requests another discrete mark family, replace the circle-specific words with that family while keeping every other material prohibition. Then write preservation and color wording explicitly as **within mark-only reconstruction**, followed by:

1. mode, primary authority, execution path, anchor, scale hierarchy, direction, viewing path, quiet-space shape, edge pressure, tension, counterweight, and image strategy;
2. silhouette, pose, key identity landmarks, and requested details preserved **within mark-only reconstruction**; primary color relationships preserved **within mark-only reconstruction** through mark fill/background only; secondary texture/background noise omitted unless requested;
3. font personality (width, weight, contour, rhythm, terminals, script support), exact title, glyph safety, layer order, fusion relation, and any selective transition region/axis/anchors; for visual modes, the 80%–90% solid / 10%–20% local mark transition measured against total title ink area;
4. color roles, active palette inheritance for title/supporting copy, and required optical-tone preservation;
5. circular-dot radius, spacing, density, fill, coherent base rhythm, limited macro flow, and no mechanical global grid (or the exact Type-led engine operating on the mark field);
6. ratio, external quiet-space calibration, title-to-image calibration, `mass_profile`, `overlap_profile`, and background edge inference;
7. only the short, task-relevant prohibitions from the spec.

Mark all supplied title and supporting copy as verbatim. Do not include discarded alternatives, questions, checklist prose, inapplicable numbers, or internal paths unless an active tool requires them. Put a fade, row count, highlight, overlap, color, or other output feature in the prompt only when the spec requires it. Claim that feature in the recipe only when the final render visibly implements it. Keep the material contract and balance decisions identical across prompt, recipe, and output; if any diverges, fail and correct the record before delivery.

## Workflow

1. Detect the source and lock exactly one mode and primary authority.
2. Lock the Pictorial Material Contract or Type Material Contract before composing; Type-led is not a material exemption.
3. Create the Normalized Poster Spec, including exact text, support state, execution path, edge evidence, mass/overlap profiles, and prohibitions.
4. Write the composition thesis with viewing path, quiet-space shape, edge pressure, and asymmetry before percentages; run the pre-render balance pass.
5. Choose font personality and fusion relation; choose one Type-led engine when applicable.
6. Select one circular-dot system for pictorial subjects and visual-mode title transition, or for the entire Type-led primary title; use one coherent base rhythm with only limited macro structure-following changes.
7. Assign color roles by authority and infer an Image Transform background from edge evidence before assuming white.
8. Compile the prompt in the required order, then render with the selected capability. Declare generative redraw; use deterministic pixel-safe operations only for explicit strict requests.
9. If a required capability or material contract is unavailable, return only prompt, recipe, and recommended specifications without claiming a render; never silently change execution path.
10. Run the mode-appropriate blocking Material Gate first (Pictorial or Type), then the blocking Balance Gate; record actual `qg_evidence`, revise only the failed variable/instruction, and retry once.
11. If either gate still fails after that targeted retry, return only prompt, recipe, and spec and state that no qualified image can be delivered.
12. Return the final raster poster when created, the exact prompt, and the recipe only after both gates pass.

## Output

Return:

**Generated Poster**

[final raster image, when created]

**Final Prompt**

[exact prompt used]

**Recipe**

- Normalized Poster Spec summary, mode, source authority, and execution path
- Pictorial or Type Material Contract (including any explicit alternative mark family), mark evidence, and preserved identity/color wording within mark-only reconstruction
- Composition thesis, anchor, hierarchy, viewing path, quiet-space shape, edge pressure, ratio calibration, external quiet space, and title-to-image calibration
- `mass_profile` optical ledger and `overlap_profile` region/depth/direction/title axis
- Image strategy, title foreground overlap, fusion relation, font personality, glyph coverage, and selective transition details
- Halftone system, local mark rhythm, background `edge evidence → inference`, and color roles
- Supporting-copy state, exact text/provenance, preserved details, and strict source record when applicable
- Type-led engine and semantic rationale, or `none` for other modes
- Mode-appropriate Material Gate and Balance Gate: executed, pass/failure evidence from the actual visual inspection, and targeted retry outcome
- Variation axis only when requested
- Recommended output specifications when rendering was unavailable or no qualified image remained after a failed gate

## Quality Gate

Evaluate visually and against the Normalized Poster Spec; do not claim pixel-exact measurement unless separately measured. Run the mode-appropriate blocking Material Gate first, then the blocking Balance Gate, then the mode checks. Record actual observations in `qg_evidence`; a prompt promise is never a pass. Retry once only when the failing gate can be repaired by changing the one variable that caused it.

### Blocking Material Gates (first)

#### Pictorial Material Gate

- For `Image Transform` and `Subject Generate`, cover the title and inspect representative shadows, midtones, and highlights: check separated dots at normal poster size; at thumbnail check only silhouette, key landmarks, and halftone reading.
- Pass only when every pictorial subject is reconstructed exclusively from the selected discrete mark family: solid circular dots by default, or the explicitly requested alternative. Source colors appear only through mark fill/background and source identity only through silhouette, pose, key landmarks, and requested details. Mark-only permits purposeful mark-free/open zones. Record separated dots at normal poster size; at thumbnail record silhouette, key-landmark, and halftone-reading evidence rather than requiring every dot to remain visible.
- Fail immediately if any `continuous photo pixels/underlay`, `smooth painted/tonal regions` or `continuous gradients`, `fine stippling`, `print texture overlay` or overlay filter, unrequested mark family, random-symbol mosaic, or original continuous layer under the marks is visible. Also fail for excessive coverage, near-touching/merged bubble-cell/perforation clusters, many adjacent sizes or unrelated local screens, no internal breathing room, secondary texture/background noise encoded without purpose, or shadows made both larger and denser by default. Treat engraving, crosshatching, or printmaking lines as failures unless the user explicitly selected a line-screen system; fail rigid global grids and perfectly straight rows through meaningful contours unless a mechanical grid was requested. Do not deliver a failed image.
- If this gate fails, make one targeted retry changing only the cause. If it still fails, return only the prompt, recipe, and spec, and state that no qualified image can be delivered.

#### Type Material Gate

- For `Type-led`, inspect the complete primary title at normal poster size and thumbnail size before the Balance Gate. The supplied words must be visibly reconstructed from the selected ASCII/halftone marks (solid filled circular dots by default), with exact glyph contours, counters, strokes, and reading order recoverable or intentionally transformed by the recorded engine.
- Fail immediately if any primary word reads primarily as a conventional solid/vector fill, if dots are merely texture over or behind an intact solid glyph, if the mark field is limited to background/outline while glyph interiors remain continuous, or if the selected creative engine is unrelated to glyph structure. A font skeleton may guide the mark field but cannot remain as a continuous final surface. Supporting copy is exempt and must remain ordinary, clear text.
- Fail if Type-led mark centers form one uniform global grid, perfectly straight rows/columns, or uniform spacing/diameter unrelated to glyph contours, unless the user explicitly requested a mechanical grid. Use coherent controlled irregularity tied to stems, counters, terminals, and the selected engine; do not use random scatter.
- If this gate fails, make one targeted retry changing only the cause. If it still fails, return only the prompt, recipe, and spec, and state that no qualified image can be delivered.

The selected Material Gate is blocking; never mark Type-led material compliance as `not applicable` merely because it has no pictorial subject.

### Blocking Balance Gate (after Material Gate)

- Inspect the full render and thumbnail with title on and off, in color and grayscale, and at edge/direction views. Use the recorded optical ledger and overlap profile, not a mathematical centroid.
- Pass intentional asymmetry only when the first focus is clear, the counterweight brings the eye back, quiet space has a deliberate shape, direction vectors are explainable, and the point field leaves internal breathing room.
- Fail imbalance when a secondary element steals focus, the eye path exits the frame, weight stacks on one side without a reason, residual blank space has no shape, the title merely tangents/crops an edge, or an undeclared side carries dense dots, high saturation, or edge pull. Also fail pictorial overcoverage that makes the subject feel crowded even when its silhouette remains readable.
- If this gate fails, change only the single variable causing the failure and retry once. If it still fails, return only the prompt, recipe, and spec and state that no qualified image can be delivered.

### All modes

- Exactly one mode and primary authority are evident; no unrelated subject or secondary visual source appears.
- The thesis is visible in anchor, hierarchy, direction/tension, viewing path, quiet-space shape, edge pressure, asymmetry, and purposeful external quiet space (approximately `55%–65%` as calibration only); no dead gap separates image and title.
- For `Image Transform` and `Subject Generate`, title is foreground/above image, actually crosses the image or halftone outer edge, and its visual mass relative to image is calibrated near `0.4–0.6` without treating that ratio as a guarantee or harming the thesis. It is not merely below or beside the image.
- Font personality is specific, theme-linked, and explained by width, weight, contour, rhythm, terminals, and script coverage; a neutral-sans swap would lose the rationale. All glyphs, including CJK, render without tofu, garbling, substitutions, clipping, or order errors.
- Exact title identity is unchanged. Display text is `clear` or intentionally `expressive/faded`; Type-led art remains tied to glyphs and its selected engine; supporting copy is always clear.
- Every pictorial subject uses solid filled circular dots by default, or one explicitly requested alternative mark family; the selected marks use a coherent base rhythm with purposeful open zones, remain separated at normal poster size, and show silhouette/key landmarks/halftone reading at thumbnail. A Type-led title is itself mark-constructed under the Type Material Gate.
- For visual modes, any title transition is selective and local: 80%–90% of total title ink remains continuous solid glyphs and 10%–20% may use the same mark family in a specified contact region, measured as `transition ink area ÷ total title ink area`; it fades size/spacing/density along a composition-chosen axis, preserves a per-word anchor unless abstraction is authorized, and uses no blur, haze, opacity wash, glow, or fixed right/bottom fade. Do not rasterize the entire visual-mode title unless explicitly requested.
- No thin white keyline, inner/outer stroke, matte fringe, halo/glow, faux knockout, contrast white gap, bright outline-like anti-alias edge, or shadow appears; text edge and fill colors match.
- Color roles follow the stated authority order with no hard palette-count rule and no random accent; visual-mode title and transition colors inherit active palette/source/subject roles, and no unrequested panel or color block appears. Supporting copy uses an existing neutral role.
- Supporting-copy state is honored exactly: required verbatim, allowed at most 1–2 authorized/user-provided lines, forbidden omitted. Material contracts, mass/overlap profiles, prompt, recipe, gates, and output agree on every claimed feature; an inconsistency fails.

### Image Transform

- Removing the title still reveals an image derived from the uploaded source, with identity, major objects, perspective, composition, spatial relationships, pose, and requested details recognizable **within mark-only reconstruction**.
- `Generative Restyle` explicitly declares redraw and makes no exact-pixel claim. `Pixel-safe / Strict Raster Transform` proves source identifier, dimensions, hash, complete source or approved crop, and deterministic operations; if any strict check fails, the result fails rather than being relabeled or silently substituted.
- Source edges were inspected before a white default. The recipe records `edge evidence → background`; dark-edge/tube/frame/vignette extension retains a central bright region when supported and never creates a second ring. Black quiet regions count as negative space.

### Subject Generate

- The generated subject is the sole pictorial authority and its defining anatomy, contour, structure, attributes, and action remain recognizable **within mark-only reconstruction**. Natural groups vary intentionally; a single subject is not copied into an equal-weight icon grid.

### Type-led

- Exact supplied text is the primary visual and is visibly constructed from the selected ASCII/halftone marks; contours, counters, strokes, and order remain recoverable or are intentionally transformed under the recorded `expressive/faded` treatment. No pictorial subject, conventional solid/vector typography, solid glyph with dots merely overlaid/behind, or conventional title-over-texture treatment appears.
- Exactly one listed creative engine is named and semantically justified. The engine operates on the mark field inside the glyphs; its marks remain related to stems, counters, terminals, and reading order rather than becoming irrelevant random texture.
