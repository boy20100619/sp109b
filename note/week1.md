## 20210224
### 一、gcc指令
* gcc sum.c -o sum : 用-o參數編譯sum.c成sum執行檔 
* gcc -c fib.c -o fib : -c代表只編譯不連結
* gcc -S fib.c -o fib.s : -S編譯成組合語言
* gcc -c sum.s -o sum.o : 將組合語言轉換成目的檔，.o檔為二進位，多個.o檔能壓成函式庫

### 二、makefile
* 範例
```
CC := gcc //:=代表沒有定義時才定義為gcc，否則按原本定義
CFLAGS = -std=c99 -O0 //1999年的c語法標準，-O0指不做最佳化，從O0到O3為數字越高最佳化越高級
TARGET = run

all: $(TARGET)

$(TARGET): sum.c main.c
	$(CC) $(CFLAGS) $^ -o $@

clean:
	rm -f *.o *.exe $(TARGET) //make clean可以刪除TARGET出的run執行檔以及.o和.exe檔
```
* 特殊符號
```
$@ : 該規則的目標文件 (Target file)
$* : 代表 targets 所指定的檔案，但不包含副檔名
$< : 依賴文件列表中的第一個依賴文件 (Dependencies file)
$^ : 依賴文件列表中的所有依賴文件
$? : 依賴文件列表中新於目標文件的文件列表
$* : 代表 targets 所指定的檔案，但不包含副檔名

?= 語法 : 若變數未定義，則替它指定新的值。
:= 語法 : make 會將整個 Makefile 展開後，再決定變數的值。
```
### 三、markdown
![markdown](note/picture/dKAwW7Y.png)
### 四、其他
1. $git checkout -b master :建立並切換branch成master
2. $git push origin master :以master push檔案回github
3. $git checkout main :切換回main
