2025/10/14 書報討論重點整理
===
11463110 張心䛡  
講者：朝陽科技大學 陳信忠 副教授
講題：A Study of Efficient GNSS Coordinate Classification Strategies for Epidemic Management
---

## 重點整理

* GNSS指全球導航衛星系統
* 透過GNSS座標了解疫情區域分布有助於分配醫療、人員等資源
* 提出一個座標分類測略，使用當下目標的GNSS座標和KNN技術對所在區域進行分類(預測)
* PIP(Point in Polygon)：分為the ray casting和the winding number兩種型別，需要多邊形的邊緣來評估節點在內或外
* KNN(K-Nearest Neighbors)：該分類適用於各種領域，包含機器學習；包含一些Train Data Point和一個Test Data Point評估分類
* One-Area and Cell/Rectangle Based PIP：將目標區域進行單元格分配
    * 內部Cell的點：不必評估；交叉Cell的點：進行評估
    * 人就是節點

* 系統模型：
    1. 座標：移動裝置的GNSS座標->儲存為未分類的地理點->Server取出一個點->評估Cell->Server儲存分類
    2. 分類：從目標的移動裝置取得GNSS座標到Server->Server提取候選點->Server分類所在區域
* KNN實現：
    1. 基本分類：$gcc=\underset i{arg}(max\sum_{g'\in NB}I(g'pc=i))$ 
    找到鄰域中類別i的點數最多的類別作為最終分類
    2. 歐幾里德距離：$d(ga,\;gb)=\sqrt{\left(ga_x-gb_x\right)^2-\left(ga_y-gb_y\right)^2}$
    3. 加權KNN：$gcc=\underset i{arg}(max\sum_{g'\in NB}I(g'pc=i)\times d{(g,\;g')}^{-1})$
* 在大量Data Set的KNN分析中大量加速了運算速度與準確度

![整理手寫圖片](251014.jpg)

