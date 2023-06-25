# Compression

## tar

### Compress

```bash
tar czf archive_folder_name.tar.gz folder_to_copy
```

```bash
# `-T` = ‘list of files’
tar cvzf missing_img.tar.gz -T missing-images
```

### Expand

```bash
tar xzvf your-path/name.tar.gz
```

## Zip

### Compress

```bash
zip -r archive_name.zip folder_to_compress
```

```bash
# compress without Mac files
zip -r your-archive.zip your-folder -x "*.DS_Store"
```

```bash
# split files (50 mb size)
zip -r -s 50m split-archive.zip Folder/
```

### Expand

```bash
unzip archive_name.zip
```

---

#Bash #Compression #CommandLine