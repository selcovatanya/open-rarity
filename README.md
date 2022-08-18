![OpenRarity](img/OR_Github_banner.jpg)

[![Version][version-badge]][version-link]
[![Test CI][ci-badge]][ci-link]
[![License][license-badge]][license-link]


# OpenRarity 

We’re excited to announce OpenRarity v0.1 (Beta), a new rarity protocol we’re building for the NFT community. Our objective is to provide a transparent rarity calculation that is entirely open-source, objective, and reproducible.

With the explosion of new collections, marketplaces and tooling in the NFT ecosystem, we realized that rarity ranks often differed across platforms which could lead to confusion for buyers, sellers and creators. We believe it’s important to find a way to provide a unified and consistent set of rarity rankings across all platforms to help build more trust and transparency in the industry.

We are releasing the OpenRarity library in a Beta preview to crowdsource feedback from the community and incorporate it into the library evolution.

See the full announcement in the blog post  <todo link to blogpost @amamujee>

# Project Setup and Core technologies

We used following core technologies in OpenRarity:

- Python ≥ 3.10.x
- Poetry for dependency management
- Numpy ≥1.23.1
- PyTest for unit tests

## Library Design
OpenRarity consists of two core parts: **Runtime** and **Rarity Resolver**. The **Runtime** part of the library can be integrated into any Python 3.10+ application to perform the scoring of any collection. The runtime doesn’t resolve collections metadata—it’s the responsibility of an application to provide correct metadata to perform collection scoring.


## How to debug collections with OpenSea API data
To debug any collections scoring we built the **Rarity Resolver** tool. Follow these steps to score the collection with the tool (by calling OpenSea API):

- Curate the <a href="https://github.com/ProjectOpenSea/open-rarity/blob/main/open_rarity/data/test_collections.json" title=“Collections>collections list </a> you want to score with OpenRarity
- Provide your <a href="https://github.com/ProjectOpenSea/open-rarity/blob/main/open_rarity/resolver/opensea_api_helpers.py#L20"> OpenSea API Key </a>
- Run scoring for these collections with the following command:
    
    ```python
    python -m open_rarity.resolver.testset_resolver # without external rarity resolution
    python -m open_rarity.resolver.testset_resolver external # with external rarity resolution
    ```
- Inspect scorring log file and csv files with ranking result

## Running tests locally

- `pip install pytest`
- `pip install scipy`
- `python -m pytest <test_name>`


# Rarity Datasets

We are sharing collected rarity datasets along with the library code. These datasets are organized as a CSV file per collection. The schema of each CSV file provides ranks for three rarity providers collected via API (TraitsSniper, RaritySniper, RaritySniffer), OpenRarity methodologies and computed rank distance between OpenRarity and rarity providers ranks.

Use AWS CLI command to download rarity datasets locally:

```python
s3://jul27-openrarity/rarity-datasets . --recursive
```

# Contributions guide and governance

OpenRarity is a cross-company effort to improve rarity computation for NFTs (Non-Fungible Tokens). The core collaboration group consists of four primary contributors: Curio, Icy, OpenSea and Proof

OpenRarity is an open-source project and all contributions are welcome. Consider following steps when you request/propose contribution:

- Have a question? Submit it on OpenRarity GitHub  [discussions](https://github.com/ProjectOpenSea/open-rarity/discussions) page
- Create GitHub issue/bug with description of the problem [link](https://github.com/ProjectOpenSea/open-rarity/issues/new?assignees=impreso&labels=bug&template=bug_report.md&title=)
- Submit Pull Request with proposed changes
- To merge the change in the `main` branch you required to get at least 2 approvals from the project maintainer list
- Always add a unit test with your changes


# License

Apache 2.0 , OpenSea, ICY, Curio, PROOF




[license-badge]: https://img.shields.io/github/license/ProjectOpenSea/open-rarity
[license-link]: https://github.com/ProjectOpenSea/open-rarity/blob/main/LICENSE
[ci-badge]: https://github.com/ProjectOpenSea/open-rarity/actions/workflows/tests.yaml/badge.svg
[ci-link]: https://github.com/ProjectOpenSea/open-rarity/actions/workflows/tests.yaml
[version-badge]: https://img.shields.io/github/package-json/v/ProjectOpenSea/open-rarity
[version-link]: https://github.com/ProjectOpenSea/open-rarity/releases

