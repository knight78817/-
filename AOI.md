AOI筆記
===========================

****
	
|Author|Howder|
|---|---|


****
## 目录
* [電路板組裝後的幾種測試方法AOI/MDA/ICT/FVT/FCT/ATE探討](#電路板組裝後的幾種測試方法AOI/MDA/ICT/FVT/FCT/ATE探討)
	* [什麼叫做（軟體）規劃](#什麼叫做（軟體）規劃)


# 電路板組裝後的幾種測試方法AOI/MDA/ICT/FVT/FCT/ATE探討
```
https://www.researchmfg.com/2011/01/board-test-strategy/

組裝電路板(PCB Assembly)的測試方法大致可以分成
AOI、ICT/MDA、FVT/FCT三大塊，
另外也有人使用X-Ray在SMT線隨線全檢，但並不普遍
```
#### AOI (Automated-Optical-Inspection)：
```
https://www.researchmfg.com/2011/11/auto-optical-inspection/

所以AOI基本上可以判斷組裝電路板上面是否有
缺件、墓碑、錯件、偏移、架橋、空焊…等不良；
缺件 (Missing) ,偏斜(Skew) ,墓碑 (tombstone) ,錯件 (wrong component),極性反 (Wrong polarity),
腳翹 (lead lift) 、腳變形(lead defective),錫橋 (solder bridge) ,少錫 (insufficient solder),假焊、冷焊
但無法無法辨識零件正下方的的焊錫性，如BGA IC或QFN IC，
至於假焊、冷焊也很難由AOI來判斷出來。

另外，如果零件的特性已經改變或有細微的外觀破裂(micro crack)也難由AOI來辨識。

一般AOI的誤判率非常高，需要有經驗的工程師調適機器一段時間之後才會穩定。
所以新板子初期導入的時候需要較多人力投入來複判AOI打下來的有問題板子是否真的有問題。
```

#### ICT/MDA (In-Circuit-Test/Manufacturing-Defect-Analyzer)：
```
傳統的測試方法。可以經由測試點來測試所有被動元件的電器特性，
有些高級的測試機台甚至可以讓待測試的電路板上電跑程式，
做一些可以由程式運行的功能測試。

如果大部分的功能都可以經由程式完成，可以考慮取消後面的FVT(功能測試)。

它可以抓出缺件、墓碑、錯件、架橋、極性反，也可以大致測出主動零件(IC、BGA、QFN)的焊性問題，
但對於空焊、假焊、冷焊問題就不一定了，因為這類的焊性問題屬於間歇性，如果測試的時候剛好有接觸到就會PASS。

它的缺點是電路板上必須有足夠的空間來擺放測試點，治具如果設計不當，會因為機械動作而損壞電路板上的電子零件，甚至電路板內的線路(trace)。

越高級的測試治具費用越貴，有些甚至高達百萬新台幣。
```

#### FVT/FCT (Function Verification Test)：
```
傳統的功能測試(FCT/FVT)方法，通常搭配ICT或MDA。
需搭配ICT或MDA的緣故是功能測試需實際上電到電路板，
如果有些電源上面的線路有短路的問題就容易發生待測板損毀的問題，
嚴重者甚至可能把電路板燒起來，有工安的顧慮。

功能測試也無法知道電子零件的特性是否符合原來的需求，也就是說無法測得產品的performance；
另外，一般的功能測試也測不到一些 by pass 的電路，這點需要考慮。

功能測試應該可以抓出所有零件的焊性、錯件、架橋、短路等問題，但By pass 電路除外，空、假、冷焊的問題也不一定可以完全測得出來。

```
