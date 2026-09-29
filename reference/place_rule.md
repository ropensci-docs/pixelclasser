# Places a line on the rgb plot

A wrapper function for
[`graphics::locator`](https://rdrr.io/r/graphics/locator.html) that
makes the creation of rules easier.

## Usage

``` r
place_rule(x_axis, y_axis, line_type = "f")
```

## Arguments

- x_axis:

  a character string indicating the colour variable that corresponds to
  the x axis, one of `"r"`, `"g"` or `"b"`.

- y_axis:

  a character string indicating the colour variable that corresponds to
  the y axis, one of `"r"`, `"g"` or `"b"`.

- line_type:

  a character string indicating that the line is vertical `"v"`,
  horizontal `"h"` or free (`"f"`, the default).

## Value

A list of class `rule_points` containing the following elements:

- `x_axis`: a character string containing the colour variable selected
  as `x` axis.

- `y_axis`: a character string containing the colour variable selected
  as `y` axis.

- `first_point`: coordinates of the start point of the line.

- `second_point`: coordinates of the end point of the line.

## Details

This function calls
[`graphics::locator`](https://rdrr.io/r/graphics/locator.html) allowing
to select two points, plots the line joining these points and returns a
list containing their coordinates. The coordinates are rearranged to
pass them to
[`define_rule()`](https://docs.ropensci.org/pixelclasser/reference/define_rule.md).

True horizontal and vertical lines are difficult to create by hand. In
these cases, specifying `"vertical"` or `"horizontal"` (partial match
allowed, i e "h") will copy the appropriate coordinate value from the
first point to the second. Note that this is done after
[`locator()`](https://rdrr.io/r/graphics/locator.html) returns, so the
plot will show the line joining the original points, not the corrected
ones. Use
[`plot_rule()`](https://docs.ropensci.org/pixelclasser/reference/plot_rule.md)
to see corrected line.

## See also

[`locator`](https://rdrr.io/r/graphics/locator.html),
[`define_rule`](https://docs.ropensci.org/pixelclasser/reference/define_rule.md),
[`plot_rule`](https://docs.ropensci.org/pixelclasser/reference/plot_rule.md),
[`plot_rgb_plane`](https://docs.ropensci.org/pixelclasser/reference/plot_rgb_plane.md)

## Examples

``` r
if (FALSE) { # \dontrun{
plot_rgb_plane("r", "g")
line01 <- place_rule("r", "g")          # A "free" line
line02 <- place_rule("r", "g", "h")     # A horizontal line
} # }
```
