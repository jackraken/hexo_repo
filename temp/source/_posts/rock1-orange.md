title: 若渴計畫參加心得<一>
date: 2014-11-22 20:06:44
tags:
- 自由軟體
- 社群
- hacker
category:
- 資訊安全與駭客技巧
---

今天去參加了若渴計畫！聽說台灣非常知名的駭客Orange大大會來分享，剛好最近修資訊安全也有接觸到相關的東西，所以當然要把握
機會來聽聽看囉！
<!--more-->

其實之前暑假去參加HITCON時，就已經聽過Orange的分享，那時候他講的是如何掃出利用遠端桌面的後門，雖然不是我很熟悉的主題，
但印象還是滿深刻的。而今天，Orange則是要和我們講他在2013 WebConf曾經講過的主題，也就是關於"上傳檔案"這件事的資安議題。

在那之前，還有一點讓我滿驚訝的，就是Orange竟然才剛升上研究所而已，其實也沒比我大很多。能在這個年紀就成為知名駭客，真的
令人滿佩服的，每次看到這種神人都會覺得很慚愧 QWQ

那麼，進入主題~

###檔案上傳的資安議題與駭客手法###

我們可以在[這裡](http://www.slideshare.net/p8361/webconf-2013best-practices-the-upload)找到Orange這個主題的投影片。

檔案上傳，可能有許多人在生活中都時常使用到這樣的功能。但在今天之前，我還不知道其中有這麼大的學問~像是如何防止別人上傳
惡意程式等等，其實是有相當多議題可以討論的！

而Orange身為駭客(是白帽子喔)，自然是以駭客的角度出發，來檢視一般檔案上傳可能會遇到的各種漏洞！但在那之前，我們先來看看
所謂駭客入侵的基本步驟和思維吧！

####駭客入侵流程####

1.Reconnaissance 偵查，通常是上網搜尋目標相關資訊
2.Scanning 掃描，掃描目標網站，檢查有無漏洞可鑽
3.Gaining Access 設法取得網站內部權限
4.Maintaining Access 維持，甚至提升權限等級
5.Clearing Tracks 清理蹤跡

以上傳檔案的系統為例，駭客很可能上傳所謂的"後門"，也就是用網頁後端語言寫的程式，可以讓駭客在受害主機下執行各種命令。

####防護議題####

剛剛是從駭客的角度，至於防護者的角度呢？Orange提出三點：

1.沒有防不了的東西
2.不知道的東西防不了
3.游走邊緣的東西防不了

這裡提到，理論上每種攻擊都是可以防禦的，但是最大的問題就在第二點和第三點提到的──"不知道的東西"和"游走邊緣的東西"

####BUG 和 FEATURE####

所謂"不知道的東西"是什麼呢？Orange提到，很多工程師在寫程式或建構系統時，往往都是網路上抄一抄別人的寫法，卻根本沒有深入
了解自己所使用的程式語言或系統，到底具有什麼樣的特點或漏洞，而這些漏洞自然會被駭客所利用，有時候甚至連系統的特色可能都
會變成一種攻擊的手段！

![BUG和FEATURE，往往只有一線之隔](http://i.imgur.com/i5aAskv.png)

舉例而言，他提到一個Nginx的文件解析漏洞。雖說是Nginx文件解析漏洞，其實主要的問題是PHP在解析文件時，假如檔案是在一個有
附檔名的資料夾底下，那個資料夾裡面的檔案都會視為跟資料夾同個附檔名。也就是說，假如我把資料夾取名為xxx.jpg，則裡面的檔案
都會自動被視為jpg檔。這樣，假設一個論壇有上傳照片的功能，駭客就可以上傳其實不是jpg檔的檔案而不被系統偵測到，這時就可以
利用這個漏洞輕鬆上傳腳本或後門進行攻擊了！

除此之外，還有很多漏洞(特色)可能成為駭客入侵的管道，在此大概提一下，有興趣的可以上網深入了解：

1.apache文件解析：如果遇到無法解析的附檔名，會依序向前找合法的副檔名。
EX:如果管理者設定不能上傳php檔，則將檔名取為abcd.php.xxx就可以繞過這道防護(因為.xxx不是合法的，所以會往前找到.php)

2.IIS7以前的版本(和asp.net)，以xx.asp命名的資料夾底下都會當作asp解析

解析檔名時會被分號截斷(EX:aa.asp;bb.jpg 在解析時會被當成asp檔)


####感想####

上傳檔案原來有這麼大的學問，現在才知道 QWQ
想當駭客，似乎真的要懂很多東西呢~再次覺得Orange大大真是厲害！
雖然有點隨便，不過今天的心得就先這樣吧~