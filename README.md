<div align="center">
<pre>
██████╗ ███████╗██████╗ ███████╗███████╗ █████╗ ████████╗  ██████╗ ██╗     ██╗   ██╗██████╗ 
██╔══██╗██╔════╝██╔══██╗██╔════╝██╔════╝██╔══██╗╚══██╔══╝  ██╔══██╗██║     ██║   ██║██╔══██╗
██████╔╝█████╗  ██████╔╝█████╗  █████╗  ██║  ╚═╝   ██║     ██████╦╝██║     ██║   ██║██████╔╝
██╔═══╝ ██╔══╝  ██╔══██╗██╔══╝  ██╔══╝  ██║  ██╗   ██║     ██╔══██╗██║     ██║   ██║██╔══██╗
██║     ███████╗██║  ██║██║     ███████╗╚█████╔╝   ██║     ██████╦╝███████╗╚██████╔╝██║  ██║
╚═╝     ╚══════╝╚═╝  ╚═╝╚═╝     ╚══════╝ ╚════╝    ╚═╝     ╚═════╝ ╚══════╝ ╚═════╝ ╚═╝  ╚═╝
--------------------------------------------------------------------------------------------
 python cli program to remove blurry images
 
</pre>

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

</div>

Moves blurry images from a folder to another given and generates a JSON report.

## Usage example
### To get help with Command-line Arguments
```
python3 perfect_blur.py -h
```
(or)
```
python3 perfect_blur.py --help
```
### Using Comand-line Arguments
```
python3 perfect_blur.py -i ”./pictures/google_photos_backup” -t ”./pictures/blurred_images” -r ”./report.json”
```
(or)
```
python3 perfect_blur.py --image_folder=”./pictures/google_photos_backup” --trash_folder=”./pictures/blurred_images” --report_folder=”./report.json”
```
## Arguments explanation

 -i / --image_folder: "Path of the directory that contains the images to filter"
 
 -t / --trash_folder: "Path of the directory that will recive the blurred images "
 
 -r / --report_folder: "Path of the .json file that will recive the report"

## JSON report example:
``` json
    {
    "elapsed_time": "0.12 seconds",
    "total_images": 5,
    "blurred_images": 2,
    "accepted": [
       {
          "path": "./pictures/google_photos_backup/image1.jpg",
          "score": 70
       },
       {
          "path": "./pictures/google_photos_backup/image3.jpg",
          "score": 90
       },
       {
          "path": "./pictures/google_photos_backup/image4.jpg",
          "score": 74
       }
    ],
    "discarded": [
        {
          "path": "./pictures/google_photos_backup/image2.jpg",
          "score": 10
        },
        {
        "path": "./pictures/google_photos_backup/image5.jpg",
        "score": 10
        }
    ]
    }
```

## Careful!

This script mantains folder hierarchy, which means that soemthing like this:

```
Images_Folder 📁/
├─ Winter 📁/
│  ├─ Blurred_1
│  ├─ Not_Blurred
├─ Summer 📁/
│  ├─ Blurred_1
│  ├─ Not_Blurred
│  ├─ Blurred_2
```

Will give the next result:

```
Trash_Folder 📁/
├─ Winter 📁/
│  ├─ Blurred_1
├─ Summer 📁/
│  ├─ Blurred_1
│  ├─ Blurred_2
```




