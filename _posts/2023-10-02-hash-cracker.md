---
title: "Password Hash Cracker"
date: 2023-02-13
categories:
  - Tools
  - Cracker
---
I put this script here, in case you have problems cracking passwords with hashcat or jhon, this script can be useful for you.

```ruby
from werkzeug.security import check_password_hash

hashes = open('hashes', 'r')
for hashl in hashes:
    hash = hashl.split(":")[1].strip()
    user = hashl.split(":")[-2].strip()

    with open('/usr/share/seclists/Passwords/Leaked-Databases/rockyou.txt', 'r', errors='ignore') as file:
        for line in file:
            password = line.strip()
            if check_password_hash(hash, password):
                print(f"[\033[1;32m+\033[1;37m] Valid credential: {user}:{password}")
```

To use this script, we simply place the hashes in a txt file, and then run the script.
<div align="center"><img src= "/writeimgs/hashcracker/crack1.png">

<img src= "/writeimgs/hashcracker/crack2.png">
