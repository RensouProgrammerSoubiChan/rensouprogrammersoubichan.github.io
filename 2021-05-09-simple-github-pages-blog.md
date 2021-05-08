## Github Pages超傻瓜式搭建Markdown靜態Blog

### 我認爲的傻瓜式
- 我對Blog功能完全沒需求，也不關心建站
- 我不想管理npm、gem、html、css、javascript、等等等等，這些和文章無關
- 我不想讓「打字變成文章/文件」這樣簡單的事情變成「讓我們先使用xx安裝yy然後在port zzzz建立web服務接着配置……反正就是不寫文章」
- 我看Quickstart、Step by step，懶得讀Manual
- 我希望比別人說的傻瓜更傻瓜
- 我有編程和Git基礎（也不那麼傻瓜）

### 照着Getting started with Github Pages建立Blog站點
- 創建名爲```username.github.io```的repo，設置爲```Public```且創建```README.MD```
- 根據初始設定，把所有的文件都堆在根目錄就好，我應該寫不了那麼多文章
- 可以通過```username.github.io```直接訪問Blog首頁
- 具體步驟可見[Creating a GitHub Pages site](https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site)

### 選個主題讓文字不是那麼刺眼
- 直接在Github中設置主題，具體步驟可見[Adding a theme to your GitHub Pages site with the theme chooser](https://docs.github.com/en/pages/getting-started-with-github-pages/adding-a-theme-to-your-github-pages-site-with-the-theme-chooser)

### 嘗試Post一篇文章
- 直接在Github頁面創建md文件，把文章寫上去，可以避開git配置。或者配置完git，git clone，本地寫完再git push
- 文件名類似```2018-08-20-bananas.md```，一個簡單的例子
    ```markdown
    ---
    author: jill
    ---
    ## Banana
    A banana is an edible fruit – botanically a berry – produced by several kinds
    of large herbaceous flowering plants in the genus Musa.

    In some countries, bananas used for cooking may be called "plantains",
    distinguishing them from dessert bananas. The fruit is variable in size, color,
    and firmness, but is usually elongated and curved, with soft flesh rich in
    starch covered with a rind, which may be green, yellow, red, purple, or brown
    when ripe.
    ```
- 使用```username.github.io/2018-08-20-bananas```訪問對應的web頁。主題生效的話即使文章沒什麼格式，看起來效果還行
- 具體步驟可見[Step by Step Tutorial - 8.Blogging](https://jekyllrb.com/docs/step-by-step/08-blogging/)，跳過了大部分Jekyll內容
- 在首頁手寫新文章的link

### 小結
- 功能：陽春白雪，一共兩個，1、寫md變web，2、有基本的web排版/主題
- 其他：Github幫我們全盤解決，只留最基本的文件（文章md和主題配置）
- 因爲什麼都沒有，首頁還得手寫link，但也避開了不少麻煩

### 吐槽
搜索各類教程的時候，發現不少人喜歡就某一內容直接發一篇文檔/教程的link（甚至直接上項目首頁）。好歹先寫個簡短說明啊，有的文檔老長的，還引用其他文檔的內容。如果能寫一兩句話說明主要步驟，讓別人看文檔也有個線索就更好了。順便也告誡我自己，以後不要犯這種曾經讓自己非常不爽過的低級錯誤。

### 等我學會更多以後也許會寫第二篇
傻瓜式第一篇到此爲止，需要手工在首頁添加文章的link，不是太麻煩，但真的很傻，也許以後我能學會更多吧
