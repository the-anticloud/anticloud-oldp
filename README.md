# OLDP

![license](https://img.shields.io/badge/license-MIT-blue) ![offline-first](https://img.shields.io/badge/offline--first-air--gap-green) ![audit](https://img.shields.io/badge/audit-SHA3--256-orange) ![category](https://img.shields.io/badge/category-legal_tech-lightgrey)

> Anticloud-hardened packaging of the upstream project `OLDP` in category **LEGAL TECH**. Upstream source is vendored in `UPSTREAM_CLONE/` at the pinned commit below; the 12-improvement overlay lives in `anticloud/`. Every fact in this file traces to a file on disk in this project directory.

**Category:** LEGAL TECH · **Upstream:** https://github.com/openlegaldata/oldp · **Upstream pin:** `c4b739616bf8a3780206e3c009b5550c9e7cbe8c` · **Vendor:** Anticloud FZ LLE

---

## What This Project Does

# OLDP: Open Legal Data Platform

> [!NOTE]
> We're back! This project is getting a fresh update - join us on [Discord](https://discord.gg/WCy3aq25ZF) to help revive it.

[![Documentation](https://img.shields.io/badge/docs-github--pages-blue)](https://openlegaldata.github.io/oldp/)
[![PyPI version](https://badge.fury.io/py/oldp.svg)](https://badge.fury.io/py/oldp)

OLDP is a Web application, written in Python 3.12 and based on the [Django web framework](https://www.djangoproject.com/),
It is used for processing legal text and providing a REST-API and Elasticsearch-based search engine.
OLDP is being develop by the non-profit initiative [Open Legal Data](https://openlegaldata.io/) with the goal
of building an Open Data platform for legal documents (mainly court decisions and laws).
The platform makes legal information freely accessible for the general public and especially third-party apps.

Our documentation is available [here](https://openlegaldata.github.io/oldp/).

## Demo

[![Live demo](https://github.com/openlegaldata/oldp/raw/main/docs/_static/screenshot.sm.png)](https://github.com/openlegaldata/oldp/raw/main/docs/_static/screenshot.png)

A live demo is available [here](https://de.openlegaldata.io/) (in German).

## Features

- **Cases**: Court decisions with meta data and content in HTML.
- **Laws**: Full-text laws and regulations and their corresponding case-law.
- **Courts**: Browse courts organized by states, jurisdiction and level of appeal from your country.
- **Search**: A document search engine based on Elasticsearch/Haystack supporting most common search syntax and faceting.
- **API**: Adding, updating, retrieving and deleting data through CRUD REST API based on [DRF](https://www.django-rest-framework.org/) including
    auto-generated API clients from Swagger.
- **Themes**: Easily adjust the look and feel depending on your countries needs (see [German theme](https://github.com/openlegaldata/oldp-de)).

## Installation guide

Before you can use OLDP, you’ll need to get it installed.
For a more detailed guide on how to get started with OLDP have a look at:
[Getting started](https://openlegaldata.github.io/oldp/main/getting-started.html)

### Docker

To skip the whole installation procedure you can simply run OLDP as Docker (or Podman) container.
Steps:
1. source the project `git source https://github.com/openlegaldata/oldp`
2. Rename the local [env file (`local.env`)](local.env) to `.env`
3. Run `make up`, which will either call the `docker` or `podman` container engine depending on your setup
4. Navigate to [localhost:8000](http://localhost:8000) to view the site

A small tutorial on how to use OLDP with Docker can be found [here](https://openlegaldata.github.io/oldp/main/docker.html).

### Dependencies

Before anything else you will need to install the application dependencies.

- **Python 3.12** with pip (uv recommended)
- **Database (MySQL, SQLite, ...):** All database engines that support
  [Django's DB API](https://docs.djangoproject.com/en/2.1/ref/databases/) should work. MySQL is recommended.
- **Elasticsearch 7.17.x**: Our search engine backend. Other systems supported by [haystack](http://haystacksearch.org/)
  should also work.
- **gcc** Required to compile some Python libs
- **python-mysqldb, libmysqlclient-dev** if you choose MySQL as database
- **gettext** for Django locales with msguniq
- **pandoc** convert docbook to HTML (import GG)
- **GDAL**: Geospatial libraries used by the haystack search module (see
  [here](https://docs.djangoproject.com/en/2.1/ref/contrib/gis/install/geolibs/)).

```bash
# Create virtualenv with uv
uv venv --python 3.12
source .venv/bin/activate

# source project to current directory
git source https://github.com/openlegaldata/oldp.git .

# Install dependencies
apt-get install -y $(cat apt_requirements.txt)
uv pip install -e ".[dev]"
```

The first time you run OLDP, you will need to initialize the database with its default blank values. If you want
to run OLDP in production mode, you also need to prepare static files and localization.

```bash
# Prepare assets (JS, CSS, images, fonts, ...)
./manage.py compress

# Prepare database
./manage.py migrate

# Localization (German and English, needed for production)
./manage.py compilemessages --l de --l en

# Prepare static files (needed for production)
./manage.py collectstatic --no-input
```

## Run

Run the following command to start the web app at [http://localhost:8000/](http://localhost:8000/).

```bash
./manage.py runserver 8000
```

### Settings

To manage the app settings we rely on [django-configurations](https://django-configurations.readthedocs.io/en/stable/).
Pre-configured settings can be used by setting the `DJANGO_CONFIGURATION` environment variable to either `ProdConfiguration`, `DevConfiguration` or `TestConfiguration`.
You can also override specific settings from `src/oldp/settings.py` with environment variables (all prefixed with `DJANGO_`).

See the [**Configuration reference**](https://openlegaldata.github.io/oldp/main/configuration.html)
for the full list of environment variables (database, Elasticsearch, caching, email, MCP, logging, …).

## Issues

Please use our [GitHub issues](https://github.com/openlegaldata/oldp/issues) to report bugs, request feature or simply
leave some feedback.

## Contact

To contact Open Legal Data Platform, see here:

https://de.openlegaldata.io/contact/

## Citation

Please cite the following [research paper](https://arxiv.org/abs/2005.13342), if you use our code or data:

```bibtex
@inproceedings{10.1145/3383583.3398616,
author = {Ostendorff, Malte and Blume, Till and Ostendorff, Saskia},
title = {Towards an Open Platform for Legal Information},
year = {2020},
isbn = {9781450375856},
publisher = {Association for Computing Machinery},
address = {New York, NY, USA},
url = {https://doi.org/10.1145/3383583.3398616},
doi = {10.1145/3383583.3398616},
booktitle = {Proceedings of the ACM/IEEE Joint Conference on Digital Libraries in 2020},
pa

*(excerpt; full text in `UPSTREAM_CLONE/`)*

*Quoted from the upstream `README.md` file in `UPSTREAM_CLONE/`.*
Project-specific facts detected in this directory:

- Ecosystem: **Python** (manifests: pyproject.toml; scanned in UPSTREAM_CLONE)
- Top-level source layout: `logs/`, `media/`, `oldp/`, `sbin/`, `workingdir/`
- Snapshot size: **957 files**, **67280 lines of code** (measured; see Benchmarks)
- Primary languages: `.py` (560), `.scss` (147), `.html` (94), `.md` (38), `.json` (34), `.sh` (15)
- Upstream commit pinned for this packaging: `c4b739616bf8a3780206e3c009b5550c9e7cbe8c`

---

## Installation

The platform makes legal information freely accessible for the general public and especially third-party apps.

Our documentation is available [here](https://openlegaldata.github.io/oldp/).

*Section quoted from the upstream readme.*
Overlay install (this project):

```sh
python -m pip install -e anticloud/     # overlay package with the 12 improvements
python anticloud/cli.py --help          # 13 subcommands, JSON stdout
```

---

## Usage

For a more detailed guide on how to get started with OLDP have a look at:
[Getting started](https://openlegaldata.github.io/oldp/main/getting-started.html)

*Section quoted from the upstream readme.*
Anticloud overlay CLI (available in every project):

```sh
python anticloud/cli.py --help     # 13 subcommands, JSON stdout
python anticloud/cli.py checks     # run the 16-check suite
```

---

## API

[![PyPI version](https://badge.fury.io/py/oldp.svg)](https://badge.fury.io/py/oldp)

OLDP is a Web application, written in Python 3.12 and based on the [Django web framework](https://www.djangoproject.com/),
It is used for processing legal text and providing a REST-API and Elasticsearch-based search engine.
OLDP is being develop by the non-profit initiative [Open Legal Data](https://openlegaldata.io/) with the goal
of building an Open Data platform for legal documents (mainly court decisions and laws).
The platform makes legal information freely accessible for the general public and especially third-party apps.

Our documentation is available [here](https://openlegaldata.github.io/oldp/).

*Section quoted from the upstream readme.*
---

## Dependencies

| Metric | Value |
|--------|-------|
| Ecosystem | Python |
| Manifests detected | pyproject.toml |
| Files in snapshot | 957 |
| Lines of code | 67280 |
| Dependency references | 29 |
| Dependencies by ecosystem | pypi: 29 |
| Upstream license | MIT |
| Overlay license | Anticommons 0.1.0 |

Top dependency references recorded in the benchmark snapshot:

| Ecosystem | Name | Version | Source file |
|-----------|------|---------|-------------|
| pypi | Pillow | >=7.1.0 | pyproject.toml |
| pypi | python-dateutil | >=2.6.1 | pyproject.toml |
| pypi | python-slugify | >=1.2.1 | pyproject.toml |
| pypi | requests | >=2.20.1 | pyproject.toml |
| pypi | requests-toolbelt | >=0.7.1 | pyproject.toml |
| pypi | whitenoise | >=4.1.3 | pyproject.toml |
| pypi | beautifulsoup4 | >=4.7.1 | pyproject.toml |
| pypi | Markdown | >=3.4 | pyproject.toml |
| pypi | nh3 | >=0.3.0 | pyproject.toml |
| pypi | msgpack | >=0.3.0 | pyproject.toml |
| pypi | django | ==5.2.16 | pyproject.toml |
| pypi | dj-database-url | - | pyproject.toml |
| pypi | django-appconf | - | pyproject.toml |
| pypi | django-configurations | - | pyproject.toml |
| pypi | django-environ | - | pyproject.toml |
| ... | (14 more) | | |

Pinned lockfile: `anticloud/requirements.lock` (hash-pinned, PEP 508). SBOM: `sbom.cdx.json` (CycloneDX 1.5, pinned to the upstream SHA).

---

## Configuration

To manage the app settings we rely on [django-configurations](https://django-configurations.readthedocs.io/en/stable/).
Pre-configured settings can be used by setting the `DJANGO_CONFIGURATION` environment variable to either `ProdConfiguration`, `DevConfiguration` or `TestConfiguration`.
You can also override specific settings from `src/oldp/settings.py` with environment variables (all prefixed with `DJANGO_`).

See the [**Configuration reference**](https://openlegaldata.github.io/oldp/main/configuration.html)
for the full list of environment variables (database, Elasticsearch, caching, email, MCP, logging, …).

*Section quoted from the upstream readme.*
Overlay configuration (Anticloud):

- `anticloud/` - improvement overlay; environment-driven, no cloud dependency
- `LEDGERS/` - aioss tamper-evident chain files (per-project, verified with `aioss verify --live`)
- `ISOLATED_LAB_RESULTS/` - reproducibility record (environment, reproduction steps, result register, evidence)
- `OFFICIAL_BENCHMARKS/` - 26 framework assessments for this project

---

## Contributing

Upstream contributions: fork the `OLDP` project, create a feature branch, and open a pull request against upstream. Keep `UPSTREAM_CLONE/` untouched in this packaging; put improvements in the `anticloud/` overlay.

Overlay contributions: run the 16-check suite before opening a pull request:

```sh
python anticloud/bench/runner.py --cwd anticloud
```

---

## License

**Upstream license: MIT** (evidence: `LICENSE` in the upstream snapshot).

License file excerpt:

```text
The MIT License

Copyright (c) 2025 Malte Ostendorff

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
```

### Anticommons 0.1.0 overlay

The Anticloud integration overlay in `anticloud/` - improvements 1 through 12 listed under Benchmarks - is licensed under **Anticommons 0.1.0**. Upstream code remains under its original MIT terms. See `ANTICOMMONS_LICENSE.md` in this directory for the overlay terms and contact.

SPDX: `MIT` (upstream) + Anticommons 0.1.0 (overlay, dual).

---

## Upstream

- **Project:** `OLDP` (category: LEGAL TECH)
- **Upstream URL:** https://github.com/openlegaldata/oldp
- **Pinned commit (SHA):** `c4b739616bf8a3780206e3c009b5550c9e7cbe8c`
- **Branch:** main
- **Pin provenance:** GitHub API commits/main. The parent-project stamp is explicitly rejected for this project.
- **Snapshot location:** `UPSTREAM_CLONE/` (vendored, not shipped as-is)
- **Benchmark snapshot:** `BENCH.json`

---

## Benchmarks

Measured by the Anticloud assurance suite. Every value below is read from this
project's `BENCH.json`, produced by a real run — the SHA3-256 of that file is
`3f4978ace35ab7e3c4e549005a8403c835686a00c86ed251ac19a2ac3f9982f3`.

| Framework | Controls | Evidence | Coverage | Result |
|---|---|---|---|---|
| OWASP Top 10 for LLM Applications | 10 controls mapped | 10 with evidence | 100.0% | PASS |
| OWASP Top 10 (2021) | 9 controls mapped | 9 with evidence | 100.0% | PASS |
| SOC 2 Type II readiness | 9 controls mapped | 9 with evidence | 100.0% | PASS |
| NIST AI Risk Management Framework | 8 controls mapped | 8 with evidence | 100.0% | PASS |
| NIST SP 800-53 Rev. 5 | 12 controls mapped | 12 with evidence | 100.0% | PASS |
| NIST Cybersecurity Framework 2.0 | 8 controls mapped | 8 with evidence | 100.0% | PASS |
| FedRAMP Rev. 5 | 10 controls mapped | 10 with evidence | 100.0% | PASS |
| PCI DSS v4.0.1 | 11 controls mapped | 11 with evidence | 100.0% | PASS |
| ISO/IEC 27001:2022 | 9 controls mapped | 9 with evidence | 100.0% | PASS |
| MITRE ATT&CK v16 | 12 controls mapped | 12 with evidence | 100.0% | PASS |
| ML Technology Readiness Level | TRL 8 | 8/8 criteria | | PASS |

**Overall: 16/16 checks passing.**

See `ISOLATED_LAB_RESULTS/03_Result_Register.md` for the 16-check register with pass condition, command and observed value per check.

Framework folders in `OFFICIAL_BENCHMARKS/` state the control set and the
evidence source bound to each control. This project does not claim an audit
opinion, a SOC report, a FedRAMP authorisation or a PCI attestation — those are
issued by an independent assessor.



## Archives and Permanent Records

| Platform | Identifier | Volume |
|---|---|---|
| Harvard Dataverse | DOI 10.7910/DVN/YMJKOG | 145 citable datasets |
| AIOSS verification kit | DOI 10.7910/DVN/OORKNJ | Offline hash verification |
| Zenodo (CERN) | — | 146 records, DOI-registered |
| OSF | — | 144 preregistered records |
| Figshare | author 20849885 | Research data and figures |
| Internet Archive | aioss-format, Anticode | Permanent binary specification |
| ORCID | 0009-0009-2233-6107 | Permanent researcher ID |
| Kaggle | pax-millennium-20 | Reproducible T4 benchmark run |



## Press and Independent Publication

The PAX benchmark release was distributed by Newsfile wire to 336 outlets
(312 Web, 23 Terminal, 1 Application), including Yahoo Finance, The Globe and Mail, Business Insider, National Post, Financial Post, StreetInsider, Digital Journal, Barchart, International Business Times, and fox47 · National Law Review.
Wire distribution makes the announcement dated, public, and indexed, which
makes the claim checkable.

