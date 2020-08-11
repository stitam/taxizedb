taxizedb
========



[![cran checks](https://cranchecks.info/badges/worst/taxizedb)](https://cranchecks.info/pkgs/taxizedb)
[![Build Status](https://travis-ci.org/ropensci/taxizedb.svg?branch=master)](https://travis-ci.org/ropensci/taxizedb)
[![codecov](https://codecov.io/gh/ropensci/taxizedb/branch/master/graph/badge.svg)](https://codecov.io/gh/ropensci/taxizedb)
[![rstudio mirror downloads](http://cranlogs.r-pkg.org/badges/taxizedb)](https://github.com/metacran/cranlogs.app)
[![cran version](https://www.r-pkg.org/badges/version/taxizedb)](https://cran.r-project.org/package=taxizedb)
[![DOI](https://zenodo.org/badge/53961466.svg)](https://zenodo.org/badge/latestdoi/53961466)

`taxizedb` - Tools for Working with Taxonomic Databases on your Machine

[taxize](https://github.com/ropensci/taxize) is a heavily used taxonomic toolbelt
package in R - However, it makes web requests for nearly all methods. That is fine
for most cases, but when the user has many, many names it is much more efficient
to do requests to a local SQL database.

Not all taxonomic databases are publicly available, or possible to mash into a SQLized
version. Taxonomic DB's supported thus far:

- NCBI: text files are provided by NCBI, which we stitch into a sqlite db
- ITIS: they provide a sqlite dump, which we use here
- The PlantList: created from stitching together csv files. this
 source is no longer updated as far as we can tell. they say they've
 moved focus to the World Flora Online
- Catalogue of Life: created from Darwin Core Archive dump.
- GBIF: created from Darwin Core Archive dump. right now we only have
 the taxonomy table (called gbif), but will add the other tables in the
 darwin core archive later
- Wikidata: aggregated taxonomy of Open Tree of Life, GLoBI and Wikidata. 
 On Zenodo, created by Joritt Poelen of GLOBI.

Update schedule for databases:

- NCBI: since `db_download_ncbi` creates the database when the function
 is called, it's updated whenever you run the function
- ITIS: since ITIS provides the sqlite database as a download, you can
 delete the old file and run `db_download_itis` to get a new dump;
 they I think update the dumps every month or so
- The PlantList: no longer updated, so you shouldn't need to download
 this after the first download
- Catalogue of Life: we have a script that we run on a server once
 per month to stitch together the sqlite database from the DCA, so
 updated once per month, but we're not sure how frequently COL updates
 their DCA dumps
- GBIF: we have a script that we run on a server once
 per month to stitch together the sqlite database from the DCA, so
 updated once per month, but we're not sure how frequently GBIF updates
 their DCA dumps
- Wikidata: last updated April 6, 2018. Scripts are available to 
 update the data if you prefer to do it yourself.

 Links:

- NCBI: ftp://ftp.ncbi.nih.gov/pub/taxonomy/
- ITIS: https://www.itis.gov/downloads/index.html
- The PlantList - http://www.theplantlist.org/
- Catalogue of Life:
   via http://www.catalogueoflife.org/content/annual-checklist-archive
- GBIF: http://rs.gbif.org/datasets/backbone/
- Wikidata: https://zenodo.org/record/1213477

Get in touch [in the issues](https://github.com/ropensci/taxizedb/issues) with
any ideas on new data sources.

This package for each data sources performs the following tasks:

* Download database - `db_download_*`
* Create `dplyr` SQL backend - `src_*`

All databases are SQLite.

Using the src connection, use `dplyr`, etc. to do operations downstream. Or create
your own database connection to the sqlite file.

## install

cran version


```r
install.packages("taxizedb")
```

dev version


```r
remotes::install_github("ropensci/taxizedb")
```

## Contributors

* [Scott Chamberlain](https://github.com/sckott)
* [Zebulun Arendsee](https://github.com/arendsee)
* [Tamora James](https://github.com/tdjames1)


## Meta

* Please [report any issues or bugs](https://github.com/ropensci/taxizedb/issues).
* License: MIT
* Get citation information for `taxizedb` in R doing `citation(package = 'taxizedb')`
* Please note that this package is released with a [Contributor Code of Conduct](https://ropensci.org/code-of-conduct/). By contributing to this project, you agree to abide by its terms.

[![ropensci](https://ropensci.org/public_images/github_footer.png)](https://ropensci.org)
