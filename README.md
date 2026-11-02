# joinedcontext-sdm-linkml

Every model of the [Smart Data Models](https://smartdatamodels.org) catalogue, converted to LinkML
ahead of time. The joinedcontext Portal bakes a pinned commit of this repository into its image and
answers a model import from disk instead of converting on every click.

| Path | Holds |
|---|---|
| `index.json` | the catalogue: subjects, models, each model's upstream commit, and `failed`, the models that did not convert, each with its finding |
| `<subject>/<model>/linkml.yaml` | the LinkML model |
| `<subject>/<model>/source.json` | the upstream commit and path the model came from |

A nightly workflow regenerates the content with `tools/model-tools/src/sdm_mirror.py` of
[joinedcontext-platform](https://github.com/marek-mraz-jc/joinedcontext-platform). A run in which more
than 10 % of the catalogue fails changes nothing, so an upstream outage keeps the last good mirror.

The models are derived from the Smart Data Models repositories, which publish them under their own
licences; each `source.json` names the commit to attribute. Nothing here is edited by hand.
