# 2015年7月份腾讯NextOne集训营writeup
---
#### 301、能看到吗？	隐藏在其中 http://106.75.8.230:18474/：
- 查看页面源代码，即可发现flag：flag{a2714506-b3e2-417d-bac9-e8d078ed4d96}

#### 302、加密的地址	看着有点特殊？ http://106.75.8.230:12860/：
- 查看页面源代码，即可发现flag：flag{455ec542-5f3e-4cd6-beb0-26a5e67338fe}

#### 303	看仔细了	能找出它来吗？  http://106.75.8.230:18837/：
- 查看页面源代码，发现如下信息：
```javascript
<script>
function time(){
pass='MWMzNmNkNTI=';
pass1='NDFiNzczNWV1ZmRj';
}
```
将pass和pass1用base64解码后提交登陆框得到flag：flag{dd97563d-e256-4b08-b5cb-a86ea77ade4f}

#### 304外表可是具有欺骗性的 http://106.75.8.230:16777/：
- 查看页面源代码,发现页面尾部
```javascript
<script>
&#102;&#108;&#97;&#103;&#123;&#53;&#50;&#98;&#97;&#98;&#50;&#53;&#56;&#45;&#97;&#49;&#97;&#54;&#45;&#52;&#54;&#99;&#51;&#45;&#98;&#54;&#50;&#49;&#45;&#102;&#54;&#101;&#50;&#53;&#49;&#52;&#56;&#52;&#97;&#49;&#102;&#125;
```
google搜索输入这段编码字符串,得到flag: flag{52bab258-a1a6-46c3-b621-f6e251484a1f}

#### 305	洞察力是你取胜的关键	洞察力是你取胜的关键:http://106.75.8.230:18255/:
- 查看页面源代码,发现加密的js代码:**5.js**,在线js解密得到:
```javascript
function aaa() {
	eval("32:64:39:30:61:39:30:38:31:63:62:38:64:61:63:38:61:64:65:65:61:34:63:33:61:66:30:33:34:39:32:61")
}
```
eval中字符串是ascii码,解ascii码然后md5,得到zf651q,提交口令,得到flag:flag{77f9eb43-9aeb-4502-af45-c590034d9ea9}

#### 306	统计	小明的数学作业，你能帮他完成这道题吗？http://106.75.8.230:6666/

- 上python:
```python
#!/usr/bin/env python
a=2;b=3;num=0
while True:
	c=a*b
	a=a+2
	b=b+2
	num=c+num
	if b==101:
		num=num+101
		print num
		break
```
得到结果:164251,提交得到flag:flag{84546837-a7c6-42f2-b051-412893cd060c}

#### 307	找到它！	找xx位字母或数字，取出来的值组成flag:http://106.75.8.230:16162/
- 利用对python字符串的分片:第102位:a[101:102],解得字符串:9VevF,提交得到flag:flag{b34b11c0-a614-48a8-bc81-285e64522ace}

#### 308	神奇数	有多个数字的平方的值出现了0至9的数字，而且只出现一次，从小到大，你能得到第一次出现的值吗？  http://106.75.8.230:14131/
- 上python:
```python
#!/usr/bin/env python
for i in range(int(1e9**0.5),100000):
	if len(set(str(i*i)))==10:
		print i
		break
```
解得结果:32043,提交得到flag:flag{a85c3504-8f63-4015-a516-8f4e03342e38}

#### 309	ASCII与二进制	ASCII码中表示一个字符需要____位二进制码?http://106.75.8.230:16901/
- 7位,得到flag:flag{ff978314-5f6a-43c4-a19d-87b418db207f}

#### 310	算算二进制	20位二进制无符号整数的数值范围是0到____http://106.75.8.230:19862/
- 2**20-1=1048575,提交得flag:flag{40702d9e-0d07-48a0-b1c9-f7e19f4fd45d}

#### 311	你会吗？	一般将多个中断触发器组合为中断寄存器，而整个中断寄存器的内容称为____  http://106.75.8.230:11592/
- 中断字,得到flag:flag{ec24d534-218e-4477-b045-b1033efb89a8}

#### 312	残缺的base64	这个编码缺失一个字符，你能还原它吗?http://106.75.8.230:17048/
- 找到一个在线base64解密网站:http://www1.tc711.com/tool/BASE64.htm,先猜测a,解密后得到结果:镜花場月,猜测加密的文字为:"镜花水月",解base64得到r,提交得到flag:flag{7eef569a-0e3a-4036-9965-22830e250eae}

#### 313	错误的md5	小明修改这段字符，不小心弄错了，能还原出正确的吗?http://106.75.8.230:16371/
- md5中第一个l改为1,在cmd5解密得到"企鹅",提交得到flag:flag{9b8eaec9-e46c-438c-81f8-b39e45c4b490}

#### 314	就差一步	这段字符代表着什么  http://106.75.8.230:19185/
- rot13加密,在线http://rot13.de/index.php,解得flag:flag{91b19e02-4fb7-45b6-a59b-4edac2b1d2ad}

#### 315	这句话有点意思！	这句话有点意思!http://106.75.8.230:10542/
- 培根密码,下面这句话转化为:
**ABAAB AABAA ABBAA ABBAA AAAAA BAAAA AAAAB**
找到一个在线解密网站:http://rumkin.com/tools/cipher/baconian.php
解密得到:kennarb,提交得到flag:flag{faa8b1fd-0834-47fe-a019-3f6ab36ef510}

#### 317	flag呢	flag在哪呢？下载看看吧! http://static2.ichunqiu.com/icq/resources/ctf/txap/f3ebebb23ec22139b47c7fac3d426540.rar
- wireshark打开,搜索关键字flag,得到flag{你自己看着办}

