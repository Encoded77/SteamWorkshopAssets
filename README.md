# workshop-assets

Published Steam Workshop material — one folder per mod. Rendered images from
this repo are served through jsDelivr, so **this repo must be public** and
everything in it is world-readable.

Authored and published with
[SteamWorkshopDescriptionHelper](../SteamWorkshopDescriptionHelper).

## Layout

```
<ModName>/
  content/       one YAML file per generated image
  description/   description.txt and urls.yaml
  assets/        source icons and screenshots
  out/           rendered PNGs (the published artifacts)
```

`swdh.workspace.json` names the GitHub repo and branch that URLs are generated
against.

## How images are served

Rendered PNGs are committed here on an explicit publish, and referenced from
Steam descriptions as:

```
https://cdn.jsdelivr.net/gh/<owner>/<repo>@<commit-sha>/<Mod>/out/<name>.png
```

URLs are pinned to a **commit SHA**, not a branch. That makes each URL immutable
and sidesteps jsDelivr's aggressive caching — a published description keeps
pointing at exactly the image it was written against, even after later
publishes.

This is also why publishing is two steps: the commit has to exist before its SHA
can appear in `urls.yaml`.

## Why not an image host

Imgur geoblocked the UK in September 2025 rather than comply with the Online
Safety Act, silently breaking embedded images for a slice of every audience.
That risk applies to any consumer UGC image host. A repo served by a developer
CDN has no such exposure, no expiry, and no hotlinking restriction.

## Note on history

PNGs are binary, so every published version is kept in git history forever.
Rendering is local; only an explicit publish writes here. Iterating on a design
does not touch this repo.
