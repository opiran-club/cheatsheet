برای نصب در لینوکس‌هایRedHat Based مثل Rocky Alma CentOS:
```
sudo yum install mariadb-server
```
و برای نصب اون در ubuntu و debian

```
sudo yum install mariadb-server
```
توجه داشته باشید که در بعضی‌ از توزیع‌های لینوکس، پس از نصب MariaDb به صورت پیش فرض ران نمی‌شود و بایدبا استفاده از دستورات زیر آن را start و enable کنیم.

```
sudo systemctl start mariaDB
sudo systemctl enable mariaDB
```
و در پایان دستور زیر را برای مطمئن بودن از فعال بودن آن دستور زیر را وارد می‌کنید

```
sudo systemctl status mariaDB
```
که باید خروجی آن چیزی شبیه عکس زیر باشد:

پس از اینکه مطمئن شدیم MariaDB سرور فعال است با استفاده از دستور زیر یک پسورد برای آن ست می‌کنیم، چرا که MariaDB در بدو نصب بدون پسورد می‌باشد.

```
sudo mysql_secure_installation
```
پس از اجرای این دستورات سوالاتی از شما پرسیده میشود که طبق ویدئو آموزشی در یوتیوب به این سوالات پاسخ دهید.

نحوه اتصال به MariaDB به دو صورت از طریق خط فرمان و محیط گرافیکی امکان پذیر است. که به ترتیب زیر آنها را نصب می‌کنیم:

۱) نصب CLI:

برای نصب در لینوکس‌هایRedHat Based مثل Rocky Alma CentOS:
```
sudo yum install mariadb-client
```
و برای نصب اون در ubuntu و debian

```
sudo yum install mariadb-client
```
۲) نصب محیط گرافیکی تحت وب به اسم PHPmyadmin

برای نصب در لینوکس‌هایRedHat Based مثل Rocky Alma CentOS:

```
sudo yum install phpmyadmin
```
و برای نصب اون در ubuntu و debian

```
sudo yum install phpmyadmin
```
کار با CLI:

```
mysql -h127.0.0.1 -P3306 -uroot -p
```
برای برقراری ارتباط به میسقل سرور از دستور زیر استفاده کنید

mysql : ابزار خط فرمان MariaDB

h- : سروری که MariaDB در آن نصب است.

-P : پورت MariaDB که .۳۳۰۶

u- : کاربر MariaDB که root کاربر پیش فرض می‌باشد.

p- : پسورد

توجه داشته باشید، در صورتی‌ که هم server و هم clint روی یک سرور نصب هستند. استفاده از پارامتر های h- P- u- الزامی نیست، و به سادگی‌ با دستور mysql می‌توان وارد MariaDB CLI شد.

کار با PHPmyAdmin:

برای استفاده از PHPmyAdmin، ایپی سرور phpmyadmin/ را به صورت زیر در مرور گرم خود وارد کنید و صفحه ورود به MariaDB را مشاهده می‌کنید. از نام کاربری root و پسوردی که در زمان نصب ایجاد کردید برای ورود استفاده کنید.

http://your-IP/phpmyadmin
توجه داشته باشید که در بیشتر مواقع phpmyadmin بسته‌های مورد نیز را برای شما نصب و تنظیمات وب سرور را به صورت اتوماتیک انجام میدهد. اما در بعضی‌ موارد خاص نیاز است بعضی‌ بسته‌ها و تنظیمات وب سرور به صورت دستی‌ انجام شود.

همچنین بدون ست کردن پسورد برای MariaDB امکان ورود به PHPmyadmin را ندارید.


---------------------------------------------------------------------------
## MariaDB cheatsheet


# Create db
CREATE DATABASE 'testDB';

# Create user on localhost
CREATE USER 'user1'@localhost IDENTIFIED BY 'password1';
# for all hosts
CREATE USER 'user1'@'%' IDENTIFIED BY 'password1';

# Grant all privileges on all dbs
GRANT ALL PRIVILEGES ON *.* TO 'user1'@localhost IDENTIFIED BY 'password1';
# Grant all privileges on single db
GRANT ALL PRIVILEGES ON testDB.* TO 'user1'@localhost IDENTIFIED BY 'password1';
# Important to flush
FLUSH PRIVILEGES;

# Check grants for user
SHOW GRANTS FOR 'user1'@localhost;

# Remove user
DROP USER 'user1'@localhost;

# Check remote users
SELECT User, Host FROM mysql.user WHERE Host <> 'localhost';

# User to access from local lan
GRANT ALL PRIVILEGES ON *.* TO 'root'@'192.168.100.%' IDENTIFIED BY 'my-new-password' WITH GRANT OPTION;
