# Django-
主要是收集学习过程中遇到的问题 


2. 销售菜单增加“销售统计”功能：可以统计自定义时间的销售总额、自定义时间的个人销售额。

销售总额就是订单
可以再增加一个业务员
>>> objectList = salesOrder.objects.values('delivery').values('totalPrice').filter(delivery__lte=datetime(2017,10,18)).filter(delivery__gte=datetime(2017,10,12))
>>> list = []
>>> for i in range(len(objectList)):
...     totalPriceSum = objectList[i].get("totalPrice")
...     list.append(totalPriceSum)
...     a = sum(list)
... 
2017-10-17 15:58:46,025 DEBUG utils.execute Line:89 (0.003) QUERY = u'SELECT "sales_salesorder"."totalPrice" FROM "sales_salesorder" WHERE ("sales_salesorder"."delivery" <= %s AND "sales_salesorder"."delivery" >= %s)' - PARAMS = (u'2017-10-17 16:00:00', u'2017-10-11 16:00:00'); args=(u'2017-10-17 16:00:00', u'2017-10-11 16:00:00')
>>> list
[1, 1, 2, 1, 1, 1]
>>> a
7
>>> 
完整的代码如下：


3. 仓库增加“出库统计”功能：自定义查询商品和自定义时间的出库数量统计。商品可以多选。
>>> lo = salesOrder.objects.values('totalPrice').filter(createUser=lo)
>>> lo
2017-10-17 16:49:03,154 DEBUG utils.execute Line:89 (0.002) QUERY = u'SELECT "sales_salesorder"."totalPrice" FROM "sales_salesorder" WHERE "sales_salesorder"."createUser_id" = %s LIMIT 21' - PARAMS = (1,); args=(1,)
[{'totalPrice': 2}, {'totalPrice': 2}, {'totalPrice': 2}, {'totalPrice': 2}, {'totalPrice': 2}, {'totalPrice': 2}, {'totalPrice': 2}, {'totalPrice': 1}, {'totalPrice': 2}, {'totalPrice': 2}, {'totalPrice': 2}, {'totalPrice': 2}, {'totalPrice': 2}, {'totalPrice': 2}, {'totalPrice': 2}, {'totalPrice': 2}, {'totalPrice': 2}, {'totalPrice': 2}, {'totalPrice': 2}, {'totalPrice': 2}, '...(remaining elements truncated)...']
>>> lo = so.createUser.userprofile.id
>>> lo = salesOrder.objects.values('totalPrice').filter(createUser=lo)
>>> lo = so.createUser.userprofile.id
>>> ls = salesOrder.objects.values('totalPrice').filter(createUser=lo)
>>> ls
2017-10-17 16:50:02,711 DEBUG utils.execute Line:89 (0.002) QUERY = u'SELECT "sales_salesorder"."totalPrice" FROM "sales_salesorder" WHERE "sales_salesorder"."createUser_id" = %s LIMIT 21' - PARAMS = (1,); args=(1,)
[{'totalPrice': 2}, {'totalPrice': 2}, {'totalPrice': 2}, {'totalPrice': 2}, {'totalPrice': 2}, {'totalPrice': 2}, {'totalPrice': 2}, {'totalPrice': 1}, {'totalPrice': 2}, {'totalPrice': 2}, {'totalPrice': 2}, {'totalPrice': 2}, {'totalPrice': 2}, {'totalPrice': 2}, {'totalPrice': 2}, {'totalPrice': 2}, {'totalPrice': 2}, {'totalPrice': 2}, {'totalPrice': 2}, {'totalPrice': 2}, '...(remaining elements truncated)...']
>>> objectList = salesOrder.objects.values('totalPrice').filter(createUser=lo)
>>> 
>>> objectList = salesOrder.objects.values('totalPrice').filter(createUser=lo)
>>> list = []
>>> for i in range(len(objectList)):
...     totalPriceSum = objectList[i].get("totalPrice")
...     list.append(totalPriceSum)
... 
2017-10-17 16:55:04,524 DEBUG utils.execute Line:89 (0.002) QUERY = u'SELECT "sales_salesorder"."totalPrice" FROM "sales_salesorder" WHERE "sales_salesorder"."createUser_id" = %s' - PARAMS = (1,); args=(1,)
>>> list
[2, 2, 2, 2, 2, 2, 2, 1, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 1, 1, 3, 1, 5, 4, 4, 5, 1, 1, 2, 1, 1, 1, 1, 1, 1, 1, 1, 2, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 11, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 2, 1, 1, 2, 2, 2, 2, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 2, 1, 1, 1]
>>> sum(list)
264
>>> 

完整代码如下：

