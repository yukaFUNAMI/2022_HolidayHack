
A1 http

A2 app.php

A3 687

A4 192.185.57.242

A5 Ref_Sept24-2020.zip

![image](https://user-images.githubusercontent.com/6504854/210536351-1dcaccdb-9bfc-463e-b575-88bb13063072.png)

A6 Ireland,Israel,South Sudan,United States of America

tshark -r suspicious.pcap -2R "tls.handshake.type == 11" -T json -n -V -J "tls" | grep -i Country | sort | uniq

A7 Yes

pcapざっとみるとHTTPの通信してるので、httpパケット->follow->HTTPで見てみつかる。Q6だけtshark。

A6は例のとおりカンマのあと半スペースが必要。
