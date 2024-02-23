# How to store open science data for long term archival and reproducibility?

We extensively use Zenodo.

The default file limit is 50GB. If the data is larger:

- option 1: you split the files in smaller chunk, see https://github.com/ASSERT-KTH/VRepair/ for example. Use Unix split (recommended, see below) or zipsplit for that.
- option 2: you formally ask for an extension at Zenodo, up to 200GB

Useful tool:

[zenodo_upload.sh](https://github.com/jhpoelen/zenodo-upload/) allows to upload files on the comman line (instead of the browser UI)

## Performance considerations

### with zip

Use /bin/split (and not zipsplit).

To unzip fast, one must avoid writing to disk so one unzips from standard input

```
$ cat *.zip.* | busybox unzip -
```
### xz 


### 7z 

TODO

## Notes

Figshare max size is 20GB.

[IEEE DataPort](https://ieee-dataport.org/) 

- Accepts and stores datasets up to 2TB in size. 
- We never used it so far. Martin tried a canary in Feb 24, with no success, the submission website is primitive.
- Open Access Dataset $1,950. Is that a joke?
- Upload from command line, see https://ieee-dataport.org/help/upload-your-files-directly-ieee-dataport-s3-bucket
