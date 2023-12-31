# Details

## Input file detailed version and format
 >$ file DSC08317.ARW
 >DSC08317.ARW: TIFF image data, little-endian, direntries=19, compression=JPEG (old), 
 >description=                               , manufacturer=SONY, model=ILCE-6700, 
 >orientation=upper-left, xresolution=290, yresolution=298, resolutionunit=2, 
 >software=ILCE-6700 v1.00, datetime=2023:09:10 00:37:45

Extracting the embedded thumbnail works.
 >$ dcraw -e -c DSC08317.ARW | convert - DSC08317.jpg

TIFF works.
 >$ dcraw -T DSC08317.ARW

But file sile is too large, and color looks different. //TODO read usage

## Converters and results
Tools with a CLI interface are preferred.

### dcraw + imagemagick
dcraw version 9.28 + imagemagick convert version 6.9.10-23 Q16 -- doesn't work
 ```
 $ dcraw -c DSC08317.ARW | convert - DSC08317.JPG
 Cannot decode file DSC08317.ARW
 convert-im6.q16: no decode delegate for this image format ' @ error/constitute.c/ReadImage/572.
 convert-im6.q16: no images defined 'DSC08317.JPG' @ error/convert.c/ConvertImageCommand/3258.
 ```
### rawtherapee (rawtherapee-cli)
version 5.8 -- doesn't work
```
$ rawtherapee-cli -o outdir -c DSC08317.ARW
RawTherapee, version 5.8, command line.
Output is 8-bit integer.
Processing: DSC08317.ARW
Error loading file: DSC08317.ARW
```

### darktable (darktable.cli)
version 4.4.2 -- loads preview, but 
 ```
 failed to read camera white balance information
 'SONY ILCE-6700' color matrix not found for image
 ```
### exiftool
version 12.64 -- works but only preview
 ```
 exiftool -b -PreviewImage DSC08317.ARW > DSC08317.JPG 
 ```
As exiftool works with preivews, the resolution is smaller (1080 vs 4k). This is enough to show pictures on Mac and iPhone. The original RAW file is preserved after import/export. File checksums are identical before and after import/export.
