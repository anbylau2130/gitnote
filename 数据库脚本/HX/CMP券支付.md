``` sql
SELECT 
a.billno Pos单号,
a.bizdate 单据日期,
orgcode 门店编码,
orgname 门店名称,
plu.vipcardno 会员卡号,
pay.PayNo 核销券码,
sum(plu.OriTotal) 订单金额,
pay.PayTotal 劵支付金额 ,
sum(plu.OriTotal)-pay.PayTotal 实收金额 
FROM tSalPosSal a
LEFT JOIN tSalPosSalPay pay ON a.billno=pay.billno
LEFT JOIN tSalPosSalPlu plu ON pay.billno=plu.billno
WHERE pay.PayCode='02' AND a.bizdate BETWEEN '2019-01-08' AND '2019-01-11'
GROUP BY a.billno ,
a.bizdate ,
orgcode ,
orgname ,
plu.vipcardno ,
pay.PayNo ,
pay.PayTotal 
;

SELECT 
a.billno Pos单号,
a.bizdate 单据日期,
orgcode 门店编码,
orgname 门店名称,
plu.vipcardno 会员卡号,
pay.PayNo 核销券码,
sum(plu.OriTotal) 订单金额,
pay.PayTotal 劵支付金额 ,
sum(plu.OriTotal)-pay.PayTotal 实收金额 
FROM tSalPosSal a
LEFT JOIN tSalPosSalPay pay ON a.billno=pay.billno
LEFT JOIN tSalPosSalPlu plu ON pay.billno=plu.billno
WHERE pay.PayCode='02' AND a.bizdate BETWEEN '2019-01-08' AND '2019-01-16'
AND pay.PayTotal IN (10,9.6) --优惠券金额10或者9.6
GROUP BY a.billno ,
a.bizdate ,
orgcode ,
orgname ,
plu.vipcardno ,
pay.PayNo ,
pay.PayTotal 
;﻿​
```