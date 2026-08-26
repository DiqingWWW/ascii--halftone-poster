---
name: ascii-halftone-poster
description: Create editorial ASCII and halftone posters from an uploaded image, a described subject, or exact supplied text. Use when an agent must faithfully transform a source image, generate a new pictorial subject, or construct a type-led poster while preserving source authority, exact text, deliberate negative space, and visible discrete-mark rendering.
---

# ASCII Halftone Poster

Create one poster from one primary authority. First lock the mode, then apply only the rules owned by that mode. Never let a later layout, typography, color, or negative-space preference override source authority or exact supplied text.

## 1. Select one mode

1. **Image Transform** — the user supplies an image that must remain the sole pictorial source.
2. **Subject Generate** — no source image is supplied and the user describes a pictorial subject to generate.
3. **Type-led** — no source image is supplied and exact text is intended to be the primary visual object.

Ask one concise question only when the image role, primary authority, required text, crop permission, or requested execution fidelity is materially ambiguous. Do not combine modes to avoid asking.

## 2. Priority and override order

Apply instructions in this order:

1. explicit user requirements;
2. mode and primary authority;
3. exact text and authorized supporting copy;
4. execution fidelity and permitted transformations;
5. selected mark system and subject recognizability;
6. mode-specific composition and typography;
7. color, negative-space, and stylistic defaults;
8. optional embellishment.

Lower items must yield to higher items. Percentages and style tendencies are calibration, never reasons to violate source fidelity, text identity, or the chosen mode.

## Blocking material contract

Lock the mode and primary authority first, then lock the applicable material contract before making any composition decision.

For Image Transform and Subject Generate, reconstruct the primary pictorial subject exclusively from discrete marks in the selected family. With the default system, every subject mark is a solid filled circle. Express source colors only through mark fill and the background, and express source identity through silhouette, pose, key landmarks, spatial relationships, and requested details. Never retain a continuous source layer beneath the marks.

Fail the material contract if the subject contains continuous photographic pixels or underlay, smooth painted or tonal regions, continuous gradients, fine stippling, a print-texture overlay or filter, engraving, crosshatching, an unrequested mark family, a random-symbol mosaic, hollow or ring marks when not requested, or an intact continuous/original layer beneath the marks.

For Type-led, construct the primary title letterforms from the selected marks. A conventional solid/vector glyph, a solid glyph with dots overlaid, or marks limited to the background or outline fails. Supporting copy remains ordinary clear text.

## 3. Mode contracts

### Image Transform

Treat the uploaded image as the sole pictorial authority. Preserve its identity, principal objects, pose, perspective, framing, spatial relationships, directional flow, and meaningful background structure. Do not replace, invent, relocate, duplicate, or anatomically redraw subjects merely to improve the poster layout.

Use **Faithful Transform** by default:

- derive the halftone layer from the supplied image;
- preserve the complete source frame unless the user authorizes a crop;
- when the source and poster ratios differ, pad or embed the source rather than silently recomposing it;
- permit tonal simplification, selected-mark reconstruction, source-aware color mapping, scaling, padding, and separate typography layers;
- adapt the poster around the source instead of redesigning the source around the poster.

Use **Generative Restyle** only when the user explicitly permits reinterpretation, redraw, scene extension, replacement, or similar generative change. State that semantic fidelity rather than pixel fidelity is expected. Never relabel a generative redraw as a faithful transform.

Use **Strict Raster Transform** when the user requires exact pixels or no redraw. Use deterministic raster operations only, record the source identifier and crop decision, and do not invoke a generative editor. If the required capability is unavailable, return a production prompt and recipe without claiming a completed image.

Image Transform composition rules:

- place title and supporting copy in relation to the existing source mass;
- derive the layout from the source's actual mass, directional flow, hard edges, quiet areas, and landmarks; do not default to a reusable image-box-plus-caption template;
- when a safe low-information contact zone exists, establish at least one visible image–type relation: partial overlap, edge crossing, contour echo, depth, continuation, or a shared alignment path;
- title overlap is not mandatory when it would obscure identity. In that case, connect image and type through a shared axis, continued mark field, contour, or counterweight rather than leaving two unrelated rectangles;
- do not shrink, crop, extend, recolor, or move source content merely to reach a title/image ratio or negative-space percentage;
- choose the canvas substrate independently from a local dark edge, tube, frame, or vignette. Do not extend a dark source border into a dark poster canvas by default; use a dark canvas only when the user requests it or the source's overall exposure and visual mass clearly support it;
- preserve source hue, saturation, brightness range, local contrast, and the optical weight of major color fields before considering any accent. Do not globally darken, desaturate, or flatten the source. Selective contrast enhancement is allowed only when it protects midtones and does not make the transformed image perceptually darker than the source.

