---
layout: default
title: "Laravel Database Connections On The Fly"
date: 2017-07-20
---

OK, so we know that you can have multiple database connections in your .env but what if you want to be more dynamic than that?

I had a case recently, where I had to get the connection details from a database.

This is how I did it.

## Where I stole it from:

[Luke Evers](https://lukevers.com/2015/03/25/on-the-fly-database-connections-with-laravel-5)


## How I implemented it:

```
 private function connect($dataSource){

        $host = $dataSource->dataConnection->host;
        $database = $dataSource->dataConnection->database;
        $username = $dataSource->dataConnection->username;
        $password = $dataSource->dataConnection->password;


        //connect to db
        //https://lukevers.com/2015/03/25/on-the-fly-database-connections-with-laravel-5
        Config::set("database.connections.temp", [
            "host" => $host,
            "database" => $database,
            "username" => $username,
            "password" => $password,
            "driver" => 'mysql',
            'collation' => 'utf8_unicode_ci'
        ]);

        return  DB::connection('temp');

    }

```

This is how I use it:

```
  $connection  = $this->connect($dataSource);
  $records = DB::connection('temp')->select($dataSource->SQL);

  DB::purge('temp');
```


Mick
