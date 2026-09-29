# Classifies the pixels of an image

Classifies the pixels represented in an object of class
`transformed_image` using the rules contained in a list of objects of
class `pixel_cat`.

## Usage

``` r
classify_pixels(image_prop, ..., unclassed_colour = "black", verbose = TRUE)
```

## Arguments

- image_prop:

  an array containing the image. It must be an object produced with
  function
  [`read_image()`](https://docs.ropensci.org/pixelclasser/reference/read_image.md).

- ...:

  a list of objects of class `pixel_cat` containing the classification
  rules.

- unclassed_colour:

  a character string setting the colour to be assigned to unclassified
  pixels. Defaults to "black".

- verbose:

  a logical value. When TRUE (default) the function prints some
  statistics about the classification.

## Value

Returns an object of class `classified_image`, which is a list
containing nested lists. Each first-level element corresponds to one of
the pixel categories and its name is the category name. They contains
the second-level list, which have the following elements:

- `colour`: a matrix defining a colour to paint the pixels in the
  classified image. Inherited from the `pixel_class` object defining the
  class.

- `incid_mat`: a logical matrix where `TRUE` values indicate that the
  pixel belongs to this pixel category.

## Details

This function generates a set of incidence matrices indicating whether a
pixel belongs to a pixel category or not. An additional matrix
identifies the pixels that do not belong to the defined categories, i e
unclassed pixels. Depending on how the rules were defined, it can be
void or contain pixels, but it is always present and named
`unclassified`.

To create the incidence matrices for each category, a matrix for each
rule is created and then combined with the matrices of the other using
the `and` operator.

When a set of subcategories is used, the procedure is the same for each
subcategory and then the matrices of the subcategories are combined
again, this time using the `or` operator. See the help for
`define_subcat` for more details.

`unclassed_colour` can be specified in any form understood by
`grDevices::col2grb`.

## See also

[`define_cat`](https://docs.ropensci.org/pixelclasser/reference/define_cat.md),
[`col2rgb`](https://rdrr.io/r/grDevices/col2rgb.html).

## Examples

``` r

# The series of steps to classify a image supplied in the package

yellow <- "#ffcd0eff"
blue <- "#5536ffff"

ivy_oak_rgb <- read_image(system.file("extdata", "IvyOak400x300.JPG",
                          package = "pixelclasser"))

rule_01 <- define_rule("rule_01", "g", "b",
                       list(c(0.345, 1/3), c(0.40, 0.10)), comp_op = "<")
rule_02 <- define_rule("rule_02", "g", "b",
                       list(c(0.345, 1/3), c(0.40, 0.10)), comp_op = ">=")

cat_dead_leaves <- define_cat("dead_leaves", blue, rule_01)
cat_living_leaves <- define_cat("living_leaves", yellow, rule_02)

ivy_oak_classified <- classify_pixels(ivy_oak_rgb, cat_dead_leaves,
                        cat_living_leaves)
#> Pixels in category dead_leaves: 80718
#> Pixels in category living_leaves: 39282
#> Pixels in category unclassified: 0
#> Duplicate pixels: 0 
#> Total number of pixels: 120000 
```
