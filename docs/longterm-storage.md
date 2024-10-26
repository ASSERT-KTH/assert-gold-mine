# How to store open science data for long term archival and reproducibility?

## Zenodo

We extensively use Zenodo. The default file size limit is 50GB. 

* If the data package is <50GB, push it to Zenodo.
* If the data package is slightly > 50GB, use a better compression algorithm, such as xz, and push it to Zenodo.
* If the data is lower <200GB,  you formally ask for an extension at Zenodo, up to 200GB, see https://zenodo.org/records/10041883 for example.
* If the data is >200GB, you split the reproduction package in smaller 50GB chunks using Unix split command (recommended, see below), see https://github.com/ASSERT-KTH/VRepair/ for example. 

Useful tool:

[zenodo_upload.sh](https://github.com/jhpoelen/zenodo-upload/) allows to upload files on the comman line (instead of the browser UI)

## Performance considerations

### with zip and split

Use /bin/split (and not zipsplit).

To unzip fast, one must avoid writing to disk so one unzips from standard input

```
# cat split zip
$ cat *.zip.* | busybox unzip -
```

### 7z 

Use the `-v` option (v is for volume) to split the archive into chunks. 
 7z `-v` option supports `b k m g` (bytes, kilobytes, megabytes, gigabytes)

Example:
`7z -v50G a my_zip.7z my_folder/`

## Notes about alternatives

* We cannot use KTH OneDrive because all links expire after 180 days.
* KTH has a working group "Research Data", see <https://www.kth.se/en/biblioteket/publicera-analysera/hantera-forskningsdata> 
* [Figshare](https://figshare.com/) max size is 20GB.
* [IEEE DataPort](https://ieee-dataport.org/) 
  - Accepts and stores datasets up to 2TB in size. 
  - We never used it so far. Martin tried a canary in Feb 24, with no success, the submission website is primitive.
  - Open Access Dataset $1,950. Is that a joke?
  - Upload from command line, see https://ieee-dataport.org/help/upload-your-files-directly-ieee-dataport-s3-bucket
* [OSF](https://osf.io/)
  - Done by the Center for Open Science
  - Max size is 50GB for public projects ([ref](https://help.osf.io/article/137-osf-storage-caps))
