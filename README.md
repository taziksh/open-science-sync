# open-science-sync

Scheduled jobs that keep these Hugging Face datasets in sync with their sources:

| Dataset | Source | Schedule (UTC) |
|---|---|---|
| [taziksh/usgs-earthquakes](https://huggingface.co/datasets/taziksh/usgs-earthquakes) | USGS ComCat | daily 06:17 |
| [taziksh/ibtracs](https://huggingface.co/datasets/taziksh/ibtracs) | NOAA NCEI IBTrACS v04r01 | Mon/Wed/Fri 12:00 |
| [taziksh/frus](https://huggingface.co/datasets/taziksh/frus) | HistoryAtState/frus | Mondays 09:17 |
| [taziksh/argo-profiles](https://huggingface.co/datasets/taziksh/argo-profiles) | Argo GDAC core profiles | Mondays 06:17 (older half-years monthly) |
| [taziksh/itrdb-tree-rings](https://huggingface.co/datasets/taziksh/itrdb-tree-rings) | NOAA NCEI ITRDB | 3rd of each month 09:17 |

Static, no sync: [taziksh/cliwoc](https://huggingface.co/datasets/taziksh/cliwoc).

Each job downloads the dataset's own `build.py` from its HF repo and runs its
update mode, which fetches only what changed upstream and pushes only the
changed files. The first run of each month also tags the HF repo (`YYYY-MM`)
so results can cite a fixed version. `status/<dataset>.json` records the last
run and its result.

Needs one secret, `HF_TOKEN`, with write access to the datasets above.
