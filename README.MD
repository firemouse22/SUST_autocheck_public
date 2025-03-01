# SUST 自动打卡

- 新版本更新，更新了登陆方式，更新日期:2021/8/11
## **Uage**
code | 说明
----|----
24 | 晨检打卡
25 | 午检打卡
13 | 假期打卡

- $location$层级之间用**空格**隔开， 比如：陕西省 西安市 未央区 111县道 111县

```python
from SUSTYiBan import *
checkInByPwd('手机','密码',code,location)
```



**以下全部废弃， 可作为备选方案**
---------------
**基于易班陕科大的自动打卡**
重要的就一个类SUST类
`sust = SUST()`
还需要一个放在`SUST.py`目录下的`data.json`

## SUST类
```python
sust = SUST()
sust.run(24)        #24代表晨检
sust.run(25)        #25代表午检
```
关于SUST类就这么多，可以自行扩展
## data.json相关
```json
{
    "last_update_day": 24,              //上次更新日期
    "email_pwd": "",    //填写的话就代表开启打卡后邮箱通知，详情见|邮箱相关|
    "email":"", //发送的地址
    "data": [                           //data.json里面存放用户信息
        {
            "name": "Nick",                     //name随便填
            "id": "1421191634",                 //id随便填
            "url": "http://yiban.sust.edu.cn/v4/public/index.php?key=XD_gv0TFJHBMro/mCXr_UUZ9WaUPwyTyOjYge/aE7pVdEpgBu0M/LziSMyQqHZz8*********xpaPjueYBqQXZoANUDFbmnsDRSQZhU_udd18KbYp_S2avsT8*********CRiONjQOSQlfvmozjX09BKSCH/joik=",     //url指信息上报页面点复制链接粘贴到这
            "location": "陕西省 西安市 未央区 111县道 111县", //需要自定义地址的话，用空格隔开
            "morning_check": true,              //是否已经晨检
            "noon_check": true                  //是否午检
        }
    ]
}
```

## ！并没有实现通过账号密码登录！
开始考虑到密码透露可能涉及安全相关，并没有实现，可以自行实现。


## 如何实现全自动?
一种是:借助GitHub的Action功能可以实现在固定时间运行<br>
另一种:在某种可以全天运行的服务器或树莓派上运行