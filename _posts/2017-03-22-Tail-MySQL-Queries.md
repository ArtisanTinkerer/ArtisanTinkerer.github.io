---
layout: default
title: "Debugging MySQL Queries"
date: 2017-03-22
---

I find this really useful, when trying to track what queries are being executed. **(On your dev box!)**

Execute ```SET GLOBAL log_output = 'TABLE';```

Execute ```SET GLOBAL general_log = 'ON';```

Take a look at the table mysql.general_log

**If you prefer to output to a file:**

```
SET GLOBAL log_output = "FILE"; which is set by default.
SET GLOBAL general_log_file = "/var/log/mysql/logfile.log";
SET GLOBAL general_log = 'ON';
```

You may find that you don't have permission to this using you SQL tool.
Drop to a terminal and ```mysql -u root```

You can now do:
```
tail -f logile.log
```




Note: my config file is in /etc/my/conf

Stolen from here:

(http://stackoverflow.com/questions/650238/how-to-show-the-last-queries-executed-on-mysql)[http://stackoverflow.com/questions/650238/how-to-show-the-last-queries-executed-on-mysql]
