# huffman-coding

## 程式簡介
### 簡述
* Implement Huffman 「Encode」and 「Decode」
* Encode
  * Input: First line containing a single integer N. Each of the next N lines is a alphabet and it's frequency
  
  * Output: Encode result, binary character code 
* Decode
  * Input: A binary character code 
  
  * Output: Decode result, a string
    > No fool-proof design
### 範例圖
![image](https://user-images.githubusercontent.com/93152909/145950286-9af21b28-e437-470d-86e4-f9482d190c20.png)

### 補充說明
1. Q: 輸出的次序是必須要照著輸入的次序嗎 ?   
A: 不用

## Huffman Coding 霍夫曼編碼
* 又譯為哈夫曼編碼、赫夫曼編碼，是一種用於無失真資料壓縮的熵編碼（權編碼）演算法
* 由美國計算機科學家大衛·霍夫曼（David Albert Huffman）在1952年發明
* 其目的是找到有效的二進制編碼
### 步驟
#### 1.  建立 Huffman tree
1. 文件以ASCII字符的形式讀入，統計每個字符的出現頻率

3. 將所有文件中出現過的字符當作節點，並排列在佇列中 ( 依小到大的頻率排列，會比較方便 )

5. 從佇列中「選出並移除」最小的兩個節點，合成一二元樹，同時將二元樹的根節點作為新節點並將其重新加入佇列

7. 重複3，直到佇列只剩下一個節點，該節點即為 Huffman tree 的根節點

* 動畫展示：https://commons.wikimedia.org/wiki/File:Huffman_huff_demo.gif

  <img src="https://upload.wikimedia.org/wikipedia/commons/a/ac/Huffman_huff_demo.gif" width="450px"> 

#### 2.  Encode & Decode
將形成的二叉樹的左節點標0，右節點標1，從最上面的根節點到最下面的葉子節點，遇到遇到的0、1個序列鏈起來，得到把每個字符的編碼表示



### 直觀理解


