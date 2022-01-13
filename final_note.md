# Linux3
## 正規表達法 Regular Expression
正規表達法是透過一些特殊符號來比對字串的方法，並可對符合比對條件的字串進行搜尋、萃取、替代、轉換等等
### 國際模式比對字符
1.  [:alnum:] 代表英文大小寫字元及數字，亦即0-9，A-Z，a-z
2. [:alpha:] 代表任何英文大小寫字元，亦即A-Z，a-z
3. [:lower:] 代表小寫字元，亦即a-z
4. [:upper:] 代表大寫字元，亦即A-Z
5. [:digit:] 代表數字而已，亦即0-9
6. [:punct:] 代表標點符號，亦即 : ' ? ! ; : # $ @ ...
7. [:blank:] 代表空白鍵與[Tab]按鍵兩者
8. [:cntrl:] 代表鍵盤上面的控制按鍵，亦即包括CR，LF，Tab，Del..等等
9. [:graph:] 除了空白字元(空白鍵與[Tab]按鍵)外的其他所有按鍵
10. [:print:] 代表任何可以被列印出來的字元
11. [:space:] 任何會產生空白的字元，包括空白鍵，[Tab]，CR等等
12. [:xdigit:] 代表16進制的數字類型，因此包括:0-9，A-F，a-f的數字與字元
### 特殊字符
1. ^ :搜尋規則前的「開頭」。意思代表 非」
2. $ :搜尋規則後的「結尾」
3. . :任意一個字元
4. '*' :任意字元或任意字串，單一字元或群組出現任意次數
5. .* :一起使用代表任意字串
6. '+' :單一字元或群組出現至少一次
7. '?' :單一字元或群組出現至少0次或1次
8. {n,m} :比對前一個字元至少n次，至多m次，m、n皆為正整數EX：'a{3,6}' 為三到六個'a'
9. [] :比對範圍內的字元或字串，EX：'[a-z]' 為所有英文小寫字母
10. [^] :比對不再指定範圍內的字元
11. [-] :範圍;如[A-Z]及A,B,C一直到Z都符合要求
12. \ :特別序列的起始字元
### 特定字元
1. \d ([0-9]) :數字
>符合的例子:123
2. \D ([^0-9]) :非數字
>符合的例子:abc或ABC
3. \w ([a-zA-Z0-9_]) :數字、字母、底線
>符合的例子:yes_123或YES123_
4. \W ([^a-zA-z0-9_]) :非\w
>符合的例子:，或、或-
5. \s ([\r\t\n\f]) :空白字元
>符合的例子:
6. \S ([^\r\t\n\f]) :非空白字元
>符合的例子:123或yes123_或，
### 特定符號
1. .【點】
> 點可代替所有可能的字元（字母、數字或符號）。
>#### EX：.GC → UGC、OGC、PGC、2GC或是nGC等...
2. ?【問號】
> 比對前一個字串或是不比對。
>#### EX：facebo?k → facebook、facebok
3. *【星號】
> 比對前一個字串零次或是多次。
>#### EX：sky*blue → skblue(y出現0次)、skyblue(y出現1次)、skyyyblue(y出現多次)
4. -【破折號】
>#### EX：product[A-K] → productA、productB、productC、productD...productK
5. +【加號】
> 跟星號類似，差別在於至少要與前一個字比對一次或以上。
>#### EX：sky+blue → skyblue(y出現1次)、skyyyblue(y出現多次)
6. |【直線】
> 或者。
>#### EX：想找到Facebook、Instagram、Wordpress、Google相關的文章，可以使用Facebook | Instagram | Wordpress | Google
7. ^【插入符號】和$【錢字符號】
> ^插入符號是比對前開頭，$錢字符號則是比對結尾。
>#### EX：^eat → eat、eatenEX：eat$ → creat、peat、leat
8. \【反斜線】
> 將任何特殊字元，恢復成  一般字元。
>#### EX：transbiz\.com → transbiz.com
9. ()【括號】
> 把想找的相關字詞放 入括號內，可依照 括號 裡的字元 排序找到可能的結果。
>#### EX：(sym) → sympathy、symbol、assym等
10. []【中括號】
> 任意比對字串內的每個項目。
>#### EX：product[DEFG] → productD、productE、productF、productG
## grep語法
可從資料或檔案中  ，使用關鍵字或正規表達法(Regex)找出想要的內容
> grep [option] filename
### grep參數
1. -i → 忽略大小寫
2. -n → 顯示匹配行及行號
3. -r → 遞歸顯示目錄
4. -c → 只輸出匹配行的計數
5. -v → 只列出不符合的內容
6. --color   =ne ver|always|auto → 顏色標示
7. -A → 多顯示匹配行的後幾行
8. -B → 多顯示匹配行的前幾行
9. -C → 多顯示匹配行的前後幾行
### grep + 正規表達法
1. 開頭結尾
>1. a開頭 → ls | grep “^a”
>2. a或b結尾 → ls | grep “[ab]$”
2. 出現次數
>1. a開頭，出現0次以上 → ls | grep “^a*”
>2. a開頭，出現零次或一次 → ls | grep “^a?”
>3. a開頭，出現一次以上 → ls | grep “^a+”
3. 多種組合
>1. 含有ab或cd → ls | grep “ab\|cd”
>2. 含有ab開頭或cd結尾 → ls | grep “^ab\|cd$”
## 文字處理工具
### WC 文字處理工具
wc → 計算指定檔案內容的換行數、字數與位元組數
> wc [option] filename
>1. -l → 只計算換行數
>2. -w → 只計算字數
>3. -c → 只計算位元組數
>4. -m → 只計算字元數
>5. -L → 計算最常行的長度
### Cut 文字處理工具
cut → 逐行擷取部分字元或欄位資料
> cut [option] filename
>1. -b → 輸出的指定範圍以bytes作為單位
>2. -c → 輸出的指定範圍以字元數量作為單位
>3. -d → 指定分隔字元，default為tab作為分隔
>4. -f → 輸出的指定範圍(每筆data的第幾column作為區分)
>5. -s → 若該行無分隔字元則不顯示
### Paste 文字處理工具
paste → 將每個文件以列對列的方式，一列一列加以合併
>paste [-s] [-d<間隔符號>] [--help] [--version] filename
### Diff 文字處理工具
diff → 比較文件的內容，特別是兩版本不同的同份文件
> diff [option] filename1 filename2
>1. -y → 以並列方式顯示文件的異同之處
>2. -W → 使用-y參數時，指定欄寬
>3. -C → 前後輸出格式
>4. -u → 統一格式輸出
### Sort 文字處理工具
sort → 處理各種文字資料的排序問題
> sort [option] filename
>1. -f → 忽略大小寫
>2. -u → 去除重複資料
>3. -r → 反向排序
>4. -t → 指定欄位的分隔字元(default=blank or tab)
>5. -k → 指定欄位的編號
>6. -n → 依照實際數值的大小排序
>7. -h → 對有單位的數值排序
>8. -M → 依照月份排序
>#### LC_ALL  =C (調整系統語言)在非英文   語系的系統上操作月份資料排序時，需先將語言設定文英文，方可操作。
### Uniq 文字處理工具
uniq → 將連續重複文字 刪除
> uniq [option] filename
>1. -c → 計算文字行重複次數
>2. -D → 只輸出有重複的文字行
>3. -d → 將重複行刪掉
>4. -u → 只輸出沒有重複的文字行
>5. -f → 指定要跳過的欄位
>6. -s → 跳過每一行開頭幾個字元
>7. -w → 只比較每一行開頭幾個字元
>8. -i → 忽略大小寫
### Tr 文字處理工具
tr → 替換或刪除操作的字串轉換
> r [option] set1 set2
>1. -c → 用set1中字符 集的補集替換此字符集，且字符集需符合ASCII
>2. -d → 刪除檔案中 所有在set1中出現的字元
>3. -s → 刪除檔案中重複且set1中出現的字元，只保留一個
### Join 文字處理工具
Join → 將兩個文件中，指定欄位內容相同的行連接起來
> join [option] filename1 filename2
>1. -1 → 連接filename1指定的 欄位
>2. -2 → 連接filename2指定的 欄位
>3. -t → 使用欄位的分隔符號
>4. -i → 忽略大小寫
>5. -o → 按指定的格式顯示結果
>6. -a → 除顯示結果，原檔案  的其他行也顯示
# Linux4
## awk 文字分析工具
1. 常用在對文字和資料進行分析處理
2. 檔案逐行的讀入
3. 以空格為預設分隔符號
### awk Script
awk 'BEGIN{ print "start" } pattern{ commands } END{ print "end" }' filename
> 工作原理
>1. 第一步執行BEGIN 語句
>2. 第二步從檔案或標準輸入讀取一行，然後再執行pattern語句，逐行掃描檔案到檔案全部被讀取
>3. 第三步執行END語句
### awk Script
>1. Begin { statement }
>> 主要目的是用來更改一些預設的設定, 如: FS (輸入行的欄位分割符號), RS (輸入行的換行分割符號)...等等, 以及讀取命令行的參數
>2. pattern { action }
>> 被執行的次數是依據被讀取文字輸入檔有多少行來決定. 一般都是在這區塊做資料的判斷統計，可以在pattern 中加入一些判斷式，來決定要不要執行action.
>3. END { statement }
>> 輸出統計完的結果(存到檔案, 或是傳到標準輸出
### awk record & field
![image](https://user-images.githubusercontent.com/91867104/149366019-222408a0-52d1-43a7-9c32-e099fe89f294.png)
### awk 語法
awk  [options]  ‘scripts’  var=value  filename
> 常用引數
>1. -F 指定分隔符(可是字串或正規表達法)，預設是空白(space)
>2. -f 從指令碼檔案(awk script)中讀取awk命令
>3. -v var=value賦值變數，將外部變數遞給awk
### awk print record & field
1. awk -F “\tab” '{print $0}' fruit.txt
2. awk '{print $1, $2, $4}' fruit.txt
>1. $0：entire line
>2. $1：column 1
>3. $2：column 2
### awk 參數
1. $0      #當前record(列、橫行)
2. $1~$n  #當前record的第N個欄位
3. FS      #輸入field直欄分隔符（-F相同作用）預設空格
4. RS      #輸入record(列、橫行)分割符，預設換行符
5. NF      #欄位個數
6. NR      #record數，就是行號，預設從1開始
7. OFS    #輸出欄位分隔符，預設空格
8. ORS    #輸出resord分割符，預設換行符
## awk 運算子
### awk 算術運算子
awk '$2 + $3 >= 160 {print $0}' filename
1. + :Add
> x+y
2. - :Substract
> x-y
3. '*' :Multiply
> x*y
4. / :Divide
> x/y
5. % :Modulus
> x%y
6. ^ :Exponentia
> x^y
### awk 關係運算子
awk '{if ($3 == 120) print $0}’ filename
1. < :Less than
> x<y
2. <= :Less than  or equal
> x<=y
3. == :Equal to
> x==y
4. != :Not equal to
> x!=y
5. > :Greater than
> x>y
6. >= :Greater than or equal to
> x>=y
### awk 邏輯運算子
awk '($2 > 6) && ($3 >= 150) {print $0}’ filename
1. && :Logical AND
> x&&y
2. || :Logical OR
> x || y
### awk 正則運算子
awk '{if ($3 ~ /0/) print $0}’ filename
1. ~ :Matched by reg exp
> x~/y/
2. !~ :Not matched by req exp
> x!~/y/
### awk 賦值運算子
Example : awk '{for (j=1; j <= NF; j++) { print $j }}' filename
1. = :Assign result of right-hand-side expression to left-hand-side variable
2. ++ :Add 1 to variable
3. -- :Subtract 1 from variable
4. += :Assign result of addition
5. -= :Assign result of subtraction
6. *= :Assign result of multiplication
7. /= :Assign result of division
8. %= :Assign result of modulo
9. ^= :Assign result of exponentiation
## Git1
## sed 文字分析工具
1. 「stream editor 」的縮寫，顧名思義是進行串流(stream) 的編輯
2. 字串取代、複製、刪除的功能
3. 自動化的修改文字檔
### Sed指令
sed [option] “[n1,n2] [command] / [pattern] / [replacement] / [flag]” file.txt
1. option：以- 符號開頭的功能，如-n、-r、-i，可省略
2. n1,n2：代表開始行數和結尾行數，一個代表指定的這行，不輸入代表每行都會執行command
3. command：進行的動作，如s, a, c, d, i
4. pattern：給command使用的參數
5. replacement：當使用s指令時會使用
6. flag：當使用s指令時會使用
### Sed語法-常用選項
sed [-nefi] “[n1,n2] [command] / [pattern] / [replacement] / [flag]” file.txt
> option:
>1. -n: 沉默模式，只有經過sed處理的那行才會被印出
>2. -e :  直接在命令模式編輯，預設
>3. -f :  直接將sed動作寫在一個檔案內，-f file會直接執行file裡面的動作
>4. -i :  修改檔案
### Sed語法-常用指令
sed [-nefi] “[n1,n2] [command] / [pattern] / [replacement] / [flag]” file.txt
> command:
>1. a: 新增，在下一行插入字串，未指定行數的話，則是在每一行之後插入字串
>2. c:  取代， 取代指定行數的內容
>3. d : 刪除，後面通常不接任何東西
>4. i :  插入，在指定行數的前一行插入字串
>5. p : 印出，只印出受影響的行，常搭配-n使用
>6. s : 搜尋、取代，最常用的指令，可搭配正規表達式使用，將搜尋的內容進行取代
### Sed語法-常用旗幟
sed [-nefi] “[n1,n2] [command] / [pattern] / [replacement] / [flag]” file.tx
> flag:
>1. g: 全部取代
>2. [0-9]: 每行第幾次出現
>3. I :  忽略大小寫
>4. w :  把符合的結果寫入檔案
### Sed應用-- s搜尋並取代
1. sed -e ‘s/a/A/1’ apple.txt
2. sed ‘s/a/A/g’ apple.txt
![image](https://user-images.githubusercontent.com/91867104/149374495-4f43e481-4e8e-418e-b6dc-b7e5c82dad63.png)
![image](https://user-images.githubusercontent.com/91867104/149374516-49fb5263-bcc2-413e-b79a-307e997cc6f4.png)

### Sed應用-- -n沉默模式+p 只印出受影響的行
1. sed -n ‘s/a/A/p’ apple.txt
2. sed -n ‘s/a/A/p’ apple.txt > apple_output.txt
![image](https://user-images.githubusercontent.com/91867104/149374635-76426be9-0d65-49b7-bb4f-8aed1445ae15.png)

### Sed應用-- -f 讀取檔案手稿
sed -f apple_command.txt apple.txt
![image](https://user-images.githubusercontent.com/91867104/149374668-49c6abe4-f3e3-4d83-bf44-48d802fe02cc.png)
### Sed應用-- a新增, c取代, d刪除
1. sed '1a apple apple apple' apple.txt
2. sed -i '2,3c hahaha' apple.txt
3. sed 1,5d apple.txt
![image](https://user-images.githubusercontent.com/91867104/149375452-0c6a98cd-6e01-458a-b017-b5d249388f3b.png)
![image](https://user-images.githubusercontent.com/91867104/149375498-80483e9d-6334-4245-bfca-a2b241842339.png)
![image](https://user-images.githubusercontent.com/91867104/149375516-2c32d4e5-f7f5-40ca-b3fa-09a1b0400e52.png)
### Sed應用-- s搜尋並取代+正規表達法
sed 's/.e/E/g' apple.txt
![image](https://user-images.githubusercontent.com/91867104/149375701-032be0b5-e342-4dc1-b838-8aa3ac20cbcb.png)
![image](https://user-images.githubusercontent.com/91867104/149375724-60444cd0-3ed5-417d-bbba-a0edc975f283.png)
### Sed應用-- s搜尋並取代(多個)&存檔
1. sed 's/pen/pencil/; s/have/had/' apple.txt
2. sed 's/pen/pencil/; s/have/had/' apple.txt > apple_output.txt等同於sed -e 's/pen/pencil/' -e 's/have/had/' apple.txt > apple_output.txt
![image](https://user-images.githubusercontent.com/91867104/149375920-aaa5adb7-027b-4c28-856b-9a331b740fe1.png)
### Grep, Awk, Sed比較
1. grep：文字搜尋工具
>1.  可用正規表達法，找出匹配的內容
2. sed ：是一種線上編輯器
>1. 它一次處理一行內容，可搭配正規表達法
>2. 主要用來自動編輯一個或多個檔案，簡化對檔案的反覆操作
>3. 用於行間的內容操作,如增刪改,查詢替換
3. awk：文字分析工具
>1. 逐行的讀入，可搭配正規表達法
>2. 主要用在對文字和資料進行分析處理，以空格為預設分隔符號
>3. 同時也是程式語言
>4. 用於處理有欄位規則的行內內容,並支援格式化輸出
## Git
### Git 是什麼？
1. 免費、開源專案管理工具
2. 用來做軟體的版本控制與維護
3. 記錄版本更動情形，保留對於檔案的新增、修改或是刪除等操作的歷史紀錄
4. 分散式系統
5. 可離線工作
6. 多人合作專案時15
### Git-版本控制
![image](https://user-images.githubusercontent.com/91867104/149376820-41a6185e-0c99-4757-a7fb-530759607742.png)
造成的困擾：
1. 當檔案備份過多時
>1. 容易忘記每個檔案做了哪些變動，檔案之間的差異
2. 當多人共同編輯時
>1. 在整合檔案或是不同人在進行反覆編輯時，容易導致原本的檔案被覆蓋掉
>2. 修改到別人的程式碼
### Git-版本控制的特點
1. 版本儲存
> 儲存檔案的重要資訊，EX：編輯者、時間、版本相關資訊
2. 共同編輯
> 可藉由repository和共同編輯者分享資料，不會因為兩人同時編輯，導致先進行編輯的人的內容被覆蓋掉
3. 儲存空間
> git並不是記錄版本差異，而是記錄檔案內容的快照，使git體積小、速度快18
### Git-版本控制流程
![image](https://user-images.githubusercontent.com/91867104/149377641-4c690d9c-12bc-4d68-b623-d60e675ea8d0.png)
![image](https://user-images.githubusercontent.com/91867104/149377725-646596a1-a15e-468e-9187-f76694b3550b.png)

### Git 指令
1. 初始化專案：git init
2. 單一檔案  加入索引(暫存區)：git add <檔案名稱>
3. 所有檔案  加入索引(暫存區)：git add
4. 觀看當前 狀態：git status
5. 提交版本：git commit -m “”修改紀錄
6. 瀏覽歷史紀錄：git log
### Git-使用方法 Local(本地端)
![image](https://user-images.githubusercontent.com/91867104/149382170-dff417b3-6d2d-4166-aa1f-1379c9f867a4.png)

1. 新增Working directory(工作目錄)
>1. 建立資料夾(ex：mkdir cs6_git)
>2. 移動到資料夾：$ cd cs6_git
>#### ＃此時會產生隱藏   檔(.git)，而這個隱藏檔會追蹤修改
>3. 將專案資料夾建立成git repository：$ git init (初始化資料夾)
>4. 新增檔案(ex：index.html)
>#### ＃此時檔案 尚未被 追蹤(Untracked files
>5. 查看資料夾內檔案變化：$ git status
![image](https://user-images.githubusercontent.com/91867104/149382227-cbbf6c4b-0420-4bba-b4d7-d6730dcfe81c.png)

2. 進入Staging area(暫存區)
>1. 將新增或變更的檔案加入追蹤：$ git add index.html
>#### ＃此時檔案已被追蹤
>2. 查看資料夾內檔案變化：$ git status
>3. 再新增一個檔案(ex：README.md)
>4. 查看資料夾內檔案的變化：$ git status
![image](https://user-images.githubusercontent.com/91867104/149382390-7de17ec2-06bc-4d36-9f03-2dbffb103edd.png)

3. 進入Local repository(本地數據庫)
>1. 將檔案移入本地repo，提交新版本：
>> $ git commit -m “First release of Hello”
>>#### ＃-m：填寫版本資 訊、修改紀錄。方便日後查找
>2. 使用$ git status觀察：$ git status
>>#### ＃出現nothing to commit, working tree clean”，因為暫存區的檔案 已被提交 成新的版本
>3. 查看新增的版本(歷史紀錄)：$ git log
>>#### ＃會看到版本更新紀錄
# Git2
## Git 講解與實作
### Git 指令
1. 初始化專案：git init
2. 單一檔案加入索引(暫存區)：git add <檔案名稱>
3. 所有檔案加入索引(暫存區)：git add
4. 觀看當前狀態：git status
5. 提交版本：git commit -m “修改紀錄”
6. 瀏覽歷史紀錄：git log
7. 取消追蹤檔案：git rm –cached <檔案名稱>
8. 取消commit：git reset --mixed HEAD^
9. 連接遠端數據庫：git remote add origin <remote網址>
10. 將本地資料推到remote端：git push -u origin master
11. 將遠端資料拉回來：git fetch
12. 將拉回的資料和本地資料合併：git merge
13. git pull = git fetch + git merge
### Git-版本控制流程
![image](https://user-images.githubusercontent.com/91867104/149381033-120aebe6-fc32-4e34-9d85-447ea1a3866c.png)
![image](https://user-images.githubus ercontent.com/91867104/149381055-4ce771b6-eba8-438a-abc7-64b141c29344.png)
### Git- 不再追蹤檔案& 取消commit
![image](https://user-images.githubusercontent.com/91867104/149381167-f8e3a0c2-d87e-40c0-a5fd-92055fe353f8.png)
git rm –cached      git reset HEAD^
### Git- 取消追蹤檔案 Local(本地端)
![image](https://user-images.githubusercontent.com/91867104/149382491-84763f8c-5ece-407b-8301-f839c84af210.png)

4. 檔案從Staging area(暫存區)退回Working directory工作目錄
> (不是真的想把這個檔案刪掉，只是不想讓這個檔案再被Git 控管)
>1. 修改index.html：vi index.html
>2. 查看狀態：$ git status
>3. 將檔案加入索引：$ git add index.html
>4. 查看狀態：$ git status
>5. 取消追蹤檔案：$ git rm –cached index.html
>>#### ＃此時檔案變回尚未被追蹤(Untracked files)
>6. 查看狀態：$ git status
![image](https://user-images.githubusercontent.com/91867104/149383125-ba71ced8-d610-4fe7-9ca3-da58a57ee1fa.png)

5. 將commit拆掉
>1. 新增檔案：vi hello.py
>2. 將檔案加入索引：$ git add
>3. 提交版本：$ git commit -m “print method”
>4. 查看歷史紀錄：$ git log
>5. 取消commit：$ git reset --mixed HEAD^
>6. 查看歷史紀錄：$ git log
>>#### #  ^ 符號表示「前一次」的意思，回到前n個
>>#### #  會發現最後一次commit的紀錄不見了
>7. 查看狀態：$ git status
>>#### #  會出現hello.py尚未被追蹤，代表此時檔案在工作目錄
### Git- Reset模式
Reset有三種模式：
>1. --mixed：預設模式，Commit 拆出來的檔案會留在工作目錄，但不會留在暫存區
>2. --soft：工作目錄跟暫存區的檔案都不會被丟掉
>3. --hard：工作目錄以及暫存區的檔案都會丟掉
![image](https://user-images.githubusercontent.com/91867104/149383823-f871af5d-4004-46cc-b9a7-4b8bbc7aa339.png)

### Git-使用方法 Remote(雲端)
![image](https://user-images.githubusercontent.com/91867104/149383960-ef8e6512-bb18-432f-b93b-aa615082026d.png)

6. 進入Remote repository(遠端數據庫)
>1. 雲端跟本地端連動：$ git remote add origin <remote網址>
>2. Push Local master(主幹)進入Remote：$ git push --set-upstream origin master
>3. 回到Github查看
>>#### ＃等同於$ git push -u origin master
>>#### ＃-u : 設定要push到哪裡，當之後push不加參數時，會將本地Local repo的master分支，push到遠端的origin節點下
![image](https://user-images.githubusercontent.com/91867104/149384503-288b8ac6-87b8-4e4e-8813-47d337206bdf.png)

7. Remote repository(遠端數據庫)
>1. 到github上新增或編輯README.md
>2. 把遠端東西拉回來：$ git fetch
>>#### # 執行Fetch 指令後，Git 看了一下線上版本的內容後，將目前線上有但本地這邊沒有的內容抓了一份下來
>3. 查看狀態：$ git status
>4. 查看歷史紀錄：$ git log
>>#### # 會發現在github上發送的commit被抓下來了
>5. 比較本地分支和遠端分之內容的不同：$ git diff origin/maste
>6. 將遠端和本地端的內容做合併：$ git merge origin/master
>7. 查看狀態：$ git status
>8. Pull下載更新：$ git pull origin
>>#### # 將本地master的資料更新, 以防與Remote端不同
## Git Flow
![image](https://user-images.githubusercontent.com/91867104/149385015-740e16cc-4b59-46cd-b559-d4b26447936e.png)

### Git Flow分支應用
1. 主要的分支有master、develop、hotfix、release以及feature
2. 各種分支負責不同的功能
3. Master以及Develop這兩個分支又被稱做長期分支，會一直存活在整個Git Flow 裡
4. 其它的分支大多會因任務結束而被刪除
>1. Master 分支
>>1. 主要是用來放穩定、隨時可上線的版本。
>>2. 個分支的來源只能從別的分支合併過來
>>3. 通常會在這個分支上的Commit 上打上版本號標籤。
>2. Develop 分支
>>1. 所有開發的基礎分支
>>2. 當要新增功能的時候，所有的Feature 分支都是從這個分支切出去的。而功能完成後，也都會合併回來這個分支。
>3. Hotfix 分支
>>1. 當線上產品發生緊急問題的時候，會從Master 分支開一個Hotfix 分支出來進行修復，Hotfix 分支修復完成之後，會合併回Master 分支，也同時會合併一份到Develop 分支。
>4. Release 分支
>>1. 當認為Develop 分支夠成熟了，就會合併到Release 分支，在這邊進行上線前的最後測試。
>>2. 測試完成後，Release 分支將會同時合併到Master 以及Develop 這兩個分支上
>5. Feature 分支
>>1. 當要開始新增功能的時候
>>2. 從Develop 分支來的，完成之後再併回Develop 分支。
## 虛擬機
### 什麼是虛擬機?
1. 行為類似 實際電腦 的電腦 檔案(通常稱作 映像)。
2. 可在視窗中 以獨立的運算環境 執行
3. 常用來執行不同的作業系統(os, windows, linux...)
### 虛擬機的優點
1. 節省成本
2. 靈活度與速度
3. 降低停機時間
4. 可擴縮性
5. 安全性優點