### Subject Generate

Treat the described subject as the sole pictorial authority. Generate recognizable anatomy, contour, material, attributes, and action without unrelated scenery or props unless requested.

Before percentages, write one concise composition thesis containing: the focal anchor and why it dominates; primary/secondary scale hierarchy; direction or action; the viewing path (`eye first lands on anchor → what carries it away → what brings it back`); the intended shape of external quiet space; edge pressure; and the asymmetric counterweight. Favor a content-derived relationship over a centered icon or equal-weight repetition. Use optical judgment, not a mathematical centroid.

Subject Generate composition defaults:

- build one connected image–type cluster with deliberate asymmetry or directional tension when appropriate;
- let title cross a sparse subject edge when this strengthens the thesis and preserves key anatomy;
- use external quiet space around the cluster; approximately 55%–65% is a calibration target, not a pass condition;
- title visual mass may calibrate near 0.4–0.6 of image mass, but optical balance outranks the number;
- vary scale, orientation, stage, or position in natural groups; do not produce equal-weight icon grids.

### Type-led

Treat exact supplied text as the primary visual. Add no pictorial subject. Construct the primary title from the selected ASCII/halftone marks; a solid glyph with dots merely overlaid, behind it, or limited to its outline fails.

Choose one semantic engine and apply it to the mark field while retaining exact contours, counters, strokes, and reading order:

- `weave/interlock`
- `compression`
- `erosion/fade`
- `echo/repetition`
- `flow`
- `fragment/reassemble`
- `counterfield/void`
- `modular stack`
- `semantic gesture`

Choose canvas ratio, lineation, axis, scale, and color from the text’s meaning. Do not inherit image/title ratios, image overlap rules, source-color rules, or Image Transform background inference.

## Optical balance process

After source authority and the material contract are locked, record a concise optical ledger in `mass_profile`:

- shape, occupied area, contour, and crop;
- luminance and contrast;
- saturation and temperature;
- mark radius, density, spacing, and flow;
- typography width, weight, line count, script complexity, and axis;
- semantic salience such as faces, eyes, and readable text;
- edge leverage and direction vectors;
- the shape of external quiet space.

For Image Transform, derive the viewing path and counterweight from the existing source; never invent a new composition thesis that overrides it. For Subject Generate, the thesis defines the intended path. For Type-led, derive the path from text semantics and glyph structure.

Before rendering, reduce the design to a few gray blocks or dot fields representing anchor, title, point field, and quiet-space shape. Record `overlap_profile` with contact region, depth, direction, and title-block axis. At thumbnail, squint, and grayscale views, confirm the intended first focus, exit direction, and return path before using percentages as calibration.

## 4. Shared mark system

Default to solid filled circular halftone. Use character ASCII, square dots, line screens, hollow marks, or another discrete family only when explicitly requested.

For pictorial modes:

- reconstruct the primary subject from visible discrete marks with no continuous photographic or painted underlay;
- carry source or subject color only through mark fill and background; carry identity through silhouette, pose, key landmarks, spatial relationships, and requested details within the mark-only reconstruction;
- use one coherent base rhythm with a broad, continuous, visibly natural range of dot sizes and purposeful open zones. "Coherent" means controlled variation, not similar-sized dots or a uniform mechanical lattice;
- derive dot diameter from a lightly smoothed tone field and local structure. Reduce dot size in edges, faces, branches, roof lines, masonry, and other landmark zones; reserve larger dots for broad low-detail tonal fields;
- choose pitch and maximum diameter from the thinnest meaningful landmark. At 100% output size, no dot may swallow a required landmark and adjacent large dots must remain separated; aim to describe a thin retained feature with at least 2–3 marks where the source resolution permits;
- allow substantially larger dots in broad low-detail tonal masses when the source requires visual density. Reduce the absolute pitch before limiting the expressive diameter range, so large relative dots can coexist with small absolute marks and protected detail. Keep neighboring dots separate and let the radius distribution span visibly small, medium, and large values rather than clustering near one mean;
- preserve the source frame and hard geometry independently from the mark field. Do not apply row-wise or column-wise sine displacement, wavy masks, or dot-envelope contours to straight walls, frames, horizons, or circular openings. Render with bleed and clip back to the exact source mask when needed;
- preserve silhouette, pose, key landmarks, and requested details; omit secondary texture and background noise by default;
- let gentle macro changes follow major contour, material, or action, but do not assign a separate screen to every edge, fold, joint, or speck;
- at normal poster size, marks should remain separated; at thumbnail, judge silhouette, landmarks, and halftone reading rather than individual dots;
- reject uniform filter-like screens, random scatter, near-touching bubble/cell clusters, merged perforation fields, and subjects with no internal breathing room;
- reject continuous photo pixels or underlay, smooth painted/tonal regions, continuous gradients, fine stippling, print-texture overlays or filters, engraving, crosshatching, unrequested mark families, random-symbol mosaics, intact continuous/original layers beneath marks, and hollow/ring marks unless requested;
- choose mark polarity from the source exposure and intended substrate. Preserve the source's perceived lightness and contrast at thumbnail size; do not let paper gaps wash out a light-background image or let a dark substrate crush midtones.

