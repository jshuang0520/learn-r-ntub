資料結構
========================================================
author: 郭耀仁
date: 2017-10-16
autosize: true

資料結構的本質
========================================================

儲存我們先前說明的不同變數類型：


```r
sat <- "Saturday"
sun <- "Sunday"
```

資料結構的本質（2）
========================================================

儲存我們先前說明的不同變數類型：


```r
weekend <- c("Saturday", "Sunday")
```

資料結構概觀
========================================================

- 一維
    - 向量
    - 因素向量
- 二維
    - 矩陣
    - 資料框
- 多維
    - 陣列
    - 清單
    
向量
========================================================

- 使用 `c()` 函數建立


```r
weekends <- c("Saturday", "Sunday")
logicals <- c(TRUE, FALSE)
numerics <- c(24, 34, 87)
```

向量（2）
========================================================

- 只容許一種變數類型


```r
mixed_vector <- c(logicals, numerics)
mixed_vector
```

```
[1]  1  0 24 34 87
```

```r
class(mixed_vector)
```

```
[1] "numeric"
```

```r
mixed_vector <- c(weekends, logicals, numerics)
mixed_vector
```

```
[1] "Saturday" "Sunday"   "TRUE"     "FALSE"    "24"       "34"      
[7] "87"      
```

```r
class(mixed_vector)
```

```
[1] "character"
```

向量（3）
========================================================

- 使用 `seq()` 函數可以產出數列
- 使用 `rep()` 函數可以產出重複值

向量（4）
========================================================

- 使用 `[]` 搭配索引值選擇元素


```r
workdays <- c("Monday", "Tuesday", "Wednesday", "Thursday", "Friday")
workdays[1]
```

```
[1] "Monday"
```

```r
workdays[2:5]
```

```
[1] "Tuesday"   "Wednesday" "Thursday"  "Friday"   
```

```r
workdays[-1]
```

```
[1] "Tuesday"   "Wednesday" "Thursday"  "Friday"   
```

```r
workdays[c(1, 4, 5)]
```

```
[1] "Monday"   "Thursday" "Friday"  
```

向量（5）
========================================================

- 使用判斷條件產出邏輯值向量選擇元素


```r
logi_filter <- workdays == "Friday"
logi_filter
```

```
[1] FALSE FALSE FALSE FALSE  TRUE
```

```r
workdays[logi_filter]
```

```
[1] "Friday"
```

向量（6）
========================================================

- 練習用兩種方法選出 "Phoebe Buffay" 與 "Chandler Bing"


```r
friends_characters <- c("Rachel Green", "Monica Geller", "Phoebe Buffay", "Joey Tribbiani", "Chandler Bing", "Ross Geller")
```

向量（7）
========================================================

- 練習用兩種方法選出 1, 2, 3, 8, 9, 10


```r
num_vector <- 1:10
```

因素向量
========================================================

- 字串向量，但是多了 `levels` 的資訊


```r
rgb_vec <- c("red", "green", "blue", "green", "red")
rgb_fac <- factor(rgb_vec)
rgb_vec
```

```
[1] "red"   "green" "blue"  "green" "red"  
```

```r
rgb_fac
```

```
[1] red   green blue  green red  
Levels: blue green red
```

```r
class(rgb_fac)
```

```
[1] "factor"
```

因素向量（2）
========================================================

- 兩種類型的因素向量
    - 名目型（Nominal）
    - 順序型（Ordinal）

因素向量（3）
========================================================

- 氣溫有高低之分


```r
temperature <- c("Hot", "Warm", "Cold")
temp_fac <- factor(temperature, ordered = TRUE)
temp_fac
```

```
[1] Hot  Warm Cold
Levels: Cold < Hot < Warm
```

```r
class(temp_fac)
```

```
[1] "ordered" "factor" 
```

因素向量（4）
========================================================

- 氣溫有高低之分


```r
temperature <- c("Hot", "Warm", "Cold")
temp_fac <- factor(temperature, ordered = TRUE, levels = c("Cold", "Warm", "Hot"))
temp_fac
```

```
[1] Hot  Warm Cold
Levels: Cold < Warm < Hot
```

矩陣
========================================================

- m * n 的矩陣指的是有 m 列、n 欄
- 使用 `matrix()` 函數將向量轉換為矩陣
- 預設是以**欄的方向**將元素填入矩陣

矩陣（2）
========================================================


```r
my_mat <- matrix(1:10, nrow = 2)
class(my_mat)
```

```
[1] "matrix"
```

```r
my_mat
```

```
     [,1] [,2] [,3] [,4] [,5]
[1,]    1    3    5    7    9
[2,]    2    4    6    8   10
```

矩陣（3）
========================================================


```r
my_mat <- matrix(1:10, nrow = 2, byrow = TRUE)
my_mat
```

```
     [,1] [,2] [,3] [,4] [,5]
[1,]    1    2    3    4    5
[2,]    6    7    8    9   10
```

矩陣（4）
========================================================

- 使用 `[ , ]` 搭配列與欄的索引值選擇元素

資料框
========================================================

- 資料框是非常重要的資料結構，如果你是 SAS/SPSS/Stata 的使用者，你可以想成是資料集（dataset）
- 一個資料框中可以包含不同資料類別的變數

資料框（2）
========================================================


```r
name <- c("蒙其D魯夫", "羅羅亞索隆", "娜美", "賓什莫克香吉士")
is_female <- c(FALSE, FALSE, TRUE, FALSE)
age <- c(19, 21, 20, 21)
one_piece_df <- data.frame(name, is_female, age)
class(one_piece_df)
```

```
[1] "data.frame"
```

資料框（3）
========================================================

- 使用中括號 `[ , ]`

資料框（4）
========================================================

- 使用錢字號 `$`

資料框（5）
========================================================

- 利用邏輯值向量選擇出觀測值

資料框（6）
========================================================

- 內建資料集 `data()`
- 常用的探索型函數


```r
dim(iris)
nrow(iris)
ncol(iris)
summary(iris)
str(iris)
head(iris)
tail(iris, n = 8)
names(iris)
```

陣列
========================================================

- 擁有三個維度的矩陣


```r
my_vec <- 1:24
my_arr <- array(my_vec, dim = c(2, 3, 4))
my_arr
```

```
, , 1

     [,1] [,2] [,3]
[1,]    1    3    5
[2,]    2    4    6

, , 2

     [,1] [,2] [,3]
[1,]    7    9   11
[2,]    8   10   12

, , 3

     [,1] [,2] [,3]
[1,]   13   15   17
[2,]   14   16   18

, , 4

     [,1] [,2] [,3]
[1,]   19   21   23
[2,]   20   22   24
```

清單
========================================================

- 清單可以包含我們前面介紹的任意資料結構
- 利用雙重中括號 `[[]]` 來選擇


```r
genre <- "Sitcom"
seasons <- 10
starring <- data.frame(
  characters = c("Rachel Green", "Monica Geller", "Phoebe Buffay", "Joey Tribbiani", "Chandler Bing", "Ross Geller"),
  stars = c("Jennifer Aniston", "Courteney Cox", "Lisa Kudrow", "Matt LeBlanc", "Matthew Perry", "David Schwimmer")
)

friends_info <- list(genre, seasons, starring)
```

清單（2）
========================================================

- 或者利用 `$` 與物件名稱來選擇

清單（3）
========================================================

- 練習選出 "Phoebe Buffay" 與 "Chandler Bing"

清單（4）
========================================================

- 清單的重要性是什麼？
    - 彈性的儲存空間
    - 函數的多重輸出
