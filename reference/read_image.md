# Imports a jpg or tiff file.

Imports an image file (in JPEG or TIFF format) into an array, and
converts the original `R`, `G` and `B` values in the file into
proportions (`r`, `g` and `b` variables).

## Usage

``` r
read_image(file_name)
```

## Arguments

- file_name:

  A character string containing the name of the image file.

## Value

Returns an array of dimensions `r x c x 3` and class
`transformed_image`, being `r` and `c` the number of rows and columns in
the image. The last dimension corresponds to the `R`, `G` and `B`
variables (= bands) that define the colours of the pixels. The values in
the array are the proportions of each colour (`r, g, b`), i.e. `r` = `R`
/ (`R + G + B`), and so on.

## Details

This function calls the functions `readJPEG()` and `readTIFF()` in
packages `jpeg` and `tiff` to import the data into an R array. Then it
transforms the data into proportions

## See also

For more information about jpeg and tiff file formats, see the help
pages of [`readJPEG`](https://rdrr.io/pkg/jpeg/man/readJPEG.html) and
[`readTIFF`](https://rdrr.io/pkg/tiff/man/readTIFF.html) functions in
packages `jpeg` and `tiff`, respectively.

## Examples

``` r

# An example that loads the example file included in the package
ivy_oak_rgb <- read_image(system.file("extdata", "IvyOak400x300.JPG", 
                                       package = "pixelclasser"))
```
