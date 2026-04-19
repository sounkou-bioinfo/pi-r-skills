# Formatting and Linting

`air` and `jarl` are good optional additions to an R package workflow when the project wants fast, editor-friendly formatting and linting without changing its core build/test/release flow.

## air

Use `air` for code formatting.

Typical command:

```bash
air format R/ tests/ inst/tinytest/
```

Use it when:

- the repository wants a consistent formatter
- you want editor and CLI formatting with the same tool
- you want a fast formatter outside the R session

## jarl

Use `jarl` for static linting.

Typical commands:

```bash
jarl check R/ tests/ inst/tinytest/
jarl check R/ tests/ inst/tinytest/ --fix
```

Use it when:

- you want fast linting in CI or pre-commit hooks
- you want automatic fixes for some lint rules
- you want an alternative or complement to `lintr`

## Workflow position

Treat formatting/linting as complements to the package's native workflow, not replacements for:

- `make rd`
- `make test`
- `R CMD build`
- `R CMD check`

A practical sequence is:

```bash
air format R/ tests/ inst/tinytest/
jarl check R/ tests/ inst/tinytest/
make rd
make test
make check
```

If a repository already uses `styler`, `lintr`, or another formatting/linting setup, prefer the existing project convention unless asked to switch.
