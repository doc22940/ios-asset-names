# Guide for Naming Assets in iOS Projects

This guide outlines best practices and [naming conventions](#naming) to help graphic designers and developers manage a large number of icons prepared for an iOS project. 

Your input is welcome: [issues](https://github.com/dkhamsing/ios-asset-names/issues), [pull requests](https://github.com/dkhamsing/ios-asset-names/pulls), or [twitter](https://twitter.com/dkhamsing).

## Table Of Contents
* [Folders](#folders)
* [Asset Type](#asset-type)
* [Naming](#naming)
	* [Uniqueness](#uniqueness)
	* [Prefixing](#prefixing)
	* [Conventions](#conventions)
	* [Special cases](#special-cases)
	* [Collisions](#collisions)
	* [Spelling](#spelling)
	* [Abbreviations](#abbreviations)
* [Acknowledgment](#acknowledgment)


## Folders

* If you are using [Asset Catalogs](https://developer.apple.com/library/ios/recipes/xcode_help-image_catalog-1.0/Recipe.html) introduced in Xcode 5, folders and names are created *automatically*. However it might be preferable to control the naming of assets (image sets).
* Use a main folder to store the assets (usually named `assets` or `images`). For universal apps, this folder itself can be under a device folder (`iphone`, `ipad`). 
	* Option 1: Keep all assets in one folder, this may seem radical but it could work in conjunction with [prefixing](#prefixing).
	* Option 2: Use subfolders
		* Break the user interface in sections (logical groupings or namespaces) and create subfolders for them (agree on names when reviewing designs). Be aware that subfolders can create problems with asset name [uniqueness](#uniqueness).
		* Format: `images`/`subfolder`/

```
ipad/
	images/
		about/
		detail/
		list/
		share/
		tutorial/ 
iphone/
	...
```

* Use lower case.
* No spaces or special characters (use dashes).


## Asset Type

* Use the [PNG format](http://en.wikipedia.org/wiki/Portable_Network_Graphics) 
	* PNG is good for small assets
	* PNG is non-lossy
	* PNG supports transparency (be aware of a [UIButton tap issue](http://stackoverflow.com/questions/17368803/how-can-i-make-uibutton-respond-to-touch-on-the-transparent-areas-of-a-png-image))
* Create 1x and 2x assets in the same folder 
* Add `@2x` at the end of the [retina asset name](https://developer.apple.com/library/mac/documentation/GraphicsAnimation/Conceptual/HighResolutionOSX/Optimizing/Optimizing.html)

```
asset.png
asset@2x.png
```

To save disk space or time, one can omit the 1x or 2x asset: the system automatically scales up or down for the appropriate resolution (in particular, you could provide only 2x assets when targeting retina devices). 

## Naming

### Uniqueness

An important attribute of an asset name is uniqueness.

* This prevents confusion: for example having two different `share` assets (say one for iPhone and one for iPad, or one in a main view and one in a detail view).
* More importantly, while it is possible in Xcode to have two files of the same names in different folders, you can only reference one of them using `+ (UIImage *)imageNamed:(NSString *)name`.

### Prefixing

Prefixing is optional but it ensures that asset names are unique across the project.

* Prefix the asset with a 2 or 3 letter prefix representing the `project` so you can tell which project it belongs to.
* Add a device prefix, especially for universal apps.
* Add another prefix using the `folder` name or `namespace` so you can quickly organize your assets.
* Format: `project`-`device`-`namespace`-`asset-name`.png

```
ss-ipad-intro-arrow-right.png 
bpc-iphone-intro-arrow-right.png 
```

### Conventions

* **The asset name describes the icon**, not the function of the icon (when possible, see [special cases](#special-cases)).
* Use lower case.
* No spaces or special characters (use dashes).

**Examples**
```
ss-rack-minus.png 
ss-top-bars.png 
ss-tree-check.png
```

**Not**

```
delete.png 
menu.png
selected.png
```

While CamelCase is the convention in Objective-C, it does not necessarily mean it needs to be applied to asset names (by all means feel free to use it if you prefer `SSRackMinus.png`).

#### Notable

* `chevron` for `>`
* `caret` for `►`

#### Special cases 

Sometimes the name is well represented by its function (refer to [Charbase](http://www.charbase.com/21bb-unicode-clockwise-open-circle-arrow) for Unicode).

* `refresh` for `open circle arrow` (⟳ U+21BB)  
* `edit` for `pencil` (✎ U+270E) 
* `search` for `magnifying glass` (🔍 U+1F50D) 
* `user` for `bust in silhouette` (👤 U+1F464) 
* `comment` for `speech balloon` (💬 U+1F4AC)

#### Collisions 

Should two assets have the same name, add a qualifier at the end.


##### Color qualifer

```
ss-top-plus-pink.png
ss-top-plus-gray.png
```

##### Shape qualifer

* `*-square` 
* `*-circle`
* `*-o` for outline

```
ss-top-arrow-right-circle.png
ss-top-arrow-right-square.png
```

##### Combine shapes

* `*-square-o` for square outline

##### Direction qualifer 

* `*-right`
* `*-left`
* `*-up`, etc

```
ss-top-arrow-right.png
ss-top-arrow-square-right.png
```

##### Buttons (control states)

* `*-normal`
* `*-selected`
* `*-highlighted`, etc

```
ss-profile-gear-normal.png
ss-profile-gear-highlighted.png
```

##### Orientation
This is adapated from Apple's [launch images guidelines](https://developer.apple.com/library/ios/documentation/iPhone/Conceptual/iPhoneOSProgrammingGuide/App-RelatedResources/App-RelatedResources.html).

* `*-portrait`
* `*-landscape`
* `*-landscape-right`, etc

### Spelling

In the US, we would favor American over British spelling (sorry M'lady).

**Examples**
```
ss-top-hanger-gray.png  
ss-tree-color-swatch.png 
```

**Not**

```
hanger-grey.png  
colour-swatch.png 
```

### Abbreviations

Do not abbreviate.

**Examples**
```
ss-share-facebook.png 
ss-share-twitter.png  
```

**Not**
```
fb.png
tw.png
```

## Acknowledgment

This guide was inspired by the [NYTimes Objective-C Style Guide](https://github.com/NYTimes/objective-c-style-guide) and the [Font Awesome](http://fontawesome.io/) naming conventions.

Special thanks to the following individuals for their feedback: [Ash Furrow](https://github.com/AshFurrow), [Sergio Campama](https://github.com/sergiocampama), [Matteo Crippa](https://github.com/matteocrippa), [Marco Sousa](https://news.layervault.com/stories/13379-guide-for-naming-assets-in-ios-projects), [Dave McKinney](https://twitter.com/davidkmckinney). 
