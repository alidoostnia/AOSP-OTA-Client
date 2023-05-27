OTA Manager for AOSP
=======
Simple application to download and apply OTA packages which is compatible with AOSP environment. This package is adapted from the Lineage project. 


Server requirements
-------------------
The app sends `GET` requests to the URL defined by the `updater_server_url`
resource and expects as response a JSON with the following structure:
```json
{
  "response": [
    {
      "date": "2022-08-21",
      "datetime": 1660855566,
      "filename": "ota-package.zip",
      "id": "5eb63bbbe01eeed093cb22bb8f5a4",
      "romtype": "eng",
      "size": 577620,
      "url": "https://sample.com/ota-package.zip",
      "version": "11.4"
    }
  ]
}
```

The `date` attribute is the build date expressed as real date.  
The `datetime` attribute is the build date expressed as UNIX timestamp.  
The `filename` attribute is the name of the file to be downloaded.  
The `id` attribute is a string that uniquely identifies the update.  
The `romtype` attribute is the string to be compared with the `ro.build.type` property.  
The `size` attribute is the size of the update expressed in bytes.  
The `url` attribute is the URL of the file to be downloaded.  
The `version` attribute is the string to be compared with the `ro.build.version.release` property.  

Additional attributes are ignored.

What's New?
-------------------
Compatibility issues with the AOSP project is addressed in all levels from the presentation layer to the controllers and JAVA libraries.
The upgrading feature is unlocked by the new changes applied in this project. It means that the OTA manager works for both incremental and full updates!

How to Build
-------------------
Put the project in your `/packages/apps` directory. Then, edit the Android.bp file if necessary. Edit the root make file of your AOSP project, and insert the following line anywhere in the file (e.g., in this file `/build/target/product/aosp_x86_64.mk`):
`PRODUCT_PACKAGES := \ Updater` 

the `mm Updater` command builds the incremental changes, and prepare the package to be added to your base image. Then, by running the `m` command, the incremental change is added to the project. 

- The project can be adapted to higher versions of AOSP; however, new changes should be applied.
