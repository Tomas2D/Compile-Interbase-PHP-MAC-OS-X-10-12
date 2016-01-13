# Compile-Firebird-MAC-OS-X-10.11
Short tutorial on how to compile Firebird extension under MAC OS X El Capitan 10.11

<hr>

## Before compiling PHP extension you must have
- Autoconf, you can install it via Homebrew (brew install autoconf) 
- Because we needs Firebird libs. for compiling interbase, we have to download Firebird Server Package (http://www.firebirdsql.org/en/downloads), download the LIPO package (important!)

## Let's compile!

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
