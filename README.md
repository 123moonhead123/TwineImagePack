# TwineImagePack

## ImagePack Macro for Twine SugarCube - by Moonhead

ImagePack for Twine (Sugarcube/TweeGo). Provides a method for showing images from a random named selection. Useful for when you want to to provide some more interesting  images for repetitive passages. This should be simpler, and more powerful, than simply adding a number to the end of a heap of different images, and selecting one at random via a random number.

Files are organised into folders. Each folder becomes it's own "ImagePack", which can then be called upon. Any file from the folder can be selected to be shown, no matter what they're named.

Updating the random file selection is scripted, so there's no need to modify code to select different random numbers.

This macro is intended to run with Sugarcube & TweeGo. It may work with other implementations/formats of Twine, but has not been tested.

## Usage
Usage is split into 2 parts, the macro itself, and the script used to generate the ImagePack JSON index.

## Macro Usage
The macro provided is called RandomImageFromPack, and takes 5 arguments, needed sequentially.

| Index | Argument | Description | Required |
|--|--|--|--|
| 1 | Image Pack Name | The name of the image pack (or path) | Yes |
| 2 | Max Height | Maximum height of the image to be rendered | No |
| 3 | Max Width | Maximum width of the image to be rendered | No | 
| 4 | Alignment | Inline alignment of element rendered. Accepted values are alightLeft, alignRight, alignCentre. If omitted image will not be rendered inline instead push all text down | No
| 5 | Is Path | Is the image pack name a path instead of a name. Accepted value is PathLoad if we are to load form path, anything else is load by name (default) | No |

For example - 

    <<RandomImageFromPack "School Outside" 450 450 alignRight>>

Will pick an image from random from the image pack called "School Outside", and render it at a maximum size of 450px X 450px (retaining scale), to the right of the text, inline.


## Image Pack Script
The second part of this system is the script to generate the Image Pack JSON index. This script is located under Images\ImagePack, and is called RebuildImagePack.cmd. It will output a file called imagePacks.js and place it in the src\javascript folder, where the function script, imagePack.js can be foud.

**Powershell 5.0 is a minimum requirement for this script to run.**

This script will generate an Image Pack for each folder underneath the "ImagePacks" folder from where the script is run. Sub folders will generate their own image pack as well, images can be placed at any level.

To name an image pack, create a file in the folder called "name.txt", and have the name for that folder in the file. If you do not create a "name.txt" file, the default name will be the path of the folder.

You need to run the script to add any new images. If using TweeGo, a batch file to generate both the image pack and HTML is recommended.

