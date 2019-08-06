# 爬虫DebugLog：HTTPHandler() 和 HTTPSHandler()
## 边执行程序，边打印调试日志
```python
import urllib.request
httphd = urllib.request.HTTPHandler(debuglevel=1)
httpshd = urllib.request.HTTPSHandler(debuglevel=1)
opener = urllib.request.build_opener(httpshd,httpshd)
urllib.request.install_opener(opener)
data = urllib.request.urlopen("http://edu.51cto.com")
```
# 异常处理URLError
## 使用try...except URLError（父类）和HTTPError（子类）
```python
import urllib.request
import urllib.error
try:
    urllib.request.urlopen('http://blog.csdn.net')
except urllib.error.URLError as e:
    if hasattr(e,'code'):
        print(e.code)
    else:
        print(e.reason)
```
  一般来说，产生URLError的原因有如下几种可能：
  * 连接不上服务器
  * 远程URL不存在
  * 无网络
  * 触发了HTTPError
  前三种属于URLError，没有code信息；只有HTTPError才有,code信息输出
# 图片爬虫 京东
```python
import re
import urllib.request
def craw(url,page):
    html1 = urllib.request.urlopen(url).read()
    html1 = str(html1)
    pat1 = '<div id="plist".+? <div class="page clearfix">'
    result1 = re.compile(pat1).findall(html1)
    result1 = result1[0]
    pat2 = '<img width="220" height="220" data-img="1" data-lazy-img="//(.+?\.jpg)">'
    imagelist = re.compile(pat2).findall(result1)
    x = 1
    for imageurl in imagelist:
        imagename = 'D:/myweb/'+str(page)+str(x)+".jpg"
        imageurl = "http://"+imageurl
        try:
            urllib.request.urlretrieve(imageurl,filename=imagename)
        except urllib.error.URLError as e:
            print("exception")
            if hasattr(e,'code'):
                x+=1
            if hasattr(e,"reason"):
                x+=1
        x+=1
for i in range(1,79):
    url = "https://list.jd.com/list.html?cat=9987,653,655&page="+str(i)
    craw(url,i)
```
