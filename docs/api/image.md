# Image

In atom-shell images are represented by their file paths, we currently do not
support in-memory images or remote images.

For example when creating tray or setting window's icon, you can pass image's
file path as `String` to represent an image:

```javascript
var appIcon = new Tray('/Users/somebody/images/icon.png');
var window = new BrowserWindow({icon: '/Users/somebody/images/window.png'});
```

## Supported formats

On Mac all formats supported by the system can be used, while on Linux and
Windows only `PNG` and `JPG` formats are supported.

So it is recommended to use `PNG` images for all cases.

## High resolution image

On platforms that have high-DPI support, you can append `@2x` after image's
file name's base name to mark it as a high resolution image.

For example if `icon.png` is a normal image that has standard resolution, the
`icon@2x.png` would be treated as a high resolution image that has double DPI
dense.

If you want to support displays with different DPI denses at the same time, you
can put images with different sizes in the same folder, and use the filename
without DPI suffixes, like this:

```text
images/
├── icon.png
├── icon@2x.png
└── icon@3x.png
```


```javascript
var appIcon = new Tray('/Users/somebody/images/icon.png');
```

Following suffixes as DPI denses are also supported:

* `@1x`
* `@1.25x`
* `@1.33x`
* `@1.4x`
* `@1.5x`
* `@1.8x`
* `@2x`
* `@2.5x`
* `@3x`
* `@4x`
* `@5x`

## Template image

Template images consist of black and clear colors (and an alpha channel).
Template images are not intended to be used as standalone images and are usually
mixed with other content to create the desired final appearance.

The most common case is to use template image for menu bar icon so it can adapt
to both light and dark menu bars.

Template image is only supported on Mac.

To mark an image as template image, its filename should end with the word
`Template`, examples are:

* `xxxTemplate.png`
* `xxxTemplate@2x.png`
