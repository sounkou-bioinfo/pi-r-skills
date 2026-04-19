# R Package Workflow Reference

## Inspect package metadata

```bash
Rscript -e 'read.dcf("DESCRIPTION")'
Rscript -e 'packageVersion("pkgname")'
```

## Useful usethis helpers

```bash
Rscript -e 'usethis::use_package_doc()'
Rscript -e 'usethis::use_lifecycle_badge("experimental")'
Rscript -e 'usethis::use_news_md()'
Rscript -e 'usethis::use_github_action_check_standard()'
Rscript -e 'usethis::use_coverage()'
Rscript -e 'usethis::use_cran_comments()'
Rscript -e 'usethis::use_git_ignore(c(".Rproj.user", ".Rhistory", ".Rdata"))'
Rscript -e 'usethis::use_build_ignore(c("^.*\\.tar\\.gz$", "^.*\\.Rcheck$"))'
```

## Common make/base-R commands

```bash
make rd
make dev-install
make test
make build
make check

R -e 'roxygen2::roxygenize(load_code = "source")'
R CMD INSTALL --preclean .
R -e "tinytest::test_package('pkgname', testdir = 'inst/tinytest')"
R CMD build .
R CMD check *.tar.gz
```

## roxygen2 tags often used

- `@export`
- `@param`
- `@returns` or `@return`
- `@examples`
- `@seealso`
- `@inheritParams`
- `@importFrom pkg fun`
- `@family`

Guideline: update roxygen in `R/*.R`, then regenerate. Never hand-edit generated `NAMESPACE` or `.Rd` files.

## Native-code naming convention

- Prefix C functions that touch the R C API or are exported to `.Call` with `RC_`
- Keep the convention consistent across C source, headers, registration, and R wrappers

## Typical package layout

```text
DESCRIPTION
NAMESPACE
Makefile
R/
man/
inst/tinytest/
tests/tinytest.R
vignettes/
README.Rmd
_pkgdown.yml
```

## NEWS.md guidance

- Keep newest changes first
- Add new bullets at the top
- Prefer user-facing wording over internal implementation detail

## CI-friendly sequence

```bash
make rd
make dev-install
make test
make check
```
