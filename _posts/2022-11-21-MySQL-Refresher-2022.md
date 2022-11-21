---
title: "MySQL Refresher 2022"
date: 2022-11-21
layout: default
---

I've not looked at MySQL lately, so time for a refresh!

# Learn SQL (using MySQL) in One Day and Learn It Well - Jamie Chan

## Common Data Types

### Textual

**CHAR(size)** - fixed length string up to 255 - gets padded with spaces
**VARCHAR(size)** - variable length string - no spaces added - uses less storage but can be slower ** so should use char if fixed length **

### Numeric

**INT** -2147483648 to 2147483647
**INT UNSIGNED** - just positive
**FLOAT(m total digits,d decimal places)** - non integers - stored as approximate values - 4 bytes - accurate up to 7 decimal places
**DOUBLE(m total digits,d decimal places)** - 8 bytes so better precision - accurate up to 14 decimal places

**DECIMAL(m total digits,d decimal places)** - exact values- monetary data where precision is important

### Date and Time
**YEAR** - 2 or 4 digit format
**DATE** - YYYY-MM-DD
**TIME** - HH:MI:SS
**DATETIME** - YYYY-MM-DD HH:MI:SS
**TIMESTAMP** - converted to UTC and then back to local

