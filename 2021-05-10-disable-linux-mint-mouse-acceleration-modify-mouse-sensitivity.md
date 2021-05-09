---
author: RPSchan
---
## Linux Mint關閉鼠標加速度，調整鼠標靈敏度

如果看到標題第一反應是打開鼠標設置，調整加速度到最slow，調整靈敏度到合適的位置，那麼你的問題已經解決了。~~這是我寫過的最短的Blog。~~

### 鼠標加速度
在Mint的設置中調整加速度到Slow似乎是負的鼠標加速度，似乎同時也會影響鼠標靈敏度，總之就是鼠標速度變得很慢。
我的目的是讓鼠標指針按照鼠標回報的數據線性比例地移動（1:1或者1:0.x，沒有加速度）

- 進入```/usr/share/X11/xorg.conf.d/```目錄
- 新增一個文件```50-mouse-acceleration.conf```（文件名似乎隨意）
- 編寫以下內容並reboot
    ```bash
    Section "InputClass"
            Identifier "Mouse With No Acceleration"
            Driver "libinput"
            MatchIsPointer "yes"
            Option "AccelProfile" "flat"
            Option "AccelSpeed" "0"
    EndSection
    ```
    - 原理大概是將Pointer類的輸入設備的加速度Profile設置爲flat
    - ```Option "AccelSpeed" "0"```這句似乎是不必要的

### 鼠標靈敏度
假設我的鼠標默認DPI是1600，我在一般尺寸和分辨率的顯示器上習慣1000DPI，並且不想/不能直接調整鼠標DPI（比如沒Linux版調整工具，鼠標沒有記憶功能）。那麼最好能精確調整鼠標靈敏度。如：1600 x 0.625 = 1000

- 進入```/usr/share/X11/xorg.conf.d/```目錄
- 新增/修改文件```50-mouse-acceleration.conf```（文件名似乎可以隨便）
- 新增一條`Option "TransformationMatrix" "0.625 0 0 0 0.625 0 0 0 1"`
    - value是個3x3的矩陣，如果是單位矩陣的話就是1:1的線性映射，改爲1:0.625（1600:1000）
    - 複習下單位矩陣
        ```
        1 0 0
        0 1 0
        0 0 1
        ```
- 結合上一段去除鼠標加速度，完整的例子
    ```bash
    Section "InputClass"
            Identifier "Mouse With No Acceleration"
            Driver "libinput"
            MatchIsPointer "yes"
            Option "AccelProfile" "flat"
            Option "AccelSpeed" "0"
            Option "TransformationMatrix" "0.625 0 0 0 0.625 0 0 0 1"
    EndSection
    ```

### 考察
比較新版本的```/usr/share/X11/xorg.conf.d/```目錄下的```40-libinput.conf```文件有寫說明
```bash
# If you want to configure your devices, do not copy this file.
# Instead, use a config snippet that contains something like this:
#
# Section "InputClass"
#   Identifier "something or other"
#   MatchDriver "libinput"
#
#   MatrchIsTouchpad "on"
#   ... other Match directives ...
#   Option "someoption" "value"
# EndSection
```
所以寫一個新的```50-mouse-acceleration.conf```大概是這樣來的

另外說明還提到去看xorg.conf(5)的man page，不過除非你對自己讀文檔特別有自信，否則建議別浪費時間去讀那些編寫極其糟糕的文檔~~垃圾~~。
















