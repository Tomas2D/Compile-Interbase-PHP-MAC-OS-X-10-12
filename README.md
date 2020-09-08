# Compiling Interbase/Firebird extension for PHP 5/7 under MAC OS X

Short tutorial on how to compile Firebird extension for PHP under MAC OS X El Capitan 10.11

## Update 2020-03-30

The tutorial is still working, keep in mind that this tutorial is for Firebird 2.5.x only!

<hr>

## Before compiling PHP extension you must have
- Autoconf, you can install it via Homebrew (brew install autoconf) 
- Because we needs Firebird libs. for compiling interbase, we have to download Firebird Server Package (http://www.firebirdsql.org/en/downloads), download the LIPO package (important!)


## Let's compile! (MAMP 4.1.1 ... PHP 7.1.1)

<ol>
  <li>Check which PHP version your MAMP server use, for example version 4.1.1 use PHP 7.1.1</li>
  <li>Download PHP source code from https://secure.php.net/downloads.php</li>
  <li>Unzip downloaded sources, rename it to "php" and move it to your MAMP include folder /Applications/MAMP/bin/php/php7.1.1/</li>
  <li>Enter to interbase extension folder
   cd /Applications/MAMP/bin/php/php7.1.1/include/php/ext/interbase/</li>
  <li>Run phpize with command 
   /Applications/MAMP/bin/php/php7.1.1/bin/phpize</li>
  <li>Run configure ./configure --with-php-config=/Applications/MAMP/bin/php/php7.1.1/bin/php-config </li>
  <li>Create symbolic link to Firebird ibase.h and iberror.h in our include/php folder so
   ln -s /Library/Frameworks/Firebird.framework/Headers/*.h /Applications/MAMP/bin/php/php7.1.1/include/
   ln -s /Library/Frameworks/Firebird.framework/Headers/*.h /Applications/MAMP/bin/php/php7.1.1/include/php/ext/interbase/include/
   these two header files are required</li>
  <li>Run make (for someone maybe make -j8)</li>
  <li>Run make install</li>
</ol>

You should get your interbase.so (/Applications/MAMP/bin/php/php7.1.1/include/php/ext/interbase/modules/interbase.so) ! Wooah


## Let's compile! (MAMP 3.4.0 ... PHP 5.6.10)

<ol>
  <li>Check which PHP version your MAMP server use, for example version 3.4.0 use PHP 5.6.10 by default</li>
  <li>Download PHP source code from https://secure.php.net/downloads.php</li>
  <li>Unzip downloaded sources, rename it to "php" and move it to your MAMP include folder /Applications/MAMP/bin/php/php5.6.10/</li>
  <li>Enter to interbase extension folder
   cd /Applications/MAMP/bin/php/php5.6.10/include/php/ext/interbase/</li>
  <li>Run phpize
   /Applications/MAMP/bin/php/php5.6.10/bin/phpize</li>
  <li>Run configure ./configure</li>
  <li>Create symbolic link to Firebird ibase.h and iberror.h in our include/php folder so
   ln -s /Library/Frameworks/Firebird.framework/Headers/*.h /Applications/MAMP/bin/php/php5.6.10/include/
   these two header files are required</li>
  <li>Run make</li>
  <li>Run sudo make install</li>
</ol>

You should get your interbase.so ! Wooah

## ATTENTION FOR MAMP USERS (Mac OS)

Be sure that you are not running PHP in CGI mode (you will propably get 500 error code during connection to database) !

