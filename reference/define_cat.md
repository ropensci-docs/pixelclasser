# Creates a category object

Creates an object of class `pixel_cat`, which contains a list of objects
of class `pixel_subcat`.

## Usage

``` r
define_cat(cat_name, cat_colour, ...)
```

## Arguments

- cat_name:

  a character string containing the name of the category.

- cat_colour:

  a character string defining the colour to paint the pixels with when
  creating a classified picture.

- ...:

  a list of `pixel_subcat` objects, or `pixel_rule` objects in case that
  subcategories are not needed. A mixed list of `pixel_rule` and
  `pixel_subcat` objects is not allowed.

## Value

A list of class `pixel_cat` with the following elements:

- `name`: a character string containing the name of the pixel category.

- `colour`: a character string describing the colour of the pixels of
  the category in the classified images.

- `subcats`: a list containing the subcategories. Their names are the
  names of the elements of the list.

## Details

The function receives a list of objects of class `pixel_subcat` and
creates a list of class `pixel_cat` with them. However, for cases that
does not need subcategories, i e that only need a set of rules,need a
single set of rules, these can be passed to the function, which creates
an internal subcategory object to contain them. See the examples below.

Note that it is an error to pass a mixture of `pixel_rule` and
`pixel_subcat` objects.

`colour` can be specified in any form understood by
`grDevices::col2grb`.

## See also

[`define_rule`](https://docs.ropensci.org/pixelclasser/reference/define_rule.md),
[`define_subcat`](https://docs.ropensci.org/pixelclasser/reference/define_subcat.md),
[`col2rgb`](https://rdrr.io/r/grDevices/col2rgb.html)

## Examples

``` r
# The rules are not consistent, they are only useful as examples
rule01 <- define_rule("R01", "g", "b",
                      list(c(0.35, 0.30), c(0.45, 0.10)), ">=")
rule02 <- define_rule("R02", "g", "b",
                      list(c(0.35, 0.253), c(0.45, 0.253)), ">=")
rule03 <- define_rule("R03", "g", "b",
                      list(c(0.35, 0.29), c(0.49, 0.178)), ">=")
rule04 <- define_rule("R04", "g", "b",
                      list(c(0.35, 0.253), c(0.45, 0.253)), "<")

subcat01 <- define_subcat("Subcat01", rule01, rule02)
subcat02 <- define_subcat("Subcat02", rule03, rule04)

cat01 <- define_cat("Cat01", "#ffae2a", subcat01, subcat02)

# A single category defined by a set of rules, not subcategories
cat02 <- define_cat("Cat02", "#00ae2a", rule01, rule02, rule03)
```
