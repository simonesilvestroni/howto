# yt-dlp

## Download a single file

Check type and quality:

```
yt-dlp -F <file-URL>
```

Assuming it's a video with ID `22`, then type:

```
yt-dlp -f 22 <file-URL>

## Download a playlist with `yt-dlp`

```
yt-dlp -i <playlistID>
```

## Batch download

Assuming I have a file on the Desktop named `my-list.txt`, check the quality and type:

```bash
yt-dlp -F -a ~/Desktop/my-list.txt
```

Then, if the download type is an audio file and its ID is `140` (for example), type:

```bash
yt-dlp -f 140 -a ~/Desktop/my-list.txt
```