#### 318	万中有一	下载查看这个文件，数据中有你想要的。 http://static2.ichunqiu.com/icq/resources/ctf/txap/03578311d34dbef90b5b650f0f5992cf.rarhttp://static2.ichunqiu.com/icq/resources/ctf/txap/03578311d34dbef90b5b650f0f5992cf.rar
- wireshark打开数据包,发现一个html网页,fllow tcp stream后可以看到flag:
flag{6c0d68b0-c638-4fb5-a8f5-fdc756daf7e0}

#### 319	大黑阔	内有玄机，不信你就下载看看吧。 http://static2.ichunqiu.com/icq/resources/ctf/txap/cd6dc72138113c305f30f67bd54b7131.rar
- wireshark打开数据包,发现有如下谈话内容:
解析出数据包：(response) hi
```
(post) i am here ,what?
(response)next week
(response)we can go somewhere to have a rest
(response)where are you going
(post)i don't have idea (854)
(post)i don't have idea (893)
(response)how about tangshang
(post)but i was born in tangshan
(response)wow...
(post)how about tianyahaijiao?
(post)sounds like not bad
(post)where is that？
(response)i do not know
(response)i can check in my map img
(post)it's a place with water
(re) then 
(post)i can not swim
(re)god
(post)then you don't want go anywhere?
(post)i have mo idea
(response)how about wangsicong 100? 15:41:36
(post)what meaning?
(re) guominlaogong.
(re)lol
(post) what is 100
(re) his family has alot of building,you know(15:44:44)
(post) yes
(post)but i really do not know the way
(post)can you show me the in the map
(re) Ok
(re)upload to me
(post)OK 
(post) 中国地图(package no.14056)
(post)see that?
(re) yes
(response)well
(post) en
```
导出图片:图片放大锐化处理后发现flag：得到flag:flag{@G00d_L4ck_H3r3@}

#### 328	整站我也能看到	没有漏洞?  http://106.75.8.230:19209/
- 打开url,发现网站只给了一个图片,查看源代码和隐写分析,发现没问题.看到提示:"a gift for you,can you find it."猜测网站上存在一个gift的文件,写了一个脚本跑:
```python
#!/usr/bin/env python
import requests
val=['php','txt','jpg','flag','zip','rar','sql']
for a in val:
	url='http://106.75.8.230:19209/gift.'+a
	req=requests.get(url)
	if req.status_code==200:
		print 'find url:'
		print url
```
找到gift.rar,file命令看到是zip文件,解压得到flag:flag{2d33a69d-411f-411a-8da4-238c8adeb4fb}

#### 329	登录	不仅仅是登录  http://106.75.8.230:10211/
- 打开链接,发现是登陆框,参数注入常用的注入语句,发现没有反应,看源代码,发现action="",郁闷了好久.猜测网站目录下可能有数据库文件,猜解Less_6.sql等,最后找到sql.sql文件,打开得到flag:flag{44f49248-d10e-40c0-976a-3b45b184f04e}

#### 330	flag在哪里?	当你上传成功的时候就会得到flag。 http://106.75.8.230:15610/
- 找到类似的内容:http://drops.wooyun.org/tips/3603,上传图片,brupsuite抓包,利用文件名大写PHP绕过,即可得到flag

#### 331	执行!	据说执行命令就能看到flag http://120.132.85.112:4436/
- 远程管理系统，尝试注入,百度了一下资料，尝试注入点：
*Username: '|0||' / Password: 1*,成功,使用linux命令进入flag文件夹cat得到falg:
flag="flag{76c78577-6e75-420d-8837-a44613bb5f3a}

#### 332	弹弹弹	flag是弹出来的  http://106.75.8.230:16611/
- XSS漏洞 ,框内输入a,查看源代码,得到
`<script>window.alert("好像不对呢")</script>`,继续输入:`<script>window.alert("flag")</script>`,提交得到
flag{c0a8ed72-7af9-4444-a880-47b8f444b9d4}

#### 333	就在其中	文件是可以被“调用”的。  http://106.75.8.230:12866/
- 打开链接,得到提示:"找到当前文件夹下的flag文件(php),文件名为4位数字的file",brupsuite爆破,得到文件为1234.php,打开为空白页.一直不知道原因,最后找到*http://www.jinglingshu.org/?p=1853*,构造url:*http://106.75.8.230:12866/?file=php://filter/convert.base64-encode/resource=1234.php*,得到**PD9waHAgDQovL2ZsYWd7M2I0NTZlMDAtOTU0Yi00MjkwLTkyZWItOTY2ZTM4NzUwNDc3fTs/Pg0K** ,base64解密得到flag:flag{3b456e00-954b-4290-92eb-966e38750477}

#### 334	瞒天过海	可以欺骗所有人!  http://106.75.8.230:11298/
- 输入测试账号test,密码test,成功登陆,提示权限不足.brupsuite抓包,抓到cookie里有token:token=ad0234829205b9033196ba818f7a872b,cmd5解密得到test1.尝试用admin/test登陆,将token改为admin1的md5加密形式,得到flag:flag{7733138d-8f8e-4c42-b4c1-5e3e003f6502}

#### 335	摄影师的家	摄影师的服务器上放了一份特殊的文件，需要你取出来？ http://106.75.20.68/
- 打开链接,发现后台地址:http://106.75.20.68/admin,一开始发现发现
*%><%Y=request(“hacker”)%><%...*,有一句话木马痕迹,发现http://106.75.20.68/1.asp,可以登陆服务器,在网站上传目录下有发现一个webshell.asp,登陆webshell,在服务器桌面上得到flag.txt文件,得到flag.
