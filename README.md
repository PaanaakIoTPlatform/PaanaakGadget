# PaanaakGadget

گجت پاناک ،یک گجت آموزشی شامل یک esp32،دو رله و دو کلید ،یک مانیتور به همراه یک onewire است که برای اهئاف آموزشی طراحی شده است.

شماره پین‌ها همگی برروی برد مشخص شده و میشود به راحتی  از آنها در درون برنامه استفاده کرد
# Contents

1. [Paanaak Class](./README.md#paanakgadet-class)

2. [sample 1](./README.md#sample-1)

3. [sample 2(Using Tft Lcd)](./README.md#sample-2-using-tft-lcd)
    
    3.1 [main code](./README.md#main-code)
    
    3.2 [St7735 Tft Library](./README.md#st7735-tft-library)
4. [sample 3 (simple Thermostat)](./README.md#sample-3-thermostat)

5. [sample 4 (Temperature Monitoring)](./README.md#sample-4-temperature-monitoring)

    5.1 [main code](./README.md#main-code-1)
    
    5.2 [Paanaak IOT Platform](./README.md#paanaak-iot-platform)
   
    5.3 [microWebSrv](./README.md#microwebsrv)

    5.4 [WebServer](./README.md#webserver)



# PaanakGadet Class

این کلاس حاوی تمامی پین‌ها،و توابعی است که بصورت مکرر از آنها حین برنامه نویسی استفاده خواهد شد که به منظور سهولت استفاده در یک کلاس جدا قرار داده شده‌اند.

در نمونه کدهایی که در پایین آمده اند نیز ما از کلیه توابع  این کلاس استفاده کرده ایم

# Sample 1
این نمونه صرفا جهت تست رله‌ها،کلید و ledها میباشد.

# Sample 2 (Using TFT LCD)
## main code
 این نمونه دما با استفاده از سنسور دمای وصل شده به گجت خوانده میشود و با فشردن دکمه ها رله های دستگاه خاموش و روشن میشوند
## St7735 TFT Library
در این نمونه از یک مانیتور tft ST7735 نیز استفاده شده است
.
لایبرری این مانیتور توسط شرکت دستخوش تغییرات فراوانی شده اما اصل این لایبرری از [اینجا](https://github.com/GuyCarver/MicroPython/tree/master/lib)
گرفته شده است.

تمامی اطلاعات مربوط به لایبرری درون فولدرLCD قرار گرفته اند.

فارغ از جزئیات ماژول ST7735 ،برای استفاده از این مانیتور کافیست سه آبجکت `tft`و`wr`و`font`را از ماژولLCD در برنامه اصلی خود import کنید:

```python
from LCD.lcdInit import tft,wr
from LCD.iransans12 import font12
```
اگر میخواهید که عکس هم بر روی lcd قرار دهید باید تابع `showBmp` را نیز import کنید:
(این تابع نیز از [اینجا](https://github.com/boochow/MicroPython-ST7735) 
رفته شده است.)
```python
from LCD.ShowBmp import showBmp
```


# Sample 3 (Thermostat)

این برنامه یک نمونه بسیار ساده از یک ترموستات است که ابتدا دما خوانده میشود و سپس اگر این مقدار از حد دما(thresold) بیشتر بود رله روشن و در غیر اینصورت رله خاموش خواهد شد.
حد دما نیز به وسیله دو دکمه گجت قابل تنظیم خواهد بود

# Sample 4 (Temperature Monitoring)

## main code

این برنامه ابتدا دمای محیط را با استفاده از سنسور میخواند، وسپس هر 30 ثانیه یکبار مقادیر را به پلتفرم پاناک ارسال میکند.(این مقادیر از طریق سایت پلتفرم قابل مشاهده هست).

برای فعالسازی وب سرور به منظور ذخیره تنظیمات وایفای نیز در ابتدای شروع برنامه میبایست کلید اول نگه داشته شود.
## Paanaak IOT Platform

در این برنامه از [پلتفرم هوشمند پاناک](https://panel.paanaak.net/) برای ارسال مقادیر دما به سایت استفاده شده است.

آموزش کار با پلتفرم را نیز میتوانید از طریق [این ویدیو](https://www.aparat.com/v/I9y5R) مشاهده نمایید.

## microWebSrv

در این برنامه از یک وب‌سرور کوچک نیز استفاده شده است.این وب سرور با نگه داشتن کلید اول گجت در هنگام روشن شودن دستگاه فعال میشود. با اتصال به این وب سرور (با وارد کردن ip دستگاه در مرورگر) میتوان اسم و رمز وایفای را برای اتصال دستگاه به اینترنت وارد کرد.

وب‌سرور استفاده شده در این برنامه از [اینجا](https://github.com/jczic/MicroWebSrv) گرفته شده است.

## WebServer
این ماژول درحقیقت پیاده سازی وب سرور هست که در آن routeهای وب سرور نوشته شده وتوابع مربوطه در آن قرار گرفته اند.
کلیه فایلهای مربوط به صفحات webserver در پوشه `www` در این sample قرار گرفته اند.


