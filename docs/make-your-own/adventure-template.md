---
title: "Adventure Template (Author's Guide)"
description: "A short sample adventure that teaches Markdown, Just the Docs, and site plugins as you read it."
nav_order: 4
parent: 🔨 Make Your Own
---

# Adventure Template (Author's Guide)
{: .no_toc }

AN ADVENTURE IN LEARNING FOR ALL LEVELS

Version 0.1

This text is licensed [Creative Commons BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). Unless otherwise noted, images in this document are licensed [CC0 Public Domain](https://creativecommons.org/publicdomain/zero/1.0/). Each adventure and ruleset on this site has its own license.

![Eclipse Orb](/assets/images/adventure-template/eclipse-orb.png)
This [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) illustration by **[Gordy](https://gordyh.itch.io/)** is embeded using only markdown. There's no size or position information.

## Table of contents
{: .no_toc }

This heading and the one above it use `{: .no_toc }` so it does not appear under the in-page table of contents or the navigation bar to the left.

- TOC
{:toc}

The **Table of contents** section above uses Just the Docs’ built-in `{:toc}` tag. With the [TOC navigation plugin](https://github.com/sunflowermans/toc-navigation) enabled, those same headings also appear in the navigation sidebar on the left.

# Credits

Written by **[directsun](https://puzzledungeon.com/)**

Art by **[Gordy](https://gordyh.itch.io/)**

# Overview

## Hook

<a href="/assets/images/adventure-template/tavern-quest-giver.png" target="_blank"><img src="/assets/images/adventure-template/tavern-quest-giver.png" style="float: right; margin: 0 0 10px 10px; max-width: 50%;"></a>

A nervous patron hires the party to explore **The Formatting Cellar**, a tutorial dungeon where every room demonstrates something you can reuse in your own adventure. The patron stresses that you should reference the source Markdown file [`adventure-template.md`](https://raw.githubusercontent.com/sunflowermans/digital-gm/refs/heads/main/docs/adventure-template.md) while navigating the cellar to reveal how it was created.

When questioned about the image displayed here, they explain that it is embedded using HTML. It's positioned to the right, the text wraps to the left, there's margins, and there's a maximum percentage width. The `<a>` anchor tag contains a hyperlink to the full-size image which opens in a new tab.

<!-- This div clears the image float style so that tall images dont bleed into the next header's section -->
<div style="clear: both;"></div>

## Front matter

Every page in `docs/` begins with **YAML front matter** between `---` lines. At the top of this Markdown file, the front matter sets the sidebar title, search description, and sort order.

```yaml
---
title: "Adventure Template (Author's Guide)"
description: "A short sample adventure that teaches..."
nav_order: 4
---
```

Save your adventure as `docs/your-adventure-name.md`. Lower `nav_order` numbers appear higher in the sidebar.

## Dungeon features

Use **callouts** for reminders, read-aloud text, or blocks of other important information that should stand apart from the rest.

{: .note .callout}

> Unless otherwise noted, these features hold true for the whole cellar:
>
> * **Light:** None.
> * **Doors:** Stuck wooden doors; 1-in-6 chance to open.
> * **Ceilings:** 10 feet high.

This site includes the following styles by default: `note`, `highlight`, `monster`, and `item`. Exploring the [Scriptorium](#3-scriptorium)) shows the rest of the callout styles in action.

Refer to Just The Docs [documentation on callouts](https://just-the-docs.com/docs/ui-components/callouts/) for more features and how to style your own.

# Map

Click a region to jump to a room key. The [image-links plugin](https://github.com/sunflowermans/image-links) reads region data from a YAML file in `assets/maps/`.

{::nomarkdown}
<img
  class="jil-map-image"
  src="/assets/images/adventure-template/formatting-cellar.png"
  alt="Formatting Cellar demo map"
  loading="lazy"
  data-jil-title="The Formatting Cellar"
  data-jil-regions="assets/maps/adventure-template.yml"
  data-jil-viewer="true"
  data-jil-inline="true"
  data-jil-labels="true"
/>
{:/nomarkdown}

To add your own map:

1. Put the map image in `assets/images/your-adventure/`.
2. Create `assets/maps/your-adventure.yml` with `regions:` — each region needs `href`, optional `title`, and `points` as `[x, y]` pixel coordinates on the image.
3. Embed the image as above with `<img class="jil-map-image" …>` wrapped in `{::nomarkdown}…{:/nomarkdown}`.

```yaml
# assets/maps/your-adventure.yml
width: 1200
height: 800
regions:
  - href: /docs/room-a/
    title: Room A
    points: [[120, 80], [420, 80], [420, 320], [120, 320]]
  - href: /docs/room-b/
    title: Room B
    points: [[480, 120], [760, 120], [760, 420], [480, 420]]
```

See the [image-links plugin readme](https://github.com/sunflowermans/image-links/blob/main/README.md) for more information.

{: .note-title }
> Note
> 
> [Image-Map.net](https://www.image-map.net/) is a useful tool for grabbing pixel coordinates from an image.

# Keys

## 1. Entrance Hall

<a href="/assets/images/adventure-template/goblin-ambush.png" target="_blank"><img src="/assets/images/adventure-template/goblin-ambush.png" style="float: right; margin: 0 0 10px 10px; max-width: 50%;"></a>

***Torchlight reveals a stone arch carved with curly brackets and hash marks.*** This read-aloud text is styled with triple asterisks: `***like this***`.

***A plaque reads:*** **“Hover me.”** Internal links like [goblin scribe](#goblin-scribe) and [2. Dice Chamber](#2-dice-chamber) open preview windows when you hover (desktop) or long-press (mobile). The links work with other documents on the site as well, like these [evasion rules](/docs/ose-rules/adventures/encounters/#evasion) from OSE. Holding SHIFT keeps a preview window open.

<!-- This div clears the image float style so that tall images dont bleed into the next header's section -->
<div style="clear: both;"></div>

## 2. Dice Chamber

***A dice tray rests atop a worn oak table.*** The [dice-tray plugin](https://github.com/sunflowermans/dice-tray) turns common dice notation into clickable rolls.

* Attack roll: d20+3
* Damage: 2d6
* Random encounter: 1-in-6 each turn
* Advantage: d6 + d8 (take highest)

You can also roll from tables:

| **1d3** | **Result** |
| ------- | ---------- |
| **1** | A [Goblin scribe](#goblin-scribe) offers bad advice. |
| **2** | A callout materializes on the wall (see [Overview](#dungeon-features)). |
| **3** | Treasure: [Silver Stylus](#silver-stylus). |

## 3. Scriptorium

{: .highlight}
> Shelves hold blank scrolls and three labeled cubbies: *Highlight*, *Monster*, and *Item*.

Here are examples of the default [callout](#dungeon-features) styles. Use blockquotes for read-aloud text, stat blocks and magic items. Add a Kramdown attribute line before the quote to style it and assign an anchor id for links:

{: .monster #goblin-scribe}
> **Goblin Scribe**
>
> AC 7 [12], HD 1 (4hp), Att 1 × quill (1d3), THAC0 19 [+0], MV 60′ (20′), ML 6
>
> * **Pedantic**: Insists on correcting your Markdown.

{: .item #silver-stylus}
> **Silver Stylus**
>
> Writes in any language. Worth 50 gp. Links to itself like this: [Silver Stylus](#silver-stylus).

# Wandering encounters

1-in-6 chance every turn in the cellar.

| **1d12** | **Encounter** |
| -------- | ------------- |
| **1**    | 1d6 [goblin scribes](#goblin-scribe) rewriting each other’s drafts. |
| **2**    | An NPC asks how URLs are generated. (see [below](#urls-and-file-names)) |
| **3–12** | Nothing. The cellar is mostly documentation. |

# Appendicies

## Checklist for your adventure

Copy this file, rename it, and work through the list:

- [ ] Update front matter (`title`, `description`, `nav_order`).
- [ ] Replace credits and license text.
- [ ] Add optional cover art with a linked thumbnail: `<a href="…"><img src="…"></a>`.
- [ ] Write an **Overview** (hook, entrance, special rules).
- [ ] Add a map image plus `assets/maps/your-adventure.yml` regions.
- [ ] Write entries with `**text styles**` and `[internal links](#anchors)`.
- [ ] Put monsters in `{: .monster #anchor}` blockquotes; items in `{: .item #anchor}`.
- [ ] Drop dice notation naturally in the prose (`2d6`, `3-in-6`, `d20+5`).
- [ ] Put images in `assets/images/your-adventure/` and reference them with site-root paths (`/assets/images/...`).

## URLs and file names

Settings in `_config.yml` control how URLs are formed. `permalink: pretty` and `heading_anchors` are enabled by default.

This document, with the original file name of `adventure-template.md`, is served at `/docs/adventure-template/`.

Headings become anchor links automatically: `## 1. Entrance Hall` → `#1-entrance-hall`.

## Side-by-side images

Use a little HTML when Markdown alone is awkward:

<div style="display: flex; gap: 10px;">
<div>
  <a href="/assets/images/adventure-template/crypt.png" target="_blank" style="flex: 1;">
    <img src="/assets/images/adventure-template/crypt.png" style="width: 100%;">
  </a>
<center>Crypt</center>
</div>
  <div>
  <a href="/assets/images/adventure-template/wizard-attack.png" target="_blank" style="flex: 1;">
    <img src="/assets/images/adventure-template/wizard-attack.png" style="width: 100%;">
  </a>
<center>Wizard Attack</center>
</div>
</div>

## References

* [Just The Docs](https://just-the-docs.com/) — more styling and configuration documentation
* [Markdown cheat sheet](https://www.markdownguide.org/cheat-sheet/) — formatting options

## Example adventures
* [Puzzle Dungeon: The Seers Sanctum](/docs/seers-sanctum/) — full adventure with figure-style map and room art
* [A Familiar Tower](/docs/a-familiar-tower/) — multi-level maps, creature appendix, and cross-page rule links

When your draft is ready, follow the [submission guide]() to share it or [host your own site]().