For Type-led, apply the same mark-family discipline to the title letterforms themselves. Supporting copy remains ordinary clear text.

## 5. Typography and image–type relation

Preserve all supplied text verbatim, including case, punctuation, CJK forms, and reading order. Inspect for missing glyphs, substitutions, tofu, clipped strokes, and garbling.

Choose font personality from subject material, motion, title semantics, and script support. Record a short rationale using only relevant traits such as width, weight, contour, rhythm, or terminals. Do not force expressive typography when it conflicts with source fidelity or glyph accuracy.

When the user asks for artistic or theme-responsive lettering, a generic default sans/hei font without a documented reason fails. Select a script-capable display face or deliberately transform spacing, lineation, scale, rhythm, or stroke texture to express the theme while preserving exact readable glyphs. Unrelated themes must not automatically reuse the same neutral font and layout skeleton.

For Image Transform, typography follows the source. It may sit outside the source, touch it, or overlap a sparse edge. If safe interaction space exists, use at least one explicit relation; if it does not, record why and create a non-overlapping structural link.

Prefer a coherent title color when it already supports the composition. Color variation is allowed when it has a clear material or semantic role, but do not mechanically use the source-image boundary or halftone mask as a hard color-split line. When a contact region changes, favor a gradual halftone fade, loss of mark coverage, or another source-responsive transition over automatic inversion for contrast.

For Subject Generate, choose one active relation: `counterweight`, `continuation`, `interruption`, `containment`, `bridge`, `depth`, or `structural echo`.

In either pictorial mode, keep the title primarily solid. When a local raster transition strengthens the chosen relation, retain roughly 80%–90% solid title ink and transform only a specified 10%–20% contact region into the same mark family. The transition may preserve the ink color or introduce a purposeful color change, but it should read as a gradual material transformation rather than an automatic hard cut at the image boundary. Treat these figures as visual calibration. Use no blur, haze, glow, opacity wash, white keyline, outline, matte fringe, faux knockout, or shadow.

## 6. Supporting copy

Record supporting copy as one state:

- `required` — render supplied copy verbatim;
- `allowed` — render at most one or two user-provided or explicitly authorized generated lines;
- `forbidden` — omit it and invent nothing.

If the user supplies no supporting copy and gives no authorization to generate it, use `forbidden`. Keep support text clear and free of ASCII/halftone distortion.

## 7. Color and background

Assign every color a role. Use this authority order:

1. explicit user colors;
2. Image Transform source colors and optical lighting;
3. subject material and recognition;
4. title/background contrast;
5. optional thematic accent.

Do not impose a color-count ceiling. High saturation is optional. Do not introduce an unassigned title accent; choose the title ink from the active palette. A "local transition" refers primarily to a change from solid ink into discrete marks or reduced mark coverage and does not imply a second title color. If a deliberate transition also changes color, assign that additional color an explicit role in the palette. For Image Transform, do not replace source colors merely to obtain a more fashionable palette.

## 8. Normalized Poster Spec

Create one compact record and derive prompt, render decisions, recipe, and QA from it:

