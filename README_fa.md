[Русская версия](README.md) | [English Version](README_en.md) | [中文版](README_zh.md) | [نسخه فارسی](README_fa.md)

[صفحه‌ی نمایشی](https://legiz-ru.github.io/Orion)

# صفحه اشتراک Material Remnawave

این مخزن حاوی کد منبع صفحه اشتراک پنل پروکسی Remnawave است که با طراحی مدرن Material Design 3 ایجاد شده است. این صفحه به کاربران دسترسی راحت به اطلاعات اشتراک، دستورالعمل‌های اتصال و لینک‌ها ارائه می‌دهد. کد با کمک مدل هوش مصنوعی Claude Sonnet 4 نوشته شده است.

## ویژگی‌های کلیدی

* **طراحی Material 3:** رابط کاربری مدرن و بصری که بر اساس آخرین اصول Material Design 3 توسعه یافته است.

* **پشتیبانی از تم تیره و روشن:** تغییر خودکار یا دستی بین تم‌های روشن و تیره برای استفاده راحت در هر شرایط نوری.

* **پیکربندی انعطاف‌پذیر اپلیکیشن:** از فهرست استاندارد اپلیکیشن‌های توصیه شده برای اتصال پشتیبانی می‌کند، همچنین ادغام آسان کلاینت‌های شخص ثالث از طریق فایل [`app-config.json` قابل تنظیم](https://remna.st/docs/install/remnawave-subscription-page#custom-app-configjson-custom-apps).
* * **گروه‌های سفارشی**  
امکان اضافه کردن گروه‌های اضافی به بخش اپ‌ها از طریق فایل ادغام، [به عنوان مثال، `بخش TV`](https://github.com/legiz-ru/my-remnawave/blob/main/sub-page/multiapp/app-config.json).

*   **پشتیبانی از برندینگ:** پیکربندی لوگو و لینک پشتیبانی از طریق پارامترهای `logoUrl` و `supportUrl` در تنظیمات `app-config.json` برای شخصی‌سازی صفحه.

*   **پشتیبانی از برندینگ:** پیکربندی لوگو و لینک پشتیبانی از طریق پارامترهای `logoUrl` و `supportUrl` در تنظیمات `app-config.json` برای شخصی‌سازی صفحه.

* **کپی کردن لینک‌های جداگانه:** امکان کپی کردن لینک‌های جداگانه (مثل `vless://`, `trojan://`) مستقیماً از صفحه، علاوه بر لینک اشتراک اصلی.

* **پشتیبانی چند زبانه:** در دسترس بودن صفحه به زبان‌های روسی، انگلیسی، فارسی و چینی، با تشخیص خودکار زبان مرورگر.

## اسکرین‌شات‌ها

<div align="center">
  <img src="./screenshots/apps-sections-select.jpg" width="66%" />
  <img src="./screenshots/apps-sections.jpg" width="66%" />
  <img src="./screenshots/user-status-sections.jpg" width="66%" />
  <img src="./screenshots/settings-sections.jpg" width="66%" />
  <img src="./screenshots/sub-links-sections.jpg" width="66%" />
</div>

## نصب

1. **دانلود فایل صفحه:**
   فایل `index.html` را در همان دایرکتوری که فایل `docker-compose.yml` شما قرار دارد، با استفاده از `curl` دانلود کنید:

   ```bash
   curl -o index.html https://raw.githubusercontent.com/legiz-ru/material-remnawave-subscription-page/refs/heads/main/index.html
   ```

2.  **پیکربندی Docker Compose:**
    مسیر فایل دانلود شده `index.html` را در `docker-compose.yml` خود با mount کردن `volumes` در container `remnawave-subscription-page` مشخص کنید.

    مثال برای نصب استاندارد:

    ```yaml
    services:
      remnawave-subscription-page:
        volumes:
          - ./index.html:/opt/app/frontend/index.html
    ```

    اگر قصد استفاده از [فهرست اپلیکیشن سفارشی](https://remna.st/docs/install/remnawave-subscription-page#custom-app-configjson-custom-apps) (`app-config.json`) را دارید، `volume` مربوطه را اضافه کنید:

    ```yaml
    services:
      remnawave-subscription-page:
        image: remnawave/subscription-page:latest
        volumes:
          - ./index.html:/opt/app/frontend/index.html
          - ./app-config.json:/opt/app/frontend/assets/app-config.json
    ```

    می‌توانید از یکی از فهرست‌های اپلیکیشن سفارشی من استفاده کنید که در آدرس زیر در دسترس است: [فهرست اپ سفارشی](https://github.com/legiz-ru/my-remnawave/blob/main/README.md#remnawave-subscription-page-%D1%81lient-configuration)

3.  **راه‌اندازی مجدد container:**
    برای اعمال تغییرات، container Docker خود را مجدداً راه‌اندازی کنید:

    ```bash
    docker compose down remnawave-subscription-page && docker compose up -d remnawave-subscription-page
    ```

## تماس

  * [کانال تلگرام](https://t.me/legiz_trashbag)

## حمایت از پروژه

اگر این پروژه را دوست دارید و می‌خواهید از توسعه آن حمایت کنید، می‌توانید کمک مالی کنید:

  * [Tribute در تلگرام](https://t.me/tribute/app?startapp=drzu)
  * [TON USDT: `UQAGQTQZYCx5TWj5cmTLpo7164PFsXqZZJ6t6x88n7sHW9gU`]