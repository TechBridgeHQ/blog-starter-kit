---
title: 程式解題新手入門注意事項
date: 2019-11-02 10:34:52
tags:
  - JavaScript
  - Algorithm
autohr: huli
---

## 前言

在這兩三年之間，「刷題」似乎成為了一種風潮。本科系要去面試大公司的時候要刷題，非本科系出去面試也要刷題，好像只要沒有刷題就會落後他人，就會被公司刷掉。

其實我一直不是很喜歡「刷題」這個詞，主要是因為「刷」這個字。不知道大家對這個字的解讀是什麼，但我會認為有種「為了寫題目而寫題目」的感覺，就好像題海戰術那樣。雖然說題海戰術用得好的話成效滿顯著的，但總感覺很多人刷到最後會變成「看過的題目就會，沒看過的就一定不會」，如果是這樣子的話，那我覺得不是一件好事。

之前我有寫了一篇文章：[當我們在學程式時，要學的到底是什麼？](https://medium.com/@hulitw/learn-coding-9c572c2fb2)，稍微談了一下這件事情。

總之呢，比起刷題這個詞，我更喜歡用「程式解題」四個字來表達我想表達的意思。

<!-- more -->

有很多人剛開始練習程式解題的時候，是從演算法與資料結構開始的。可能去找了一些書或是線上課程來看，接著從經典的開始，例如說泡沫排序、選擇排序、插入排序，再來是困難一些的合併排序以及快速排序等等。但我覺得對真正的初學者來說，學這些還太早了。

簡單來說就是：「如果你寫不出九九乘法表，你會寫 KMP（可代換成任何演算法）也沒什麼用。」如果有兩個人，A 會寫九九乘法表但寫不出 KMP，B 會寫 KMP 但寫不出九九乘法表，我一定把 B 淘汰掉。因為 B 很有可能是直接把 KMP 的寫法記起來，而不是真的理解，否則我不相信他寫不出來九九乘法表。

在這邊也誠摯呼籲各個公司在面試的時候可以考那種比較簡單的題目，有時候成效會出乎意料的好。例如說找中位數、判斷質數或是大數加法之類的，會發現有些人還真的寫不出來。

總之呢，我認為要透過程式解題來熟悉演算法是絕對沒問題的，也是很棒的一個方法，但基礎要打穩，沒有打穩的話就只是在背題目而已。

而且還有一點很重要，在真正開始解題以前，你要先理解題目並且確切掌握題目的範圍。這點很多人都會忽略，直接就動手開始解題了，這在寫白板題的時候也不是一件好事。

所以這篇我們不談解題本身，而是來談談在動手解題以前應該先做的事。底下我們先來看一個題目，來源是 [NPSC 2007 年國中組初賽](https://contest.cc.ntu.edu.tw/npsc2007/)。

## 題目名稱：不公平的人，是誰？

自從周杰倫出了新專輯「牛仔很忙」後，大郭和小郭就時常幻想自己是牛仔，終於有一天，大郭找來了兩把水槍要和小郭決鬥。 可是玩了幾場以後，小郭全身都溼透了，大郭卻是一身乾爽，隱忍許久的小郭終於發難了！

小郭：「我都噴不到你………」

大郭：「那大概是你技術差吧？」

小郭：「騙人～騙人～你一定有作弊吧？」

雖然小郭什麼都比大郭差（諸如智力、運動神經等…），但是如果在事前大郭準備給小郭的水槍比較差的話，那代表大郭是從一開始就有心把這場遊戲策畫成不公平的壞人。

剛好路過的你，被吵吵鬧鬧的兩人抓去當裁判。

### 輸入說明
輸入會是兩個字串 M 與 N。其中M代表大郭的水槍射程，N代表小郭的水槍射程，注意為求精確，所有射程的長度單位均為奈米。
因為大郭弄來的水槍是22世紀的產物，故水槍的射程非常非常遠，最長可以到達400位數的數字（射程必為一非負整數）。

### 輸出說明
對每一組測試資料，你應該回傳一個字串，該列從小郭的角度出發（小郭雖然比較笨，但還是很奸詐的！），判斷這是不是一場公平的比賽（對於小郭來說，只要大郭的射程不比小郭大，就是一場公平的遊戲）。
若是對小郭有利的遊戲，則回傳「Fair」，若不是，則回傳「Unfair」

### 範例輸入
123 456

### 範例輸出
Fair

*****

以上就是一個完整的題目，會包含題目介紹、輸入說明、輸出說明以及範例。你可能會覺得就是一個數字比大小的問題而已，但其實沒有那麼簡單。

接著我們就來看看應該要注意哪些東西。

## 1. 題目的範圍

為什麼這種程式解題的題目一定要給範圍？要回答這個問題很簡單，我們先來看看如果不給範圍會怎樣，例如說：

> 請寫出一個判斷質數的 function

你可能看到以後就批哩啪啦寫完然後就交卷了。可是因為這個題目非常不明確，所以你其實沒有辦法確認自己的答案是不是對的，例如說：

1. 是回傳 true 或 false 嗎？還是回傳字串 YES 跟 NO？
2. 如果輸入是字串怎麼辦？我需要做處理嗎？
3. 如果是小數或負數呢？需要做特別處理嗎？
4. 如果數字超過 integer 的範圍會發生什麼事？

若是沒有明確地定義輸入以及輸出，其實你根本寫不出「正確」的程式，因為也沒有「正確」這種事，所以定義輸入範圍的第一個目的就是幫你更明確地去釐清題目。

例如說一個比較好的題目會長這樣：

> 請寫出一個函式，給定一個正整數 n（1<=n<=100000），請回傳 n 是否為質數，是的話回傳 true，反之回傳 false

當題目說「給定一個正整數 n（1<=n<=100000）」的時候，代表你可以完全不管超出這範圍的情形。n 絕對不會是字串，也不會是陣列，也不會是 0，不會是小數或負數，所以不需要去理會這些 case。

順帶一提，這是很多人在面試白板題的時候會犯的錯誤，沒有把題目範圍問清楚就開始實作了。

白板題是可以跟面試官討論的，這時候你就應該把題目範圍問清楚，才開始動手解題，而且題目範圍其實也會影響到你的解法。

舉開頭的題目來說：

> 因為大郭弄來的水槍是22世紀的產物，故水槍的射程非常非常遠，最長可以到達400位數的數字（射程必為一非負整數）

以 JavaScript 為例，有些人會很天真的以為這一題是在考你兩個「數字」比大小。400 位數的數字，JavaScript 存得下嗎？存不下。

可以用`Number.MAX_SAFE_INTEGER`來取到 Number 型態能存的最大數字，連 20 位都不到，何況是 400 位。

如果題目跟你說數字是 10 位數以內，就可以直接把字串轉成數字比大小然後回傳結果。但今天數字是 400 位數，就沒辦法用 Number 這個型態。所以要嘛就是直接拿字串來比大小，要嘛就是用比較潮的 [BigInt](https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Global_Objects/BigInt) 來解。

若是題目沒有給範圍，就沒辦法決定要採取怎樣的做法。所以範圍的目的就是把題目定義地更明確，畫一條線在那邊，跟你說：「欸欸，題目範圍到這邊喔，超出界線的可以不用考慮」

## 2. 寫完之後的測試

如果是一些 Online Judge（以下簡稱 OJ）系統，平時的解題可以一直試錯，隨意寫完之後就丟上去，有錯的話再來 debug 找錯誤，沒錯的話就解下一題。

但是比賽或是有些面試的話就不一樣了，你只有一次機會，或是答錯了會有 penalty 之類的，所以要在送出答案之前自己先檢查個幾遍，確認沒什麼問題才送出。

這時候測試就很重要，基本上有幾個方法可以測試你寫出來的程式是否正確，例如說第一個，也是最簡單的一個：先拿題目給的範例測資（測試資料的簡稱）測，如果範例過不了那一定是寫錯了。

第二，如果可以的話，寫一個程式來測。這有些題目做得到有些做不到，例如說判斷質數可能就做不到，除非你去找別人寫好的判斷質數的 code 來用。但如果是上面數字比大小的這一題，針對小範圍（數字位數低於 10 位數以下）的情形就可以寫程式來測：

``` js
// 絕對是對的的數字比較
function compare(a, b) { return b >= a ? 'Fair' : 'Unfair' }
  
// 跑一萬遍
for(let i = 1; i <=10000; i++) {
  // 隨機產生資料
  const a = Math.floor(Math.random() * 1e9)
  const b = Math.floor(Math.random() * 1e9)
  // 判斷一般數字比大小以及字串比大小的結果
  // 記得這邊要轉成字串來比對
  if (compare(a, b)!== stringCompare(a + '', b + '')) {
    // 出錯，印出來哪筆資料錯誤
    console.log('error', a, b)
  }
}
```

跑個十次你就測十萬筆資料了，就能保證一些正確性。除了這樣以外，還有一點很重要：自己生測資，而且要產生那種邊界條件的測資。

## 3. 邊界條件

邊界條件通常也被稱為 boundary case、corner case、edge case 等等（最精確的定義好像不太相同，但概念上應該差不多），一言以蔽之，就是很容易讓你程式出問題的測資，要測你的程式在極端的情形之下會不會壞掉。

以上面比大小的題目為例，可能就是 `0 0`、`0 10` 這種比較少會考慮到的條件。或者是以大數加法（兩個字串當作數字相加，例如說`'123'+'123' => '456'`）為例，就會是：

1. `0 + 0`，兩個零相加
2. `0 + 9999`，加完沒有改變
3. `1 + 9999`，加完會進位

最後再舉一個判斷迴文的例子，可能就會是：

1. 空字串
2. 只有一個字的字串

這些 edge case 是很容易會欠缺考慮而出錯的地方，所以在產生測資的時候，最好是自己也要想一下有哪些 edge case 是沒有考慮到的。很多時候你沒有拿滿分，就是因為這些 edge case 沒有考慮到。

可是就算滿分，就代表真的對了嗎？

## 4. 假解的可能性

一般來說我們稱那些通過 OJ 但其實不是正確的解答為「假解」，通常會發生都是因為 OJ 上的測資太弱，所以才讓假解蒙混過關。

像是上面比大小這題，雖然題目寫說 M 與 N 最多可以到 400 位數，但有可能測資偷懶，最大只到五位數而已。在這種情形底下，你寫一個把字串轉換為數字然後比大小的解法就可以過關，但我們不會說這是正解，因為多加一筆測資答案就錯了。

或者是有些題目沒有卡時間複雜度，原本預期要 O(n) 的解法，結果用 O(n^2) 也可以過。有些假解寫了你會自己知道是假解，但有些你不會發覺。這部分其實要靠 OJ 來把關，測資必須用心產生，才能避免這種假解的狀況。

## 結論

上面的題目如果想練習的話，我之前有寫了一個非常非常陽春而且破爛的專門給 JavaScript 的 OJ 系統：[Lidemy OJ](https://lidemy-oj.netlify.com/problems/9)，在開始解題之前請先到首頁閱讀注意事項（例如說請勿使用箭頭函式之類的。

寫這篇的原因是希望剛接觸程式解題的新手們可以理解在動手解題之前，其實有更多重要的事需要去關注。記得先把題目定義清楚，才去動手解題，這個在面試考白板題的時候也是必備技能之一。

如果寫題目的時候發現題目沒有定義清楚，那這個題目或許就不是這麼好，可以跟網站反映一下，讓他們補上題目範圍。

祝大家都能在程式解題的路上找到樂趣。

關於作者： 
[@huli](https://blog.huli.tw) 野生工程師，相信分享與交流能讓世界變得更美好