# 更新
 - update ALISMS_GATEWAY address from 'sms.aliyuncs.com' to 'dysmsapi.aliyuncs.com'
 - update interface version from '2016-09-27' to '2017-05-25'
 - update action param from 'SingleSendSms' to 'SendSms'
 - update query param from 'RecNum' to 'PhoneNumbers', from 'ParamString' to 'TemplateParam'
 - more ref see aliyunsdkdysmsapi/request/v20170525/SendSmsRequest.py

# 阿里云短信服务接口
一个很简单的发送短信接口，该接口针对官方提供的短信API进行了封装，我只用到了发送单条短信功能，所以就写了这些，日后需要再增加。该接口适用python3，依赖requests包，并且作为flask的功能模块适用。

## 使用方法
在flask的config文件中加入下面的配置

```python
# 可选XML
ALIYUN_API_FORMAT = "JSON"
# 阿里云的access key id
ALIYUN_API_KEY = ""
# 阿里云的access secret
ALIYUN_API_SECRET = ""
# 区域,可选
ALIYUN_API_REGION_ID = ""

ALISMS_GATEWAY = "https://dysmsapi.aliyuncs.com"
ALISMS_SIGN = "签名"
ALISMS_TPL_REGISTER = "SMS_xxxxxx"
```
## 示例
```python
# :param app: flask app
sms = AliyunSms(app)
# :param phone: 手机号
# :param sign: 短信签名
# :param template: 短信模板
# :param params: 模板变量
# sms.send_singe(phone, sign, template, params)
sms.send_single("186xxxxxxxx", app.config["ALISMS_SIGN"], app.config["ALISMS_TPL_REGISTER"], {"code": 234232})
```
