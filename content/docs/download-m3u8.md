---
title: "How to download .m3u8"
weight: 1
# bookFlatSection: false
# bookToc: true
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
---

```
ffmpeg -i "url/list.m3u8" -map p:1 -c copy -bsf:a aac_adtstoasc "/home/file/video.mp4"
```

với -map p:1 để chọn trong danh sách, bắt đầu từ 0 

```
#EXTM3U

#EXT-X-VERSION:3

#EXT-X-STREAM-INF:BANDWIDTH=400000,NAME="low"

size1.m3u8

#EXT-X-STREAM-INF:BANDWIDTH=800000,NAME="med"

size2.m3u8

#EXT-X-STREAM-INF:BANDWIDTH=1900000,NAME="best"

size3.m3u8
```
chuyển từ ts sang mp4

```
-bsf:a aac_adtstoasc
```
<!-- 
{{< gist 5e83f727023bbf737f44f2b540660551 >}} -->