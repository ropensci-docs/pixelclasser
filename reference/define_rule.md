# Creates a rule object

Creates an object of class `pixel_rule` from a line in `rgb` space,
defined by the user, and a relational operator.

## Usage

``` r
define_rule(rule_name, x_axis, y_axis, rule_points, comp_op)
```

## Arguments

- rule_name:

  a character string containing the name of the rule.

- x_axis:

  a character string selecting the colour variable used as x axis, one
  of `"r"`, `"g"` or `"b"`.

- y_axis:

  a character string selecting the colour variable used as y axis, one
  of `"r"`, `"g"` or `"b"`.

- rule_points:

  either an object of of class `"rule_points"` created with function
  [`place_rule()`](https://docs.ropensci.org/pixelclasser/reference/place_rule.md),
  or a list containing the coordinates of two points defining the line.

- comp_op:

  a character string containing one of the comparison operators
  `">", ">=", "<", "<="`.

## Value

A list of class `pixel_rule` containing the following elements:

- `rule_name`: a character string containing the rule name.

- `rule_text`: a character string containing the mathematical expression
  of the rule.

- `comp_op`: a character string containing the comparison operator used
  in the rule.

- `a`: a numerical vector containing the parameter `a` (slope) of the
  line.

- `c`: a numerical vector containing the parameter `c` (intercept) of
  the line.

- `x_axis`: a character string containing the colour variable selected
  as `x` axis.

- `y_axis`: a character string containing the colour variable selected
  as `y` axis.

- `first_point`: a numerical vector containing the coordinates of the
  first point used to estimate the line equation.

- `second_point`: a numerical vector containing the coordinates of the
  second point.

## Details

This function estimates the slope (`a`) and intercept (`c`) of the line
`y = ax + c` using the coordinates of two points on the line. `x` and
`y` are two colour variables selected by the user (`r`, `g`, or `b`).
The line divides the plane in two subsets and the comparison operator
selects the subset that contains the points (pixels) of interest.

When a list of two points is passed in `rule_points`, it is internally
converted into an an object of class `rule_points`.

The pair of points used to define the line are not constrained to belong
to the area occupied by the pixels, but they are used by
[`plot_rule()`](https://docs.ropensci.org/pixelclasser/reference/plot_rule.md)
as the start and end of the plotted line. Therefore, the extremes of the
line can be selected in the most convenient way, provided that the line
divides correctly the categories. Convenience means that the line should
seem nice in the plot, if this matters.

Because the variables were transformed into proportions, the pixel are
always inside the triangle defined by the points
`(0, 0), (1, 0), (0, 1)`. So, the sides of this triangle can be
considered as implicit rules which do not need to be created. In this
way, a single line creates two polygons by cutting the triangle in two.
The implicit rules can reduce the number of rules to create in most
cases.

## See also

[`define_subcat`](https://docs.ropensci.org/pixelclasser/reference/define_subcat.md),
[`define_cat`](https://docs.ropensci.org/pixelclasser/reference/define_cat.md),
[`plot_rule`](https://docs.ropensci.org/pixelclasser/reference/plot_rule.md),
[`plot_rgb_plane`](https://docs.ropensci.org/pixelclasser/reference/plot_rgb_plane.md)

## Examples

``` r
# Creating the line by passing the coordinates of two points on the line:
rule01 <- define_rule("rule01", "g", "b",
                      list(c(0.35, 0.30), c(0.45, 0.10)),">")

# A vertical line as a rule; note that the equation is simplified
rule02 <- define_rule("rule02", "g", "b",
                      list(c(0.35, 0.30), c(0.35, 0.00)), ">")
if (FALSE) { # \dontrun{
# Creating the rule by passing an object of type rule_point:
rule_points01 <- place_rule("g", "b")
rule03 <- define_rule("rule03", "g", "b", rule_points01,">")

# Note that the creation of the intermediate object can be avoided:
rule04 <- define_rule("rule04", "g", "b", place_rule("g", "b"),">")
} # }
```
