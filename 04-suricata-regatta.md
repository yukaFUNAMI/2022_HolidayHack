
```
alert dns any any -> any any (msg:"Known bad DNS lookup, possible Dridex infection."; dns.query; content:"adv.epostoday.uk"; nocase; sid:1; rev:1;)
alert http any any -> any any (msg:"Investigate suspicious connections, possible Dridex infection"; sid:2; rev:1;)
alert tls any any -> any any (msg:"Investigate bad certificates, possible Dridex infection"; tls.cert_subject; content:"CN=heardbellith.Icanwepeh.nagoya"; sid:3; rev:1;)
alert http any any -> any any (msg:"Suspicious JavaScript function, possible Dridex infection";file_data; content:"let byteCharacters = atob"; sid:4; rev:1;)
```
特に何もかんがえず元のコピペしていれた。なんか1個IP指定してないけど動いたからヨシ。🐱

https://suricata.readthedocs.io/en/suricata-6.0.0/file-extraction/file-extraction.html#architecture
