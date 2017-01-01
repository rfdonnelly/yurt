# YURT 1            2016-12-31      0.1

## NAME

yurt - YAML-Ruby template renderer

## SYNOPSIS

`yurt` [*OPTION*]... [*FILE*]

## DESCRIPTION

An ERB template renderer with YAML/JSON data source and easy regeneration.

### Templates

Templates are written using [ERB](https://en.wikipedia.org/wiki/ERuby).

### Data Source

Data can be sourced from a YAML/JSON file or string.  This data can be used in
the template.

### Regeneration

Output can be easily regenerated with the `--regen` option.  Templates must
include the `<%= generate_comment %>` somewhere in the first line of the
template.

Template (`template.erb`) contents:

```ruby
# <%= generate_comment =>
...
```

Initial generation:

```sh
yurt --data data.yml template.erb --output output
```

Subsequent generation:

```sh
yurt --regen output
```

## OPTIONS

`--data` *file.yml*|*YAML-string*
  Data is YAML or JSON format as a file or a string.

`--require` *path*
  Require one or more Ruby files.

`--output` *output-file*
  Write output to *output-file* instead of STDOUT.  Used by the regen feature.

`--regen` *output-file*
  Regenerate *output-file*.
