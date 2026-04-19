# pi-r-skills

Pi skills for R package development.

## Install

```bash
pi install git:github.com/sounkou-bioinfo/pi-r-skills
```

## Included skills

- `r-package-development`
- `s7-development`
- `duckhts-development`

## When to use `duckhts-development`

Load `duckhts-development` when you are:

- working in `RGenomicsETL/duckhts`
- changing DuckDB extension code under `src/`
- changing the bundled R package under `r/Rduckhts/`
- adding public functions that require `functions.yaml`, SQL tests, and tinytests
- touching wasm/webR build logic
- porting existing genomics tools into DuckHTS with exact-compatibility goals

## When to use `s7-development`

Load `s7-development` when you are:

- defining S7 classes with `S7::new_class()`
- defining S7 generics or methods with `S7::new_generic()` and `S7::method()`
- writing validators, properties, getters, or setters
- integrating S7 into an R package
- dealing with S3/S4 compatibility or migration toward S7
- debugging package issues around method registration, collation order, or S7 documentation

## Development

This repo is a Pi package. Pi auto-loads skills from `skills/`, and `package.json` declares the package explicitly under the `pi` key.