```yaml
mode: Image Transform | Subject Generate | Type-led
primary_authority: uploaded_image | generated_subject | supplied_text
execution_path: Faithful Transform | Generative Restyle | Strict Raster Transform | Generative
source_policy: complete frame | authorized crop | not applicable
exact_title: verbatim text
supporting_copy: required | allowed | forbidden; exact text and provenance
mark_system: family, base rhythm, size bands, polarity, purposeful open zones
composition: mode-specific thesis or source-adaptive placement
mass_profile: optical ledger for shape, tone, color, mark field, typography, semantic salience, edge leverage, vectors, and quiet-space shape
overlap_profile: contact region, depth, direction, and title-block axis
typography: font rationale, relation, layer order, optional local transition
color_roles: named roles and authority
constraints: only task-relevant prohibitions
qa_evidence: Material Gate and Balance Gate observations, failures, and retry outcome
```

Resolve only genuinely blocking unknowns with the user. Do not silently invent fields or maintain conflicting prompt and recipe versions.

## 9. Prompt Compiler

Compile by mode. Do not use one universal instruction order.

### Image Transform compiler order

1. Declare the uploaded source as sole pictorial authority and name the execution path.
2. State the blocking material contract: reconstruct through the selected marks, carry color through mark fill/background only, and prohibit a continuous source underlay.
3. State the source frame/crop policy and permitted transformations; prohibit unapproved redraw, replacement, relocation, scene extension, and recomposition.
4. State source-adaptive composition and viewing path derived from existing mass, landmarks, edges, and quiet-space shape.
5. State exact title and supporting copy, then source-adaptive typography placement and any optional low-information overlap.
6. State canvas/padding/background treatment derived from source evidence and add only task-relevant prohibitions.

Never lead an Image Transform prompt with a new composition thesis, title ratio, negative-space percentage, fashionable palette, or typography gesture. Those are subordinate to source authority.

### Subject Generate compiler order

1. State the generated subject as sole pictorial authority and specify defining anatomy, material, attributes, and action.
2. State the blocking material contract and simplification priorities: mark-only reconstruction, with color through mark fill/background only and no continuous underlay.
3. State the composition thesis: anchor, hierarchy, direction, viewing path and return, title counterweight, edge pressure, and quiet-space shape.
4. State exact title, font rationale, image–type relation, and optional local transition.
5. State color roles and calibrated external quiet space.
6. Add only task-relevant prohibitions.

### Type-led compiler order

1. State exact text as sole visual authority and forbid pictorial subjects.
2. State the blocking Type Material Contract: the letterforms themselves are constructed from the selected marks, with contours, counters, strokes, and order preserved and no solid glyph underlay.
3. State the selected semantic engine, composition/viewing path, lineation, axis, scale, and quiet-space relation.
4. State color roles and authorized supporting copy.
5. Add only task-relevant prohibitions.

In every mode, omit internal field names, discarded alternatives, checklists, unresolved questions, and inapplicable numeric targets. Keep the prompt concise enough that mode authority and material requirements remain dominant.

## 10. Workflow and output

1. Lock mode and authority.
2. Choose execution path and permitted transformations.
3. Lock the mode-appropriate blocking material contract.
4. Create the Normalized Poster Spec, including `mass_profile` and `overlap_profile`.
5. Make only mode-owned composition, typography, mark, and color decisions; run the pre-render optical balance pass.
6. Compile in the mode-specific order and render with an explicitly bound source when applicable.
7. Run the blocking Material Gate, then the blocking Balance Gate, then the remaining mode checks. Retry once with one targeted correction when a correctable gate fails.
8. If the capability cannot satisfy source fidelity, exact text, selected-mark rendering, or optical balance, return prompt, recipe, and recommended specifications without claiming a qualified poster.

Return the final poster when qualified, the exact final prompt, and a concise recipe containing mode, authority, execution path, source/crop policy, exact text, support state, mark system, composition decision, typography relation, color roles, and observed QA result.

## 11. Quality Gates

Run the applicable blocking gates in the order below. A prompt promise is never evidence of a passing render.

### Blocking Material Gate

For Image Transform and Subject Generate, cover the title and inspect representative shadows, midtones, highlights, contours, and landmarks at 100% size and thumbnail size. Pass only when the pictorial subject is carried by the selected discrete marks and its colors appear only through mark fill/background.

Fail immediately if any primary subject region contains continuous photography or underlay, smooth tone or gradient, painted fill, fine stippling, print-texture overlay/filter, engraving, crosshatching, an unrequested mark family, a random-symbol mosaic, hollow/ring marks when not requested, or a visible original layer beneath the marks. Also fail excessive coverage, merged or near-touching bubble fields, loss of internal breathing room, or mark sizes that erase required landmarks.

