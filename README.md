Updater
=======
Simple application to download and apply OTA packages which is compatible with AOSP environment.


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

Note that the upgrading feature is unlocked by the new changes applied in this project.

