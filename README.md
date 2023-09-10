# SONY RAW Image Support for MacOSX Photos Application
Apples `Photos` app doesn't have good support for pictures taken by SONY cameras in RAW format. This is true at least for the following combination. 

* MacOSX 13.4.1 (c) 
* Photos Version 8.0 (551.0.140)
* SONY A6700

This repo provides a simple workaround, which will no longer be needed when Apple fixs the bug. However, if you are curious and don't want to depend on others schedule, keep reading.

# Bug Description
`Photos` app on MacOSX and its cloud counterparts on iPhones don't display RAW images properly. A blank image is displayed instead. 

| ![image](https://github.com/lqu/macsonyraw/assets/432856/482fa5d2-c373-41b9-b1db-67d7c90a644c) |
|:--:| 
| *after import* |


The pictures can be imported from SD cards to the `Photos` app without any problem. In the preview before the import, the thumbnails of the RAW images are displayed correctly. This indicates Apple does support RAW format and `Photos` app knows how to read and display RAW images. So I consider this a bug (either SONY or Apple, or both) , instead of lack of features. 

| ![image](https://github.com/lqu/macsonyraw/assets/432856/0ed6ec07-c6a1-48d1-bdfa-f3e2562fdaf4) |
|:--:| 
| *preview before import* |


# Troubleshooting
SONY cameras provides 3 options when saving pictures - RAW, JPEG, and RAW+JPEG. Only RAW has problems. Further examination shows RAW+JPEG format is just the same picture saved twice, with the same filename but different extensions, for instance, DSC0012.jpg and DSC0012.arw. `Photos` app knows how to handle this.


# Solution
1. Configure your camera to use RAW+JPEG format to save pictures; or
2. Convert RAW images into RAW+JPEG fomrat by augmenting it with JPEG

```
exiftool -b -PreviewImage DSC08317.ARW > DSC08317.JPG 
```
[[troubleshooting.md]
](https://github.com/lqu/macsonyraw/blob/main/troubleshooting.md#exiftool)https://github.com/lqu/macsonyraw/blob/main/troubleshooting.md#exiftool
