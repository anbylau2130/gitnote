SELECT * FROM (
--明细
SELECT pos.billno AS billno,
pos.bizdate AS bizdate,
posplu.plucode AS  plucode,
posplu.pluname AS pluname,
posplu.BarCode AS barcode,
posplu.salcount AS salcount,
posplu.OriPrice AS OriPrice,
posplu.FinTotal AS FinTotal,
NULL as xj,
NULL AS  elm,
NULL AS mtwm,
NULL AS wechat,
NULL AS alpay,
NULL  payplatno,
NULL  couponno,
NULL couponAmount
FROM tSalPosSal pos
LEFT JOIN tSalPosSalPlu posplu ON pos.billno=posplu.billno
WHERE pos.orgcode='2069001'

UNION ALL
--汇总
SELECT 
pos.billno AS 流水号,
pos.bizdate AS 营业日期,
'-' AS  商品编码,
'-' AS 商品名称,
NULL AS 商品条码,
SUM(posplu.salcount) AS 销售数量,
sum(posplu.OriPrice) AS 商品原价,
sum(posplu.FinTotal) AS 实收金额,
(SELECT SUM(PayTotal)   FROM tSalPosSalPay  WHERE  billno=pos.billno AND PayCode='00') as 现金,
(SELECT SUM(paytotal) FROM tsossalsale WHERE udp2 IN ('17' ,'15') AND billno=pos.billno) AS  饿了么,
(SELECT SUM(paytotal) FROM tsossalsale WHERE udp2 IN ('12' ) AND billno=pos.billno) AS 美团外卖,
(SELECT SUM(PayTotal)   FROM tSalPosSalPay  WHERE  billno=pos.billno AND PayCode=11 AND PayNo LIKE '%微信%') AS 微信,
(SELECT SUM(PayTotal)   FROM tSalPosSalPay  WHERE  billno=pos.billno AND PayCode=11 AND PayNo LIKE '%支付宝%')   AS 支付宝,
(SELECT listagg(PayNo,'|') within group (order by billno)  FROM tSalPosSalPay  WHERE  billno=pos.billno AND PayCode=11)  支付平台单号,
(SELECT listagg(PayNo,'|') within group (order by billno)  FROM tSalPosSalPay  WHERE  billno=pos.billno AND PayCode=02)  优惠券支付号,
(SELECT listagg(PayTotal,'|') within group (order by billno)  FROM tSalPosSalPay  WHERE  billno=pos.billno AND PayCode=02) 优惠券金额

FROM tSalPosSal pos
LEFT JOIN tSalPosSalPlu posplu ON pos.billno=posplu.billno
WHERE pos.orgcode='2069001' 
GROUP BY pos.billno,pos.bizdate

) a
ORDER BY a.流水号,a.商品编码 ASC




