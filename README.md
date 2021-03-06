## Foolz\Inet

This [Composer](http://getcomposer.org) package contains a class two static functions to convert IPs from presentation to decimal. It works both for IPv6 and IPv4.

It's especially useful to store the IP in databases without having to resort to strings that may be much slower to match against.

Based on an [answer](http://stackoverflow.com/a/1271123/644504) to [this question on StackOverflow](http://stackoverflow.com/questions/1120371/how-to-convert-ipv6-from-binary-for-storage-in-mysql).

The author who shared the code is [Sander Marechal](http://stackoverflow.com/users/103202/sander-marechal). Content posted on Stackoverflow is under [CC BY-SA 3.0 License](http://creativecommons.org/licenses/by-sa/3.0/).

#### Requirements

* [BCMath](http://php.net/manual/en/book.bc.php) (preferred) or [Math_BigInteger](http://pear.php.net/reference/Math_BigInteger-1.0.0RC2/Math_BigInteger/Math_BigInteger.html) (untested)
* PHP 5.3+

#### Adapters

Not necessary at all, but there's an adapter for FuelPHP 1.x to be used as package.

#### Usage

	$decimal_ip = \Foolz\Inet\Inet::ptod($ip);

	$ip = \Foolz\Inet\Inet::dtop($decimal_ip);

#### Store it in MySQL

Instead of using a `varchar` column, create a `decimal (39,0)` column that will store the entire length of the number. Enjoy better matching speed than you would have with `varchar`.