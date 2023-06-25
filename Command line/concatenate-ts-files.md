# Concatenate `.ts` files

`.ts` is a streaming video file format.

```bash
cat segment1_0_av.ts segment2_0_av.ts segment3_0_av.ts > all.ts
```

```bash
ffmpeg -i all.ts -acodec copy -vcodec copy all.mp4
```

---

#Bash #CommandLine