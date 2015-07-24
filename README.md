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

Sample result:

```
[
    {
        "uid": {
            "user": "Gabriel Medina (Rha7) <rha7.com@gmail.com>",
            "time": "1437515835"
        },
        "pub": {
            "keyId": "35F6CE83886558ABF6CE59D7AD5F669D16A76D39",
            "bits": "4096",
            "time": "1437515835"
        }
    },
    {
        "uid": {
            "user": "Gabriel Medina (Rha7) <rha7.com@gmail.com>",
            "time": "1265153330"
        },
        "pub": {
            "keyId": "F73CE1DBE51F9369C7F59204992AFE46565BF06B",
            "bits": "2048",
            "time": "1265153330"
        }
    }
]
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

Sample result:

```
-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.1.5
Comment: Hostname: pgp.mit.edu

mQINBFWuwDsBEACrkjiFQwI7ccuWTRPkilVnaR/8K1MIdb/Lb85gUTc3DLG4IrbRuuefm2WO
KELQlj2qqzgJ8/EubY0ohP3OrIL2+VpmKV7jMK58+P+QeGSZRoVNNX4yIXgUU2ilMvfoHEi3
AivEfbIrEdt6ekiJ+BBBuyjS+tMHxHypcoE9+3SGhbfQ9mO4hwBK4qt5YZYxOB1TvMpqqtVD
/Hmn9Olb6kKRbxeIXdUb8UIvlSbz1EuhyDF0LM8hup5uw5tArmUemSN3EMq6Qnua3EClpkrA
Fcdbs8Ki8QX4ob/oQLfOCeiFttwHdMgbSlKkSTKnN6ciig9EsNjeYYiH1cfJISY2qik5c/y3
mDqO052Q7XFti2zlfQaIoQAriyk7aFAT2n0cCYsRFxnCSYIvZQzaTfRHS+oUUK2z8+HhW41B
qnL6jZP26UI5TkbGh4llu/BInEbzL/ta1Y686dFfTgduPpyqbGHc68T7Z/4kjyVC6TPknNIv
JWTBCPyqo54aYXRXVVuLHGbk6zheMcPjN7k6lAdkH6NtK53UjTOtTgIHm7NebIe8ILliLu7p
VPmgQstZvxXd3URYwzE9Q5XWFvFCfdTler5CsRLDIsBWFVFlt5FQkVcanQS/lE3EaBWhJxsa
a/hPJ3x4/rkSQ0bk4vicEICw7tavdXYMLUtzEtvI+pauYaz03wARAQABtCpHYWJyaWVsIE1l
ZGluYSAoUmhhNykgPHJoYTcuY29tQGdtYWlsLmNvbT6JAj0EEwEKACcFAlWuwDsCGwMFCQeG
H4AFCwkIBwMFFQoJCAsFFgIDAQACHgECF4AACgkQrV9mnRanbTkfCg/+Idz05caopzCKkZES
2Mtk2HzmR80ihr85F8ICZjYReOB6dD4YZoPplMFCDETjvA2zrTiWlrGkXXkMGIz6M32YsZU9
s8dfzLp9+OJErlPbckZ+KsBbak1W7M1InGNb/BaAcYUz31YBhi79JxhMEmCcthadnXCAg2EG
G+eLksLTu1Iv0cmho8pJWg44iUoJ7aMRhTaX4i31xesMF3F/NDbfMI3m+Z5NNGEag7DkSA2g
Kcet2mHs6/mQGxE20+vb7Z1jkE+i4xIc/Ic7Qc2LmvVVr6zesG/ZV1aqkyDJ8QWf14LznW40
bZpuG4M6G3fdqlRaEcHeaprNKZM/+eqnlPaQbSGb3zWPbLhCPKh5rIa5iaWzBuFOJPpjMg8M
jJ/FIIvTwKoHv7OhEdm69pmi7mX06dvwbkcrB+9QQJnrlpVeIDw3rq86mHkwnRwoKSbkqNDi
/pVZwnOivhTAv08lCCLj0QNPsFJUEaU/s407eKLY1fhpiUsi7MJfdB+PvH/54K7dCEnsV4wz
c3v6IJm0rwgjuLELHJ5I9Fizusyq3XAD3jPhg4lwXAoC9oB68/4y48YsR676kxbUc+gn3ume
BhuE/fEeWmuQ/LF/54Yieh9jfO7r8TrQFKjcbQaQm1fol+fsMX6mSlkAGiwMuxoUPA6KFSBR
xbzLUk0Qxd3cpOCrHAy5Ag0EVa7AOwEQANdYa9aCX5jII5qo3cufi/xucIPOjUAG/nRzmd5r
zmu7tKDJMMca6Ed1Z3gcNqninWypchYZ7m14lgim89M2qCdjO1GFIjNbPZlfcpAhG4FqMRap
5oEzFxKgGGzYdJA4VOynt/6sHHQUni2l/0BCBVXPniN1E5COl8h4jdZGA6iCk6lCZIjOG5fW
JNll+sHcCbYYKLG8Lux58CZySlgL5smWSTRBOy6jWZG6vpYCONl9fZEBDFUL3nFyP0+P23sn
Whk+wQSAIkAfsTi8L56UNfeUXk8uolh37FE4/mw7WsqWeYN5mZbauDnVQYxSU7N4PVbbMzJL
3j19ZlaQv6qznElGj/c9ugVb6m7JMeqwTLCUIw2OHyS/i6XednvNxKYtewSboC9nXFbKmAw2
kX7XpEljGfzMOnNNU53Ilg2jmxPBFhHXznIPXkEMMnQRmFKKa6sQVpjrTmGQ43nESWye8vGC
6Qnqo29ZA7ip8XgzCxUGIQltjAyxI1w7EHT9R24Z8Q4K62VQe1V+V93hJDZDmX+ZOrRhxRU4
mDDN9SqT9KmauBUTG/i9lPdQHhmhh6ZB0/2mcri0wCNSHmOLA5v3qQJiCoWTyt6wNNGfQjNd
7p1LboBSI1Na2vk4IYAqs6ejVqyoh5ee6dTcC8Nj0l/BvJ+CD1HwATo/1rhBLOOcMXYtABEB
AAGJAiUEGAEKAA8FAlWuwDsCGwwFCQeGH4AACgkQrV9mnRanbTl2rxAAhlSlzdEB1hy8hGwe
0Eq8GK4AVzEzUjWq03M08Me8qLaAInVg6En/jji94kKCyov1fSThLkDEIwb9tshJrDT6gCat
7Y/NNu0HK9i9hyFW0BA/ppX/9z8iic1AJh9Ha6SE7g6SLx60RMD2Lkb76ha42W5Q4Yfqsj65
Mt0XXHMCh/O0/A6rjgVKPoIkXnbN5asovQ1SfXW3vGjKGroNipv0/9SCvG8MeM+aqiHGiG1c
1kkZl4KbpfGcMTmQrJNUpex6Fq0dexK96Efo4QVIWj6vc7cdkI6PWmHGMSWZnG5US5wdnwGu
s7hgYeea8svZ4F0XxDYCceybUoho8YZr1CUidN+nTBVR3qzaHvCphG8aa0BULrgsTnAwcVp9
ZBTotm5gbDKNBmR5Hn7oCs6xhE1IX0scm6wDZ66WPvLOJ1I6Ai6z7FuV1uQu1FYGG5Q5VIxV
iVLE/XSbS0wLowryOTgc3cdqfIJPftdDfvf2awEBMtOPCydgLho4CcJd6MdlQ5fiPLd33su7
Q6TOWPmt7QPUOgIoNArfpNcKn9GYlZeUBzs7iFMSl7rgasD5bJd6JqMQwRB30cgPHgStjfuh
v0U8HALdbjJam4AU6LosnEoqbamv7gE1WBwNNpFKzgbK2sHX60CO1UqxE+8V4VSrdlnoDfeu
AA7FgjNpYA8kdEZfArc=
=EkjF
-----END PGP PUBLIC KEY BLOCK-----
```

## Finally

If you want to say hi, drop me a line [by mail (rha7.com@gmail.com)](mailto:rha7.com@gmail.com), [Twitter (@\_Rha7\_)](https://twitter.com/_Rha7_) or [LinkedIn (gmedinam)](https://mx.linkedin.com/in/gmedinam). 
