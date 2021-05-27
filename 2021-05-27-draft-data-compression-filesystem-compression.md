---
author: RPSchan
---
## 個人壓縮格式測試

#### 鏡像文件寫入USB Flash
47.7GB

exFat 8K
    copy                        9:42s    83.92MB/s
    7z + Zstd Fastest   10.2GB  5:03s   161.20MB/s  34.47MB/s
    7z + Brotli Fastest 10.2GB  3:39s   223.04MB/s  47.69MB/s
    7z + LZ4 Fastest    10.3GB  3:02s	268.38MB/s  57.95MB/s
    7z + LZ5 Fast       10.3GB

#### 簡單壓縮率表
- 測試對象大小爲3.07GB，內容爲：瀏覽器Program + Profile、Program Files、個人文檔
    - 對我來說算是比較典型的日常文件內容
    - 沒有大量容易壓縮的文件，比如磁盤鏡像.img（內有大量全零）
    - 沒有大量難以壓縮的內容，比如圖像、視頻、大型壓縮包（已經壓縮過）
- 基準爲7z的LZMA2的Fastest爲100%，其餘的爲壓縮後比基準大了多少百分比
    - 壓縮後大小 3.07GB -> 2.30GB (74.92%)

7z Fastest      100%
Brotli Fastest  5.06%
Brotli Fast     3.80%
LZ4 Fastest     9.10%
LZ4 Fast        9.10%
LZ5 Fast        8.89%
Zstd Fastest    3.78%
Zstd Fast       1.95%

#### NTFS自帶的壓縮沒有想象中那麼差
用在隨機寫入性能和寫入壽命比較好的設備上（SSD or USB Flash）

雖然NTFS的壓縮算法比現在的LZO、LZ4、Zstd差太遠了，在筆記本的i7HQ上只能跑到50MB/s的寫入（數據壓縮率一般的話），但是勝再穩定不用折騰。

特別是體質比較好的U盤，本來U盤寫入也就100MB/s左右，用btrfs折騰下也就70+，還容易碰到奇怪的問題。用NTFS就當Windows一樣用，問題出得少50也夠用了。

我的實際需求是放磁盤鏡像的.img，其中有大量全0的部分，不管用什麼算法壓縮都很有效 + 快速就是了。
















