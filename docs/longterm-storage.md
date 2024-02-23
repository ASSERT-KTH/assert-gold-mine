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
