**نصب پنل s-ui علیرضا با ایمیج داکر در سرور یا روتر میکروتیک**  
  
**تا چندی پیش این امکان برای ما میسر نبود که بتونیم در میکروتیک خودمون این کانفیگها رو ارائه یا از اون برای دور زدن فیلترینگ استفاده کنیم اما با روی کار آمدن پکیج کانتینر در ورژنهای 7 به بعد در میکروتیک این امر میسر شده**  

## 📺 ویدیو آموزشی
🎥 Watch the full installation and usage guide on YouTube:  
👉 [Click here to watch the video](https://www.youtube.com/watch?v=7rJgk30xIs0)  

**دستورات نصب در میکروتیک**  

**دستورات زیر را در ترمینال میکروتیک وارد کنید**  

**فعال سازی کانتینر**

/system/device-mode/update container=yes  
/system/device-mode/print    

**ساخت اینترفیس و آی پی دهی**

/interface/bridge/add name=dockers  
/ip/address/add address=172.17.0.1/24 interface=dockers  
/interface/veth/add name=veth1 address=172.17.0.2/24 gateway=172.17.0.1  
/interface/bridge/port add bridge=dockers interface=veth1  
/ip/firewall/nat/add chain=srcnat action=masquerade src-address=172.17.0.0/24   

**در صورتی که میخواهید از آی پی ورژن 6 هم استفاده کنید به اینصورت باید آی پی را در اینترفیس خود ست کنید**

ipv6:fc07:55::1/64 set to bridge interface

ipv6:fc07:55::2/64 set to veth

**کانفیگ لینک داکر ریجستری**  

container/config/set registry-url=https://registry-1.docker.io tmpdir=pull   

**لینکهای میرور داکر ریجستری برای دانلود مستقیم در سرور ایران بدون نیاز به تغییرات**  

https://docker.arvancloud.ir, https://registry.docker.ir, https://docker.host:5000, https://docker.iranserver.com, https://docker.dockerme.ir

**در نهایت ایجاد مانت**  
Mounts:  
src:/x-ui/db  
dst:/app/db  

**دانلود ایمیج در میکروتیک خودتون**  

Docker image : alireza7/s-ui:latest    
  
**چرا از این ایمیج داکر استفاده میکنیم؟**  
**سهولت استفاده از آن و پشتیبانی از پروتکلهای مختلف و مهمترین موضوع استارت مجدد اتوماتیک پنل درصورت ریبوت احتمالی سرور**

**اگر به مشکلی برخوردید میتوانید از ویدیو یوتیوب ما کمک بگیرید**  

https://www.youtube.com/@mikronet_plus  

  
