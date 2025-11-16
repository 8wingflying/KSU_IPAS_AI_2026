# Python作業

## 資料型態:字串
- 大小寫轉換:給定一段英文句子，請將所有英文字母轉成 小寫，並移除所有首尾空白。
- 字串反轉:輸入一個字串，請輸出其 反轉後 的結果`（不能使用 slicing 的 [::-1]）`。
- 計算字元出現次數:輸入字串與一個目標字元，請計算該字元在字串中出現幾次（不分大小寫）
- 移除標點符號:請寫程式將字串中的所有標點符號（. , ! ? ; : ' "）移除
- 判斷是否為迴文:輸入任意字串，忽略大小寫與空白後，判斷是否為迴文
- 字串壓縮:
  - 輸入 "aaabbcccaaa" ==> 輸出壓縮後字串：a3b2c3a3
- 字串展開:
  - 給定壓縮字串，例如：a3b2c4 ==> 請展開成：aaabbcccc
- 移除重複字元
  - 輸入字串 aabbccddeeffgg → 請移除連續重複字元，輸出：abcdefg
- 字串分詞（自行拆分）:
  - 將 `"apple,banana;orange/grape"` 使用任何標點進行分割，得到：`["apple","banana","orange","grape"]`
- 統計單字次數:
  - 輸入英文句子：This is a test, and this test is simple.==> 請輸出每個單字的次數（忽略大小寫、忽略標點）。
- 移除空白（含中間）
  - 輸入：" A B C " ==> 請移除所有空白 → "ABC"
- 字串重複偵測(判斷是否由某子字串重複組成)
  - 輸入："abababab" → 回傳 True
  - 輸入："abcdab" → 回傳 False

## 決策程式開發 IF
- 奇偶判斷:輸入一個整數，判斷是否為偶數。
- 成績等第:輸入分數，若 ≥90 A；≥80 B；≥70 C；≥60 D；否則不及格
- 成年人判斷:輸入年齡，如果 ≥18 歲顯示「成年人」，否則「未成年人」
- 正負數判斷:輸入數字判斷正數、負數或零
- 輸入驗證:帳號：admin、密碼：1234 才能登入。
- 三數最大值:輸入三個數字找最大者。
- 購物折扣:滿 1000 打 9 折，滿 3000 打 8 折，否則無折扣。
- BMI 結果分類:BMI < 18.5 過輕；18.5~24 正常；>24 過重。
- 是否為閏年:
  - 閏年規則：
    - 可被 4 整除但不可被 100 整除
    - 或可被 400 整除
- 時薪 overtime計算:時薪 150，超過 8 小時的部分按 1.5 倍。
- 三角形判斷:輸入三邊能否組成三角形。
```python
a, b, c = map(int, input("輸入三邊: ").split())
if a + b > c and a + c > b and b + c > a:
    print("可以組成三角形")
else:
    print("不行")
```
- IPAS初階考試是否通過:輸入兩科分數
  - 若 科目1≥70 且 科目2≥70 B==> 輸出通過
  - 若 科目1≥60 且 科目2≥60 且 (科目1+科目2)/2 ≥60 ==> 輸出通過
  - 否則不及格
```python
s1 = float(input("請輸入科目1分數："))
s2 = float(input("請輸入科目2分數："))

# 判斷規則
if s1 >= 70 and s2 >= 70:
    print("通過")
elif s1 >= 60 and s2 >= 60 and (s1 + s2) / 2 >= 60:
    print("通過")
else:
    print("不及格")
```
- 
## Loop程式開發
- 找出最長無重複子字串(經典字串題）
  - 輸入："abcabcbb" → 輸出 "abc"
- 字串格式化（模板）
  - 給定模板 "Hello {user}, total price = {price} TWD"
  - 輸入 user="Ben", price=100 →
  - 輸出 "Hello Ben, total price = 100 TWD"
- 驗證密碼強度{輸入密碼判斷是否：
  - 長度 ≥ 8
  - 含大小寫字母
  - 含數字
  - 含特殊符號
- 找出最長共同前綴
  - 輸入：`["flower","flow","flight"]` ==> 輸出：`"fl" `
## 函數開發
- 基礎函數題
  - 設計一個函數 add(a, b) 回傳兩數相加的結果
  - 設計一個函數 is_even(num) 判斷輸入是否為偶數（回傳 True/False）
  - 設計一個函數 greet(name)，輸入名字後回傳：`「Hello, XXX！」`
  - 設計一個函數 square_list(nums)：輸入一串整數 list，回傳所有元素平方後的新 list。
- 中等函數題
  - 設計一個函數 factorial(n) 計算 n 的階乘
  - 設計一個函數 is_prime(n)：判斷整數是否為質數
  - 設計一個函數 remove_duplicates(lst)：去除 list 內重複的元素並回傳新 list（保持原順序）
  - 設計一個函數 merge_dicts(d1, d2)：將兩個 dictionary 合併成一個新 dict（若 key 衝突，以 d2 為主）
  - 設計一個函數 sum_of_digits(n)：輸入整數 n，計算其每個數字的總和。
    - 例如：123 → 1+2+3 = 6*
  - 設計一個函數 longest_word(words)找出字串 list 中最長的字
  - 設計一個函數 count_words(sentence)：輸入一句話並回傳單字數。
  - 例："I love Python" → 3
  - 
- 遞廻函數題(底下考題)
- 進階函數題
  - 計一個函數 fibonacci(n)回傳第 n 個費波那契數（可用迴圈或遞迴）
  - 設計一個函數 find_anagrams(word, word_list)輸入一個單字，回傳 word_list 中所有「字母相同但順序不同」的字
  - 設計一個函數 flatten(nested_list)將多層巢狀 list 攤平成一維 list。
  - 例如：[1,[2,[3,4]],5] → [1,2,3,4,5]（可用遞迴）
  - 設計一個函數 statistics(nums)回傳以下統計資訊（以 dict 表示）：
```
{
    "mean": 平均值,
    "min": 最小值,
    "max": 最大值,
    "median": 中位數
}
```
  - 
