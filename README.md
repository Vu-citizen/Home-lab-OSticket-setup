<h1>Home Lab setting up technical support/help desk ticketing system Osticket from the ground up </h1>


  ### [YouTube Demonstration (@00:00)](https://www.youtube.com/watch?v=HWbCt6swSu8)


Before you start, ensure you have:

1. **Windows Server 2012** installed and configured.
2. **Administrative access** to the server.
3. A **stable internet connection**.
4. The following software installed or ready to install:
   - **IIS (Internet Information Services)**
   - **PHP** [Download PHP](https://windows.php.net/download#php-8.4)
   - **Visual Studio**  
     [Download the latest supported VC++ redistributable](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170#visual-studio-2015-2017-2019-and-2022)
   - **MySQL** or **MariaDB**  
     [Download MariaDB](https://mariadb.org/download/?t=mariadb&p=mariadb&r=11.6.2&os=windows&cpu=x86_64&pkg=msi&mirror=acorn)
   - **osTicket installation files**  
     [Download osTicket v1.18.1](https://github.com/osTicket/osTicket/releases/tag/v1.18.1)
   - **Microsoft URL Rewrite**  
     [Download URL Rewrite](https://www.iis.net/downloads/microsoft/url-rewrite)

## Step 2: Install PHP
To ensure PHP can run, first install the **Microsoft Visual C++ Redistributable**.

1. **Download and Prepare PHP**:
   - Download the **PHP Non-Thread-Safe** version from [PHP for Windows](https://windows.php.net/download#php-8.4).
   - Extract the PHP files to `C:\PHP`.

2. **Configure PHP**:
   - Rename `php.ini-development` to `php.ini`.
   - Edit the `php.ini` file to enable the required extensions:
     ```ini
     extension_dir = "C:\PHP\ext"
     extension=mysqli
     extension=gd2
     extension=imap
     extension=intl
     extension=mbstring
     extension=openssl
     extension=xml
     extension=curl
     ```
   - Save the file.

3. **Add PHP to the System PATH**:
   - Right-click **Computer** > **Properties** > **Advanced system settings** > **Environment Variables**.
   - Under **System Variables**, find `Path`, click **Edit**, and add `;C:\PHP` at the end.


4. Test PHP Configuration

 1. Create a PHP Test File
- Navigate to your web root directory (usually `C:\inetpub\wwwroot` for IIS).
- Create a new file named `info.php`.
- Open the file in a text editor (e.g., Notepad) and add the following code:
  ```php
  <?php
  phpinfo();
  ?>
- Save the file.
2. Check PHP Configuration
Open your browser and navigate to the following URL:

http://localhost/info.php


and you will see a image like this 
![image](https://github.com/user-attachments/assets/4c76f25f-fabc-41ef-879b-dcd780622adb)

This step ensures users can verify that PHP is properly installed and working.

