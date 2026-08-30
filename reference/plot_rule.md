# Plots the line that defines a rule

This function draws the line that defines a rule on the plot created by
[`plot_rgb_plane()`](https://docs.ropensci.org/pixelclasser/reference/plot_rgb_plane.md).

## Usage

``` r
plot_rule(rule, label = "", ...)
```

## Arguments

- rule:

  an object of class `pixel_rule` produced by
  [`define_rule()`](https://docs.ropensci.org/pixelclasser/reference/define_rule.md).

- label:

  a string to label the line. It is attached at the coordinates of the
  second point used to define the line.

- ...:

  additional graphical parameters passed to the underlying
  [`lines()`](https://rdrr.io/r/graphics/lines.html) function, for
  example to define the line colour or dashing style. They are also used
  for the line label.

## Value

The function does not return any value.

## Details

The function uses the information stored in the `pixel_rule object` to
plot the line.

Use the ... to set the colour and other characteristics of the line. Use
any character string understood by
[`col2rgb()`](https://rdrr.io/r/grDevices/col2rgb.html).

Labels can be added to the rule using
[`label_rule()`](https://docs.ropensci.org/pixelclasser/reference/label_rule.md).

## See also

[`plot_rgb_plane`](https://docs.ropensci.org/pixelclasser/reference/plot_rgb_plane.md),
[`define_rule`](https://docs.ropensci.org/pixelclasser/reference/define_rule.md),
[`label_rule`](https://docs.ropensci.org/pixelclasser/reference/label_rule.md)
[`col2rgb`](https://rdrr.io/r/grDevices/col2rgb.html)

## Examples

``` r
rule_01 <- define_rule("rule_01", "g", "b",
                      list(c(0.345, 1/3), c(0.40, 0.10)), "<")

plot_rgb_plane("g", "b")
plot_rule(rule_01, col = "green")

```
