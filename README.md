# huffman-coding

## 程式簡介
### 簡述
* Implement Huffman 「Coding」 & 「Encoding」 & 「Decoding」

* Coding
  * Input: First line containing a single integer N. Each of the next N lines is a alphabet and it's frequency
  
  * Output: Coding result, Huffman coding table
  
* Encoding
  * Input: a string
  
  * Output: Encoding result, binary Huffman code 
  
* Decoding
  * Input: binary Huffman code  
  
  * Output: Decoding result, a string
    
> No fool-proof design
    
### 範例圖
![image](https://user-images.githubusercontent.com/93152909/146004024-f1fe4f82-cc54-4867-a9c6-1e389bce7323.png)

### 補充說明
1. Q: 輸出的次序是必須要照著輸入的次序嗎 ?   
A: 不用

## Huffman Coding 霍夫曼編碼
* 又譯為哈夫曼編碼、赫夫曼編碼，是一種用於無失真資料壓縮的熵編碼（權編碼）演算法
* 由美國計算機科學家大衛·霍夫曼（David Albert Huffman）在1952年發明
* 其目的是找到有效的二進制編碼

### Coding

1. 文件以ASCII字符的形式讀入，統計每個字符的出現頻率

3. 將所有文件中出現過的字符當作節點，並排列在佇列中 ( 依小到大的頻率排列，會比較方便 )

5. 從佇列中「選出並移除」頻率最小的兩節點，合成二元樹，同時將其根節點作為新節點，重新加入佇列

7. 重複3，直到佇列只剩下一個節點，以該節點為根節點所形成的樹，即為 Huffman tree

8. 從 Huffman tree 的根遍歷到葉節點，左0右1(相反也可)，將途中遇到的0、1序列串起來，即是各字符的編碼

9. 將編碼結果儲存成 Huffman coding table，Coding 完成

> 霍夫曼樹的實作細節有很多種，3.的挑選節點可以使用優先佇列（Priority Queue）實現

### Encoding & Decoding

#### Encoding
* 根據 Huffman coding table 直接將字符轉換成二進制編碼

#### Decoding
* 根據 Huffman coding table 或 Huffman tree 將二進制編碼回推字符

* 單字符解碼的時間複雜度
 
  * Huffman coding table：使用 Hash 為O(1)；暴力搜尋最壞為O(n)
  
  * Huffman tree：最壞為 O(n)
  
* 任一n位數編碼「**不會**」成為其他編碼的前n位數，例如「**不存在**」以下編碼：
  
  |char| binary code|
  |-----|--------|
  |a|010       |
  |b  |0101      |
  
  * 因為字符一定是 Huffman tree 的 leaf，所以會有這樣的特性
  
  * 根據此特性，從二進制編碼的頭到尾進行比對，並不會出現無法判斷的情況



#### 動畫展示
> 參考：https://commons.wikimedia.org/wiki/File:Huffman_huff_demo.gif

 <img src="https://upload.wikimedia.org/wikipedia/commons/a/ac/Huffman_huff_demo.gif" width="450px">

### 直觀理解

* 演算法設計很直觀：出現頻率較高的字元( 字符 )，使用較短的編碼；反之，出現頻率較低者，使用較長的編碼

* 若每個字元( 字符 )的編碼長度一樣，而不考慮其出現頻率，是較不具效率的

### 有趣歷史
* 1951年，霍夫曼在麻省理工學院（MIT）攻讀博士學位，他和修讀訊息論課程的同學得選擇是完成學期報告還是期末考試。導師羅伯特·法諾（Robert Fano）出的學期報告題目是：尋找最有效的二進制編碼。由於無法   證明哪個已有編碼是最有效的，霍夫曼放棄對已有編碼的研究，轉向新的探索，最終發現了基於有序頻率二元樹編碼的想法，並很快證明了這個方法是最有效的。霍夫曼使用由下而上的方法構建二元樹，避免了次優演算   法香農-范諾編碼（Shannon–Fano coding）的最大弊端──自頂向下構建樹。

* 1952年，於論文《一種構建極小多餘編碼的方法》（A Method for the Construction of Minimum-Redundancy Codes）中發表了這個編碼方法。