For Type-led, inspect every primary word at 100% and thumbnail size. Fail if a word reads primarily as a conventional solid/vector fill, if dots merely texture an intact glyph, or if marks exist only behind or around the letterform. The selected engine must operate on the mark-built glyph while exact contours, counters, strokes, and reading order remain recoverable.

Record concrete observations in `qa_evidence`. On failure, make one material-only correction and rerender once. If it fails again, return the prompt, recipe, and specifications without presenting the image as qualified.

### Blocking Balance Gate

Inspect the full poster and thumbnail with title on and off, in color and grayscale, then inspect edge pressure and direction vectors. Use `mass_profile` and `overlap_profile` to verify that the intended anchor is seen first, the eye path leaves it through a declared carrier, and a counterweight or quiet-space shape brings attention back into the frame.

Intentional asymmetry passes only when hierarchy, direction, edge pressure, and the return path remain explainable after color is removed. Fail when a secondary element steals first focus, image and title push toward the same edge, the eye exits without returning, one side carries undeclared dense or saturated weight, quiet space is shapeless residue or a dead gap, the title merely grazes the subject, or mark overcoverage changes the declared balance.

Make one balance-only correction and rerender once. If the same failure remains, do not deliver the image as qualified.

### Shared gates

- Exactly one mode and primary authority are evident.
- Exact title and authorized support copy are correct; no unauthorized text, subject, panel, frame, logo, watermark, or signature appears.
- The selected mark family is visually real rather than a continuous image with a texture overlay.
- Marks retain a coherent rhythm and internal breathing room without mechanical filter grids or crowded bubble clusters.
- Dot size contains several perceptible levels and changes continuously with tone and structure; it is neither uniform nor randomly unrelated to the image.
- At 100% size, named landmarks remain recognizable and no oversized or merged dots erase the smallest important contours.
- At thumbnail size, the transformed image preserves the source's overall exposure, major color-field weight, and focal contrast. It must not look globally darker, paler, flatter, or less saturated unless explicitly requested.
- Color roles are traceable to the stated authority; no random accent appears.
- At thumbnail, squint, grayscale, title-on/title-off, and edge/direction views, the declared first focus and exit/return path remain evident.
- Prompt, recipe, and output agree.

### Image Transform gates

- Removing typography still reveals the supplied source rather than a redesigned or regenerated substitute.
- Principal objects, identity, pose, perspective, framing, spatial relationships, and meaningful background structure remain faithful within the selected-mark abstraction.
- Complete frame or authorized crop is honored. Ratio and quiet-space preferences did not force an unapproved crop, subject relocation, scene extension, or background replacement.
- Straight source edges remain straight, circular openings remain circular, and the exact rectangular source mask has no periodic waves, scallops, or displaced-edge gaps.
- The canvas substrate does not inherit darkness from a local source border alone. Midtones remain open, and selective contrast changes do not crush shadows or turn a normally exposed source into a dark poster.
- Faithful and strict paths contain no generative redraw. Generative Restyle is used only with explicit permission and is labeled accurately.
- Typography placement and color follow the source rather than forcing Subject Generate composition defaults. When safe contact space exists, at least one visible image–type interaction is present; the result must not read as an isolated photo rectangle plus a detached label.
- The typography recipe names a theme-relevant font or shaping rationale. An unmodified generic system font is not sufficient when expressive lettering was requested.

Inspect every Image Transform at both 100% and thumbnail size. Record: frame/hard-edge integrity, dot-size range and transition, landmark recognition, absence of a mechanical lattice, image–type relation, and font rationale. One failed item requires one targeted retry; a repeated failure cannot be reported as qualified.

### Subject Generate gates

- Defining anatomy, material, attributes, and action remain recognizable.
- The composition thesis is visible in anchor, hierarchy, direction, title relation, and shaped external quiet space.
- Repeated subjects are intentionally varied rather than equal-weight copies.
- Title integration does not obscure identity-defining anatomy.

### Type-led gates

- Exact supplied text remains the primary visual and no pictorial subject appears.
- Primary letterforms are visibly mark-constructed, not solid/vector glyphs with decorative dots.
- The selected engine is semantically justified and operates on glyph structure while preserving recoverable contours, counters, strokes, and reading order.

If a blocking gate still fails after one targeted retry, do not deliver the failed image as successful.
