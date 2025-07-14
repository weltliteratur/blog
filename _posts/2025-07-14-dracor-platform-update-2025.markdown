---
title: "DraCor Platform Update (July 2025)"
layout: post
author: [frank, cmil, ingo, julia, peer]
comments: true
date: 2025-07-14
---

- **tl;dr:** Enhanced API, Frontend and Schema, Comprehensive Documentation, and Upcoming Summit in Berlin.

After bigger updates in [August 2021](https://weltliteratur.net/dracor-summer-update-2021/) and [December 2023](https://weltliteratur.net/streamlining-the-dracor-api/), we are excited to share that DraCor just got another upgrade!

This latest release introduces a wide range of improvements – from enhancements to the API and frontend to refinements in the underlying TEI/XML data model. It is the result of months of collaborative work by our team, all in the spirit of keeping DraCor open, transparent, and easy to hack, build on, and explore. The new features come without any breaking changes.

DraCor was built as an open digital infrastructure for the computational study of European drama – spanning from ancient Greek tragedy to 20th-century theatre. Since our last major technical update, the platform has grown not only in functionality but also in content, thanks in large part to our global community of researchers and enthusiasts who have contributed new corpora. Today, DraCor hosts more than 4,000 plays across nearly 30 corpora, representing over 20 languages – and the platform continues to grow.

Before diving into the roundup of changes, we would like to give credit where it is due. The lion’s share of this update was made possible thanks to the tireless work of our technical lead, Carsten Milling, and co-lead, Ingo Börner. Development was supported through funding from [CLS INFRA](https://cordis.europa.eu/project/id/101004984) and [DraCorOS](https://oscars-project.eu/projects/dracoros-fostering-open-science-digital-humanities-connecting-dracor-ecosystem-eosc).

## 💡 A Smarter, Cleaner API

The DraCor API has seen its most comprehensive revision since the project began. Among the many changes are the following:

- **DTS Support:** We have implemented a `/dts` endpoint to align the API in line with the [Distributed Text Services (DTS) specification](https://distributed-text-services.github.io/specifications/). A DraCor Notebook documenting the new endpoint is available [here](https://github.com/dracor-org/dracor-notebooks/blob/main/dts/dts.ipynb).
- **Plaintext Endpoint:** Users can now fetch a plain text version of any play via a dedicated endpoint – making it easier to use DraCor data in NLP pipelines and other tooling.
- **Corpus Metadata Enhancements:** We now track Git commit hashes from the corpus repositories, adding another layer of provenance and traceability to our data.
- **Improved Filtering:** The `spoken-text` endpoint now features refined relation filter parameters, offering more precise ways to query dramatic dialogue.
- **Inclusive Metadata:** The API now supports both `sex` and `gender attributes`, enhancing its ability to reflect diverse encodings of character identity.
- **Better Developer Experience:** We have extended and refined our OpenAPI specification, added more comprehensive tests, and introduced a robust CI workflow for building Docker images.
- **Upgrades:** Under the hood, we have moved to **[eXist-db](https://exist-db.org/) 6.4.0** and **dracor-metrics 1.5.1**, improving both performance and maintainability.

Full API release notes here: [dracor-api changelog](https://github.com/dracor-org/dracor-api/releases).

## 🖥️ A Refined Frontend for Exploration

The DraCor frontend has also received a series of upgrades that improve usability and extend functionality:

- **New "Tools" Tab:** Data from each play can be sent directly to third-party analysis tools, such as Voyant Tools, Gephi Lite or the CLARIN Switchboard.
- **Corpus Status Overview:** We have added a [status page](https://dracor.org/doc/corpora) that provides an overview of the current state, maintenance responsibilities, and licencing of all DraCor corpora – useful for developers, curators, and researchers alike.
- **Rendering Fixes & UI Improvements:** A variety of bugs were squashed, including issues with rendering segment lists. The toolchain has been updated, and we have migrated to **pnpm** for improved dependency management.

Full frontend release notes here: [dracor-frontend changelog](https://github.com/dracor-org/dracor-frontend/releases).

## 🧾 TEI Schema 1.0: A Solid Foundation

One of the most substantial and long-awaited developments is the release of the **first stable version of the DraCor TEI schema**. It all began during a coffee break at the **[CCLS 2024](https://jcls.io/site/ccls2024/)** in Vienna – and ended in a full overhaul of how we define and validate DraCor corpora. Highlights include:

- **Based on tei_drama (TEI 4.9.0):** The schema builds on the official TEI customisation for drama, ensuring compatibility with broader TEI ecosystems.
- **More Flexibility & Clarity:** We have revised the structure to make it easier for contributors to encode new plays and for the schema to accommodate varied metadata.
- **New Elements & Better Validation:** We now support elements such as `<region>`, `<orgName>`, and `<addName>`, and introduced Schematron rules tailored to DraCor’s specific needs.

Full schema release notes here: [dracor-schema changelog](https://github.com/dracor-org/dracor-schema/releases).

## 📜 Comprehensive Documentation

Our contribution to the EU project [CLS INFRA](https://clsinfra.io/) is documented in several detailed reports that provide comprehensive insights into DraCor:

- **D7.1:** The report "On Programmable Corpora" presents DraCor as a prototype for an infrastructural ecosystem of *Programmable Corpora*, defined as corpora that expose an open, transparently documented, and a research-driven API, enabling machine-actionable access to texts. This concept builds on on Aaron Swartz's vision of "A Programmable Web" (2013), in which applications form an interoperable, dynamic ecosystem through the "natural growth" of APIs from the resources they make accessible. ([doi:10.5281/zenodo.7664964](https://doi.org/10.5281/zenodo.7664964))
- **D7.2:** The "Report on API Libraries for R and Python for the Programmable Corpora Prototype DraCor" introduces the DraCor libraries, ([rdracor](https://cran.r-project.org/web/packages/rdracor/index.html) for R and [pydracor](https://pypi.org/project/pydracor/) for Python), which provide researchers with direct programmatic access to DraCor's corpora in their preferred programming language. ([doi:10.5281/zenodo.15302236](https://doi.org/10.5281/zenodo.15302236))
- **D7.3:** The report "On Versioning Living and Programmable Corpora" addresses the challenge of ensuring research reproducibility with *living corpora* by recommending Git-based versioning for dynamic corpora and containerisation for complex programmable corpora infrastructures. ([doi:10.5281/zenodo.11081934](https://doi.org/10.5281/zenodo.11081934))
- **D7.4:** The final report of our CLS INFRA work package, "Report on the Implementation of Programmable Corpora", documents the evolution of DraCor into a standards-compliant, extensively documented service. It now features a stable API (version 1.x), Distributed Text Services (DTS) endpoints, and new tools such as [EzDrama](https://github.com/dracor-org/ezdrama) and [Who-is-@who](https://github.com/dracor-org/epdracor-whois), all of which contribute to transforming the experimental prototype into a sustainable piece of European infrastructure for computational literary studies. ([doi:10.5281/zenodo.15301341](https://doi.org/10.5281/zenodo.15301341))

## 📅 Save the Date: DraCor Summit 2025

**From 1 to 5 September 2025, the [DraCor Summit](https://summit.dracor.org/) will take place in Berlin** – hosted by the Freie Universität Berlin and the University of Potsdam. It will be five days of workshops, talks, a corpora conference, a computational drama analysis workshop, a barcamp, and even co-working time. The Summit is open to anyone working in or curious about computational literary studies, corpus development, or cultural analytics. There is no registration fee. General registration opened on 6 June – we would love to see you there!

## 🧭 Follow the Drama

To stay up to date with DraCor news, project updates, and community events, subscribe to [our mailing list](https://www.listserv.dfn.de/sympa/info/dracormailinglist) and follow the official [DraCor account on Bluesky](https://bsky.app/profile/dracor.org).

<small>(Portions of this blog post were composed with assistance from Claude Opus 4.)</small>
