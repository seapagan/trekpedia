# Trekpedia JSON

<!-- TOC start -->
- [Trekpedia JSON](#trekpedia-json)
  - [Development](#development)
    - [Current progress](#current-progress)
  - [Produced Files](#produced-files)
  - [Operation](#operation)
  - [Current known BUGS](#current-known-bugs)
  - [Further Enhancements planned](#further-enhancements-planned)
<!-- TOC end -->

Star Trek TV/Film episode database scraped from web sources and provided in JSON
format.

This geek project is just for me to get familiar with Python web-scraping and
provide data for API development.

For an API specifically written to use this data, see
[trekpedia-api-rails][trekpedia-api-rails] (work in progress)

All copyright to the 'Star Trek' name and data belongs to
[ViacomCBS][viacomcbs].

All data in this project is mined live from the [Wikipedia Star Trek page][wst]
and associated subpages under the [Fair Use][fup] principal.

The license below only applies to the **SOURCE CODE**.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## Development

Initially, I carried out the development of the scraper using [Jupyter
Notebooks][jupyter]. These are depreciated and archived in the `notebooks`
folder.

I have migrated this base work into pure Python, where all further development
will remain.

### Current progress

I am only scraping the TV series data, leaving film data until later iterations.

There are currently two stages of operation:

- Scrape the main Wikipedia Star Trek page and create a JSON file containing
  Series names and metadata (number of seasons, number of episodes, etc.). This
  metadata will probably include a series summary and other data in future
  iterations (not necessarily from Wikipedia)

- Take the JSON file created in the previous step, and dump the episode names
  for each series to a separate JSON file, with some Series metadata
  - There is a bug where the script will not parse any series with only one
    season due to the lack of a summary table.

## Produced Files

A current version of the derived data is available in the [output](output)
directory, valid as of June 2022.

This directory contains the following GENERATED files:

- The file [star_trek_series_info.json](output/star_trek_series_info.json) lists
  info and links for each series. This file was previously required as input to
  the Stage 2 notebook but not needed for the current scripts. However,
  it does contain Series metadata that is useful when generating an API, for
  example.
- A Separate JSON file for each Star Trek series, 12 to date.

A tarball is included in the [releases](releases) folder and attached to each
GitHub release.

## Operation

Clone or download the repository, then run the main script from the root of the
created folder.

```python
python generate_trek.py
```

The updated files will be created in the output folder, overwriting existing
ones.

## Current known BUGS

- ~~Single-season Series currently won't be decoded; [issue #7][i7] is open for
  this.~~
- There is no detection of two-part episodes **written as a single entry**, so
  the numbering is a little wrong when we parse them. I will look at fixing this
  when the main functionality is bug-free.

## Further Enhancements planned

- A list of Star Trek characters [here][st-char] can also be parsed and linked
to the relevant series/season/episode data.
- Add a brief series and episode summary.

[viacomcbs]:https://www.viacomcbs.com
[wst]: https://en.wikipedia.org/wiki/Star_Trek
[st-char]: https://en.wikipedia.org/wiki/List_of_Star_Trek_characters
[fup]: https://en.wikipedia.org/wiki/Fair_use#Text_and_data_mining
[jupyter]: https://jupyter.org/
[trekpedia-api-rails]: https://github.com/gnramsay/trekpedia-api-rails

[i7]: https://github.com/gnramsay/trekpedia/issues/7
