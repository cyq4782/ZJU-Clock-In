# 自动打卡教程

本程序的workflow代码灵感来源于@FurryPotato，Python打卡部分的程序实现来源于我的朋友DW。

由于本程序的实现和@FurryPotato的方法不同，因此设定过程也需要略加修改。

如果这个仓库帮到了你，也别给我给我一颗star。

首先你需要拥有一个github，直接在左上角注册就行了。

### Step1. Fork本仓库

点击本仓库的Fork

![image-20210504141421350](https://tva1.sinaimg.cn/large/008i3skNly1gq6dacfvdjj31yy0u07ed.jpg)

Fork的含义是将本仓库拷贝一份，放到你自己的github账号下，所以只有在第一次观看本教程的时候才需要fork。

然后我们可以看到，左上角这里的Di-Zhipeng已经变成了你自己账号的名字，下面标注着forked from Di-Zhipeng/ZJU-Clock-In.

![image-20210504141632691](https://tva1.sinaimg.cn/large/008i3skNly1gq6dcl2073j31h90o8jv2.jpg)

此时你已经拥有了本仓库的一个拷贝。

### Step2. 添加cookies

打开DingHealthReport.py文件，找到deal_person函数，遵循注释完成cookies提取：

```python
此函数是打卡功能的顶层函数，通过传入不同的cookies实现为多人打卡，
url_save = 'https://healthreport.zju.edu.cn/ncov/wap/default/save'
url_index = 'https://healthreport.zju.edu.cn/ncov/wap/default/index'

# 给出headers和cookies，令其可以免登录
# headers和cookies的确定方法为：
# 1. Chrome打开无痕页面，键入url_save网址，返回登录界面
# 2. 右键审查元素或者按F12，找到network栏
# 3. 输入账号密码并登录，然后找到“index”的“requests headers”一栏
# 4. 将cookie中的所有内容全部复制粘贴到116行附近的cookies1 = ‘’中，用以完成请求头。
```

### Step4. 配置微信推送

打开https://sct.ftqq.com 注册账号获取sendkey，以获得微信消息推送。

将新得到的sendkey替换程序中116行附近原有的SendKey1的值。

### Step5. 如何触发打卡？

**在触发打卡前，请确保sendkey和cookies已经更新。**

**只有单人打卡时，请删除120-122行附近的内容：**

**Line 120** cookies2 = 'xxxxx'

**Line 121** SendKey2 = 'yyyyy'  # other one

**Line 122** deal_person(cookies=cookies2, send_key=SendKey2)

触发打卡有两种方式，第一种是在自己的ZJU-Clock-In仓库里点击Star（已经Star的就取消Star，再重新点击）。

第二种是等待12小时，这个脚本是每隔12小时触发一次的。

### Step6. 如何判断打卡是否成功？

点击仓库的Action：

![image-20210504142536391](https://tva1.sinaimg.cn/large/008i3skNly1gq6dm0ix9vj327o0twteb.jpg)

每次触发打卡就会在右边多出一个记录，比如现在我已经执行过四次打卡脚本了，点击你需要查看的记录，再点击里面的ClockIn按钮，我们就可以看到本次打卡的情况了：

![image-20210504142743921](https://tva1.sinaimg.cn/large/008i3skNly1gq6do8552sj32r80r8wi9.jpg)

非计算机科学的学生只需要关注右侧ClockIn的文字提示内容就行了，点击Clock In：

![image-20210504142839755](https://tva1.sinaimg.cn/large/008i3skNly1gq6dp77angj320v0u079c.jpg)

就可以看到提示信息了，如果打卡失败，就按照提示去操作就好了。
