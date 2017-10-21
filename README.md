# OpenSourceExperience
前后台接口  
# 创建订单 
## 入参
航班号 String（去）  
仓位 string  

航班号 String（回）  
仓位 string    


## 出参  
创建是否成功 boolean


# 查询所有订单 pojo数组
## 入参  
无 
## 出参  
订单号  string
航班号 String    
名称：显示起始目的地  string  
航班日期时间 string    
仓位 string 
金额 long   
订单生成时间 string  
状态: 未支付 (支付)-> 已支付、已退款  int  (0 1 2）

# 支付
## 入参  
订单号 string

## 出参  
是否支付成功 boolean


# 退款
## 入参  
订单号 string  

## 出参  
是否退款成功  boolean  

# 删除订单
## 入参  
订单号  string  

## 出参  
是否退款成功  boolean




# 后台数据库表结构
机票订票表格（huaweiairoder）
订单号  string
航班号 String    
订单生成时间 string  
状态: 未支付 (支付)-> 已支付、已退款  int  (0 1 2）
