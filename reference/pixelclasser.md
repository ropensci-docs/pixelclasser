# pixelclasser: Functions to classify pixels by colour

`pixelclasser` contains functions to classify the pixels of an image
file (in format jpeg or tiff) by its colour. It uses a simple form of
the technique known as Support Vector Machine, adapted to this
particular problem. The original colour variables (`R, G, B`) are
transformed into colour proportions (`r, g, b`), and the resulting two
dimensional plane, defined by any convenient pair of the transformed
variables is divided in several subsets (categories) by one or more
straight lines (rules) selected by the user. Finally, the pixels
belonging to each category are identified using the rules, and a
classified image can be created and saved.

## Details

To classify the pixels of an image, a series of steps must be done in
the following order, using the functions shown in parenthesis:

- import the image into an R array of transformed (`rgb`) data
  ([`read_image()`](https://docs.ropensci.org/pixelclasser/reference/read_image.md)).

- plot the pixels of the image on the plane of two transformed variables
  that shows the categories of pixels most clearly
  ([`plot_rgb_plane()`](https://docs.ropensci.org/pixelclasser/reference/plot_rgb_plane.md),
  `plot_pixels`).

- trace lines between the pixel clusters and use them to create
  classification rules
  ([`place_rule()`](https://docs.ropensci.org/pixelclasser/reference/place_rule.md),
  `define_rule`,
  [`plot_rule()`](https://docs.ropensci.org/pixelclasser/reference/plot_rule.md)).

- combine the rules to define categories. Sometimes the rules are
  combined into subcategories and these into categories
  ([`define_cat()`](https://docs.ropensci.org/pixelclasser/reference/define_cat.md),
  [`define_subcat()`](https://docs.ropensci.org/pixelclasser/reference/define_subcat.md)).

- use the categories to classify the pixels
  ([`classify_pixels()`](https://docs.ropensci.org/pixelclasser/reference/classify_pixels.md)).

- save the results of the classification as an image, if needed
  (`save_clasif_image()`).

These steps are explained in depth in the vignette included in the
package.

## Author

Carlos Real (carlos.real@usc.es)
