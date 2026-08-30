# Saves a classified image in TIFF or JPEG format

Creates an image file in TIFF or JPEG format from an array of class
`classified_image`.

## Usage

``` r
save_classif_image(classified_image, file_name, ...)
```

## Arguments

- classified_image:

  an object of class `classified_image`.

- file_name:

  a character string with the name of the output file, including the
  extension.

- ...:

  further parameters to pass to functions `writeJPG` and `writeTIFF`. If
  void, the default values of these functions are used.

## Value

It does not return anything, only creates the file.

## Details

The type of the output file (jpeg or tiff) is selected from the
extension included in the file name. It must be one of
`("jpg", "JPG", "jpeg", "JPEG", "tif", "TIF", "tiff", "TIFF")`.

Note that the default value for jpg quality is 0.7. For maximal quality
set `quality = 1` using the ... argument. Such adjustments are not
needed with `tiff` files, as this is a lossless format.

## See also

[`classify_pixels`](https://docs.ropensci.org/pixelclasser/reference/classify_pixels.md)

For more information about the options for file formatting see see the
help pages of [`readJPEG`](https://rdrr.io/pkg/jpeg/man/readJPEG.html)
and [`readTIFF`](https://rdrr.io/pkg/tiff/man/readTIFF.html) functions
in packages `jpeg` and `tiff`, respectively.

## Examples

``` r
if (FALSE) { # \dontrun{

# Saving an hypothetical image. Note the use of quality to set the
# maximum quality level in the JPEG file
save_classif_image(image01_class, "./myimages/image01_classified.jpg",
                   quality = 1)
} # }
```
