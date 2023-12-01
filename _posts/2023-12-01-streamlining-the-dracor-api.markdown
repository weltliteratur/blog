---
title: "Streamlining the DraCor API"
layout: post
author: [frank, cmil, mark]
comments: true
date: 2023-12-01
---

## Again, What Is DraCor?

DraCor, the Drama Corpora platform, is an infrastructure built to facilitate the digital research on European drama. We have currently 25 (!) TEI-encoded DraCor corpora in 19 (!) languages/dialects:

* Alsatian, Bashkir, Czech, Dutch, English, French, German, (Ancient) Greek, Hebrew, Hungarian, Italian, Latin, Polish, Russian, Spanish, Swedish, Tatar, Ukrainian, Yiddish

16 of these corpora are already running on our production server ([dracor.org](https://dracor.org/)), the others are still in the development phase and will be released when ready. Some corpora (like the Shakespeare corpus) have a stable number of plays. Depending on the corpus strategies of their maintainers, other corpora can generally grow and be updated with new plays. We call them ‘living corpora’.

## DraCor API 1.0

The TEI-encoded plays are stored in an [eXist database](http://exist-db.org/). Various encoding layers are extracted and made available via our API: customised data for individual research purposes. You can easily access the full text or text slices (a list of characters, spoken texts, stage directions) or co-occurrence networks. All API endpoints [are documented](https://dracor.org/doc/api) following the OpenAPI specification.

A little bit of history. The DraCor API has grown organically ever since we introduced it sometime in August 2017. Yet the first publically documented release on GitHub was [0.72.0](https://github.com/dracor-org/dracor-api/releases/tag/v0.72.0) in September 2020.

New endpoints were added on a frequent basis and made DraCor what it is today, a research-prone platform serving data for computational literary studies. We always tried to use meaningful names and adhere to naming patterns, but over the years some inconsistencies have slipped in.

Henny Sluyter-Gäthje revisited the consistency of names when working on her pydracor library, a wrapper for DraCor API endpoints ([see GitHub ticket](https://github.com/dracor-org/dracor-api/issues/186)). Building on her work, we revised the DraCor API, making it more consistent and sustainable.

This work took a lot of time and after the streamlined API has worked well on our staging server for a while now, we release today the first version of the DraCor API that we consider stable, [our 1.0.0](https://github.com/dracor-org/dracor-api/releases).

<figure style="text-align:center;">
  <img src="/images/dracor/dracor-mockup-2023.jpg" alt="DraCor Mockup 2023" style="width:600px; border: 1px solid transparent; border-color: black;}" />
</figure>
<center><p style="font-size: 16px; line-height: 24px;"><b>Fig. 1.</b> This mockup is part of the new <b><a href="https://dracor.org/doc/media-kit">DraCor Media Kit</a></b> by Mark Schwindt, released along with the new API version.</p></center>

## Legacy API

From here on out, we would like that everyone who works with the DraCor API to use version 1.x. The URL paths on dracor.org now have a `/v1` prefix (e.g., `https://dracor.org/api/v1/info`).

However, the last pre-release version of the API will remain to be available under URLs featuring a `/v0` prefix (e.g., `https://dracor.or/api/v0/info`). Old URLs without a version prefix will be redirected to the versioned ones. For instance, `https://dracor.org/api/info` now redirects to `https://dracor.org/api/v0/info`. This should allow old scripts to function as long as they follow the redirect.

We plan to keep the API version 0.x available for at least a year. After that period we may choose to fade it out so as not to have to maintain multiple versions of the API indefinitely. Also see [dracor.org/faq](https://dracor.org/faq).

## pydracor and rdracor

Our API wrappers will be updated to work with our API version 1.0.

pydracor is available [via PyPI](https://pypi.org/project/pydracor/), rdracor [via CRAN](https://cran.r-project.org/web/packages/rdracor/index.html).

## Other Updates

We introduced a new `/wikidata/mixnmatch` endpoint to automatise the integration of DraCor permalinks into Wikidata.

We retired the `/corpora/{corpus}/plays/{play}/segmentation` endpoint so as to reduce redundancies (the same information can be obtained via the `/corpora/{corpus}/plays/{play}` endpoint).

For now, the RDF endpoint has been removed from the OpenAPI specification as it needs more work. This is something we prioritise and plan to release rather sooner than later, probably with a 1.1 release of our API.

With this release, we also updated our eXist-db from 6.0.1 to 6.2.0.

## The Team Behind the Update …

… includes Carsten Milling, Henny Sluyter-Gäthje, Ingo Börner, Peer Trilcke, Daniil Skorinkin (all University of Potsdam), Frank Fischer, Viktor J. Illmer, Mark Schwindt, Julia Beine, Heinz-Alexander Fütterer (all Freie Universität Berlin) and Ivan Pozdniakov. The implementation was largely carried out as part of the "CLS INFRA" project ([funded through EU's Horizon 2020 programme](https://cordis.europa.eu/project/id/101004984)) and the Cluster of Excellence "EXC2020 Temporal Communities" ([funded through DFG](https://gepris.dfg.de/gepris/projekt/390608380)).

DraCor was founded as a community project and, as always, numerous friends and colleagues have contributed feedback and ideas while working on their corpora or conducting research based on data from DraCor.

The platform, [once praised](https://twitter.com/eumanismo/status/1218066125969412096) for its original guerilla strategy – although this is debatable 😊 – has become a well-frequented part of the international research infrastructure. We trust that this API 1.0 release will contribute to making digital research on European drama (and beyond) more reliable and sustainable.

Goodbye for now, may your requests be valid, your responses swift, and your status codes always successful!
