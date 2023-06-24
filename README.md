# China-Motor-Luxgen-Hyundai

#### Preface
考慮疫情為短期車輛領牌數波動因子，我們與廠商討論後，決定聚焦於疫情前的領牌數  
Training Dataset(2012/1~2017/12) ： 60筆  
Testing Dataset(2018/1~2019/12)  ： 24筆  
Output：各品牌領牌數 = 全市場汽車銷售量預測 x 各品牌市占率預測

#### Model
由於上述為時間序列資料，選用Sarima模型，並使用R語言。

#### Variables Relation 變數相關性檢定

#### Feature Processing
1. 標準化：針對過大或過小的數值scale，確保fit時不會影響過於劇烈。
2. Dummy：根據廠商給予的每月有無促銷活動資料建立一個(0：無；1：有)的List，且fit進去模型
3. 斷點處理：時間序列走勢劇烈的轉換點即為斷點，有可能會影響到時間序列的預測，在此也考慮

#### Luxgen
外生變數：標準化人均收入、標準化領先指數、失業率、失業人數、斷點序列
預測MAPE：35.7%

#### Hyundai
外生變數：標準化油價、標準化 CPIT、標準化人均收入、標準化失業人數、斷點
預測MAPE：9.18%

#### Conclusion
1. Luxgen加入一個斷點，落差的原因是由於當時推出的S3和U5引擎會不正常積碳從而導致車輛抖動、車輛無預警熄火，因此召回修理，導致消費者對於此品牌產生疑慮，模型來不及修正，但可見2018年9月以後的預測就很符合實際情形。
2. Hyundai加入兩個斷點，可以看到在2018年的3、4月預測是準確的，在2019年3、4月時針對Elantra舊換新以及免費升級多媒體影音系統的優惠內容，成功帶動領牌數上升。
