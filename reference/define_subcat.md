# Creates a subcategory object

Creates an object of class `pixel_subcat` from a list of objects of
class `pixel_rule`.

## Usage

``` r
define_subcat(subcat_name, ...)
```

## Arguments

- subcat_name:

  a character string containing the name of the subcategory.

- ...:

  a list of objects of class `pixel_rule`.

## Value

An object of class `pixel_subcat`, which is a list with the following
elements:

- `name` a character string containing the name of the subcategory.

- `rules_list` a list of `pixel_rule` objects.

## Details

When the shape of the cluster of pixels belonging to one category is not
convex, the rules become inconsistent (the lines cross in awkward ways)
and the classification produced is erroneous. To solve this problem, the
complete set of rules is divided into several subsets (subcategories)
that break the original non-convex shape into a set of convex polygons.
Note that any polygon can be divided in a number of triangles, so this
problem always has solution. However, in many cases (such as the one
presented in the pixelclasser vignette) a complete triangulation is not
needed.

Internally,
[`classify_pixels()`](https://docs.ropensci.org/pixelclasser/reference/classify_pixels.md)
classifies the points belonging to each subcategory and then joins the
incidence matrices using the `or` operator, to create the matrix for the
whole category.

## See also

[`define_rule`](https://docs.ropensci.org/pixelclasser/reference/define_rule.md),
[`define_cat`](https://docs.ropensci.org/pixelclasser/reference/define_cat.md)

## Examples

``` r
rule01 <- define_rule("R01", "g", "b",
                      list(c(0.35, 0.30), c(0.45, 0.10)), ">=")
rule02 <- define_rule("R02", "g", "b",
                      list(c(0.35, 0.253), c(0.45, 0.253)), ">=")

subcat01 <- define_subcat("Subcat_01", rule01, rule02)
```
