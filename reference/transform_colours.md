# Transforms RGB values into proportions (rgb values)

This function transforms an array of RGB absolute values into a similar
array containing the proportion of each band (= colour variable): r g
and b.

## Usage

``` r
transform_colours(image_array)
```

## Arguments

- image_array:

  an array of class `image_array` created by function
  [`read_image()`](https://docs.ropensci.org/pixelclasser/reference/read_image.md).

## Value

Returns an array of class `transformed_image` containing the proportions
of each colour variable in the pixels of the image. The third dimension
of the array is named "bands" and its elements are labelled as "r", "g"
and "b", respectively.

## Details

The proportions are calculated as `r` = `R` / (`R + G + B`), and so on.
It is used by function read_image().
