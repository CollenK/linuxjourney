# رابط‌های شبکه

## محتوای درس

یک رابط شبکه در واقع چگونگی ارتباط بین سخت‌افزار و نرم‌افزار شبکه را مشخص
می‌کند. نمونه‌ای از این بحث را قبلا دیده‌ایم:


```
pete@icebox:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 1d:3a:32:24:4d:ce  
          inet addr:192.168.1.129  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fd60::21c:29ff:fe63:5cdc/64 Scope:Link
```

## دستور iconfig

ابزار `ifocnfig` امکان تنظیم رابط شبکه را برای ما فراهم می‌کند. اگر هیچ رابط
شبکه‌ای تعریف نکرده باشیم‌، درایور‌های سخت‌افزار و شبکهٔ کرنل‌، نخواهند توانست با
یکدیگر ارتباط برقرار کنند. `ifconfig` در زمان بارگذاری سیستم اجرا شده و از طریق
فایل‌های config رابط‌های شبکه را آماده می‌کند، همچنین در صورت نیاز ما می‌توانیم آن‌ها
را بسته به هدف‌، تغییر دهیم. خروجی `ifconfig` در سمت چپ شامل نام رابط و در سمت
راست شامل اطلاعات مربوط به آن رابط می‌شود. عموما در هنگام نام گذاری رابط‌های شبکه
از اسامی‌ای مشابه با eth0 (اولین کارت اترنت روی ماشین)، wlan0 (رابط شبکهٔ بی‌سیم) و
یا lo (رابط loopback) استفاده می‌شود. رابط loopback برای نمایش کامپیوتر خودتان
استفاده می‌شود و درخواست‌ها را به سمت خودتان بر می‌گرداند که برای دیباگ کردن و
اتصال به سرور‌هایی که به صورت لوکال اجرا می‌کنید کاربردی است.

وضعیت رابط‌ها می‌تواند up یا down باشد و همانطور که احتمالا حدس می‌زنید‌، اگر
بخواهید رابطی را خاموش کنید، کافیست آن را به حالت down در آورید. بخش‌هایی از
خروجی `ifconfig` که احتمالا بیشتر مورد توجه‌تان است‌، HWaddr (آدرس MAC رابط)، inet
(آدرس IPv4) و inet6 (آدرس IPv6) هستند. البته احتمالا می‌بینید که مقدار subnet mask و
آدرس broadcast نیز در این خروجی نشان داده شده‌اند. همچنین می‌توانید اطلاعات مربوط به رابط‌ها
را در `‎/etc/network/interfaces` مشاهده کنید. 

### چگونگی ساخت یک رابط و روشن کردن آن

```$ ifconfig eth0 192.168.2.1 netmask 255.255.255.0 up```

این دستور آدرس IP و netmask مشخص شده را به رابط `eth0` الساق می‌کنند و این اینترفیس را روشن می‌کنند. 

### خاموش و روشن کردن یک رابط


```
$ ifup eth0
$ ifdown eth0
```

### دستور ip

دستور `ip` همچنین به ما اجازهٔ دستکاری ساختار شبکه را می‌دهد. بسته به توزیع مورد
استفاده شما ممکن است استفاده از این دستور راه حل توصیه شده برای تنظیم شبکه باشد. 

در ادامه مثال‌هایی از کاربرد این دستور را بررسی می‌کنیم:

#### مشاهدهٔ اطلاعات مربوط به تمامی رابط‌ها

```
$ ip link show
```

#### مشاهده آمار اسفتاده از یک رابط

```
$ ip -s link show eth0
```

#### مشاهدهٔ آدرس‌های IP اختصاص داده شده به رابط‌های

```
$ ip address show
```

#### خاموش یا روشن کردن رابط‌ها
 
```
$ ip link set eth0 up
$ ip link set eth0 down
```

#### اختصاص یک آدرس IP به یک رابط شبکه

```
$ ip address add 192.168.1.1/24 dev eth0
```




## تمرینات

وضعیت یک رابط شبکه را به خاموش یا روشن تغییر دهید. 

آیا می‌ةوانید وضعیت رابط شبکه را هم با دستور ifconfig و هم دستور ip تغییر دهید؟


## سوال آزمون

کدام دستور برای تنظیم رابط‌های شبکه مورد استفاده قرار می‌گیرد؟

## پاسخ آزمون

ifconfig