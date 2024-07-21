# install nextcloud on ubuntu


sudo apt update && apt install apache2 -y
اکنون با استفاده از این دستور وضعیت آپاچی را چک کنید:

systemctl status apache2
Nextcloud با استفاده از زبان برنامه نویسی PHP نوشته شده است. به همین دلیل موارد زیر باید نصب شود:

sudo apt install -y php libapache2-mod-php php-imagick php-common php-mysql php-gd php-json php-curl php-zip php-xml php-mbstring php-bz2 php-intl php-bcmath php-gmp php-dom unzip
در ادامه apache را ریلود کنید:

systemctl reload apache2
نصب دیتابیس (MariaDB) :

در فهرست پیش‌نیازی که برای نصب Nextcloud وجود دارد، مورد بعدی دیتابیس است. انتخاب‌های متعددی برای این کار وجود دارد، از جمله PostgreSQL، MySQL، SQLite و MariaDB. این بیشتر به شما بستگی دارد. برای این مقاله، ما از MariaDB به عنوان نمونه استفاده خواهیم کرد. این دستور را اجرا کنید:

sudo apt install -y mariadb-server
پس از اتمام نصب با دستور زیر رمز عبور برای یوزر root در دیتابیس تعیین کنید:

نکته: اگر بر روی سرور تست هستید می‌توانید این کامند را نادیده بگیرید.

sudo mysql_secure_installation
مراحل کانفیگ دیتابیس را در یوتیوب و همچنین مقاله راه اندازی mariaDB دنبال کنید.

با یوزر root به دیتابیس وارد می‌شویم:

sudo mysql -u root -p
یک دیتابیس با نام دلخواه خود درست کنید.در اینجا ما اسم دیتابیس را academy می‌گذاریم:

;CREATE DATABASE academy
اکنون می‌خواهیم یک یوزر برای دیتابیس ایجاد کنیم و همچنین مجوزهای کار به آن را بدهیم. ما academy-User را به عنوان نام انتخاب کردم، اما دوباره می توانید آن را با هر چیزی که دوست دارید جایگزین کنید. همچنین رمز عبور خود را جایگزین “”your-password” کنید:

;GRANT ALL ON academy.* TO 'academy-User'@'localhost' IDENTIFIED BY 'your-password'
حالا با کامند زیر دیتابیس را refresh می‌کنیم:

;FLUSH PRIVILEGES
پس از تنظیم Apache، حالا می‌توانیم به مرحله بعدی برویم و Nextcloud را دانلود و نصب کنیم. برای این کار، برنامه به صورت یک فایل ZIP در دسترس است. ابتدا به سایت رسمی Nextcloud بروید تا آخرین نسخه را بررسی کنید. در حال حاضر، آخرین نسخه منتشر شده 28.0 است. شما می‌توانید با ورود به خط فرمان و وارد کردن دستور زیر، دانلود را آغاز کنید.

wget https://download.nextcloud.com/server/releases/nextcloud-28.0.2.zip
پس از دانلود، با دستور زیر از حالت zip خارج می‌کنیم:

sudo unzip nextcloud-23.0.0.zip -d /var/www/html
sudo mkdir /var/www/html/nextcloud/data 
sudo chown -R www-data:www-data /var/www/html/nextcloud
با موفقیت نصب به اتمام رسید!

در ادامه باید از طریق وب پنل تنظیمات مورد نیاز خود را انجام دهید

http://YOUR-IP/nextcloud/index.php
با استفاده از حساب کاربری مدیریتی خود وارد شوید. پس از ورود، به صفحه اصلی می‌روید. در این مرحله، برای دسترسی به تنظیمات و تنظیم پیکربندی‌های پایه‌ای مانند پوشه داده و اطلاعات اتصال به پایگاه داده، باید بر روی آیکون چرخ دنده در بالا سمت راست کلیک کنید. پس از تنظیم این قسمت‌ها، نصب و راه‌اندازی Nextcloud شما تکمیل می‌شود!
