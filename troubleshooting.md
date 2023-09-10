# Details

## Input file detailed version and format
 >$ file DSC08317.ARW
 >DSC08317.ARW: TIFF image data, little-endian, direntries=19, compression=JPEG (old), 
 >description=                               , manufacturer=SONY, model=ILCE-6700, 
 >orientation=upper-left, xresolution=290, yresolution=298, resolutionunit=2, 
 >software=ILCE-6700 v1.00, datetime=2023:09:10 00:37:45

## Converters and results
Tools with a CLI interface are preferred.

### dcraw
version 9.28 -- doesn't work
 >$ dcraw -c DSC08317.ARW | convert - DSC08317.JPG
 >Cannot decode file DSC08317.ARW
 >convert-im6.q16: no decode delegate for this image format `' @ error/constitute.c/ReadImage/572.
 >convert-im6.q16: no images defined `DSC08317.JPG' @ error/convert.c/ConvertImageCommand/3258.

### rawtherapee (rawtherapee-cli)
version 5.8 -- doesn't work
 >"Processing: DSC....ARW
 >Error loading file: DSC....ARW"

### darktable (darktable.cli)
version 4.4.2 -- loads preview, but "failed to read camera white balance information"
 >'SONY ILCE-6700' color matrix not found for image
