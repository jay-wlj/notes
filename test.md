# 浑天仪api文档
----


# 协议说明

请求及响应体均采用json格式。响应格式为ok_json。
请求成功返回200,失败返回4xx,5xx并返回相应的JSON。


# 域名及测试环境

* 正式域名待定
* 开发环境域名：172.17.6.140 open-goods.yunbay.com

### ok_json格式说明：

ok_json主要有三个字段，ok, reason, data。其中：
* ok 为true表示服务成功。ok为false表示服务失败。
* reason中是失败原因(当ok=false时)，或为空(ok=true时)。
* data 为接口返回的数据，具体接口会不一样。可为空。
* 示例：OK_JSON

```
{"ret": 200000,
"msg": "请求成功",
"data": {}}
```

以下接口中，响应数据只列出data部分，ok_json部分不再列出。
* 下面是通用的数据字段说明：
* 特别说明：如果接口返回是字段中无特殊说明时，create_time、update_time代表如下意思：
字段 | 类型 | 是否可为空 | 说明
:--- | :---  | :---  | :--- 
create_time | string | 否 | 创建时间
update_time | string | 否 | 更新时间

* 获取列表时，data字段如下：
字段 | 类型 | 是否可为空 | 说明
:--- | :---  | :---  | :--- 
total | int | 否 | 总记录数
list_ended | boolean | 否 | 是否已结束，false：未，true：已
list | array | 否 | 列表数据 


# cmdb相关接口
### 通知应用id下ecs变化接口
* URL: http://$host/api/jog/notify_cmdb_apps
* 是否需要签名：否
* 是否需要登录：否
* 请求参数(GET参数)：无
 字段 | 类型 | 是否可为空 | 说明
:--- | :---  | :---  | :--- 
app_ids | array(int64) | 是 | 应用id列表

* 响应：OK_JSON


# prometheus相关接口

### prometheus通知的报警消息
* URL: http://$host/api/alert/event/prometheus/{appkey}
* 是否需要签名：否
* 是否需要登录：否
* 请求参数(GET参数)：

字段 | 类型 | 是否可为空 | 说明
:--- | :---  | :---  | :--- 
- | hookV1.HookMessage | 否 | hookmsg对象

  
* 响应：OK_JSON







