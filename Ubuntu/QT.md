  
  
  
`https://qt-mirror.dannhauer.de/`

```Plain
[aqt]
baseurl: https://qt-mirror.dannhauer.de/

[requests]
max_retries_on_checksum_error: 1
max_retries_to_retrieve_hash: 1
INSECURE_NOT_FOR_PRODUCTION_ignore_hash: True

[mirrors]
fallbacks:
    https://mirrors.ocf.berkeley.edu/qt
    https://qt.mirror.constant.com/
    https://ftp.acc.umu.se/mirror/qt.io/qtproject/
    https://qtproject.mirror.liquidtelecom.com/
    https://ftp.jaist.ac.jp/pub/qtproject
    http://ftp1.nluug.nl/languages/qt
    https://mirrors.dotsrc.org/qtproject
    https://mirror.yandex.ru/mirrors/qt.io
```

С зеркалом яндекса наблюдаются проблемы (не удается скачать mingw), поэтому я не стал его ставить как baseurl.

Ставить так:

```Plain
aqt -c /aqt.cfg install-qt windows desktop 5.15.2 win64_mingw81
```