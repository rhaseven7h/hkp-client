# hkp-client

## Description

HKP PGP Key Server Client

This is a client to look up (search) and fetch PGP keys from a server.

Its is based/adapted from [Node HKP Client](https://github.com/freewil/node-hkp-client).

## Support

Please feel free to fork and send pull-requests if you want to add new features or send bug fixes.

Other links:

* [Wiki](https://github.com/Rhaseven7h/hkp-client/wiki)
* [Issue Tracking](https://github.com/Rhaseven7h/hkp-client/issues)
* [Git Repo](https://github.com/Rhaseven7h/hkp-client.git)

## Installation

You can simply git-clone it:

```
$ git clone https://github.com/Rhaseven7h/hkp-client.git
```

or use bower install:

```
$ bower install hkp-client
```

and link it from your html file

```
<script src="bower_components/hkp-client/src/hkp-client.js"></script>
```

## HKP Server Selection

This is optional, by default it will use `http://pgp.mit.edu:11371`, but you can use other servers.

```
hkpClient.server = "http://pgp.mit.edu:11371";
```

## How to look up (search) for a key

Find public key entries in server by user id.

```
hkpClient.search("rha7.com@gmail.com")
.done(function(records, data, textStatus, jqXHR) {
  console.log("Search::Yeah!", records);
})
.fail(function(jqXHR, textStatus, errorThrown) {
  console.log("Search::Bummer!", textStatus, errorThrown);
})
;
```

## How to fetch a key definition

Fetch a specific public by key id.

```
hkpClient.fetch("35F6CE83886558ABF6CE59D7AD5F669D16A76D39")
.done(function(key, data, textStatus, jqXHR){
  console.log("Fetch::Yeah!", key);
})
.fail(function(jqXHR, textStatus, errorThrown){
  console.log("Fetch::Bummer!", textStatus, errorThrown);
})
;
```

## Finally

If you want to say hi, drop me a line [by mail (rha7.com@gmail.com)](mailto:rha7.com@gmail.com), [Twitter (@_Rha7_)](https://twitter.com/_Rha7_) or [LinkedIn (gmedinam)](https://mx.linkedin.com/in/gmedinam). 
