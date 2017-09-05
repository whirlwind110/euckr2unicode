# euckr2unicode

韩国文字编码EUC-KR转Unicode

一般注入韩国网站，遇到EUC-KR编码，同时用UNICODE等函数注出，可以包含这个文件，然后用数组输出。

```

<?php
function unicode_to_utf8($unicode_str) {
	$utf8_str = '';
	$code = intval(hexdec($unicode_str));

	$ord_1 = decbin(0xe0 | ($code >> 12));
	$ord_2 = decbin(0x80 | (($code >> 6) & 0x3f));
	$ord_3 = decbin(0x80 | ($code & 0x3f));
	$utf8_str = chr(bindec($ord_1)) . chr(bindec($ord_2)) . chr(bindec($ord_3));
	return $utf8_str;
}
include 'euckr2uni.php';

echo unicode_to_utf8($euckr['8147']);

```
