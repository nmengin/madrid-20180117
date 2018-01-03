# WHY TRAEFIK IS AWESOME <!-- .element: style="margin-left:-5px"-->

![Traefik](./slides/images/traefik-logo-horizontal.svg) <!-- .element: style="border:none;" -->

Meetup DevOps - Madrid - 2018/01/17

<small>[Nicolas Mengin](http://twitter.com/nicomengin) - [Containous](http://twitter.com/containous)</small>

---

## A frenchman in Madrid <!-- .element: style="margin-bottom:100px"-->

* French <!-- .element: class="fragment" data-fragment-index="1" -->
* ❤ Spain ❤ <!-- .element: class="fragment" data-fragment-index="2" -->
* Developer for 12 years <!-- .element: class="fragment" data-fragment-index="3" -->
* Part time DevOps <!-- .element: class="fragment" data-fragment-index="3" -->
* ❤ Java, Go, Shell, Docker World ❤ <!-- .element: class="fragment" data-fragment-index="3" -->
* Work @ Containous <!-- .element: class="fragment" data-fragment-index="4" -->
* Maintainer of <!-- .element: class="fragment" data-fragment-index="4" --> [Træfik](https://traefik.io) <!-- .element: class="fragment" data-fragment-index="4" -->

---

## Træfik explained to my mother

```
Mum : "What are you doing in your new company?"
Me : "I am computing a Reverse Proxy."
Mum : "..."
Me : "Your Internet Box is like a proxy!"
```

![Internet Box](./slides/images/box-wifi.png) <!-- .element: style="height:300px;width:600px;" class="fragment" data-fragment-index="1" -->

<div class="fragment">
```
Me : "Træfik allows doing the reverse."
```
</div>
<div class="fragment">
```
Mum : "OK! It's like Nginx and HA Proxy?!"
```
</div>
```
```

Note:

Autres RP font d'autres choses que RP

Serveur web, authentification

Traefik ne fait que RP, on delègue le reste

---

## Why another Reverse Proxy?

![Why](./slides/images/why.gif) <!-- .element: style="height:500px;width:600px;"-->

-

## A long time ago in a galaxy far, far away.... <!-- .element: style="margin-left:-50px"-->

1. Deploy a service to expose <!-- .element: style="margin-top: 100px; margin-left:-400px" class="fragment" data-fragment-index="1" -->
1. Configure the Reverse Proxy <!-- .element: style="margin-left:-400px" class="fragment" data-fragment-index="2" -->
1. Reload/Restart it. <!-- .element: style="margin-left:-400px" class="fragment" data-fragment-index="3" -->

<p style="margin-top:200px;font-size: 200%;color:white" class="fragment">**In a static way!!**</p>

![Old archi](./slides/images/old-archi.png) <!-- .element: style="float: right; width: 60%; margin-right:-200px; margin-top:-500px"-->

-

## Static infrastructure is (almost) dead!

![New archi](./slides/images/newarchi-RP.png) <!-- .element: style="background-color:white; height:480px; margin-top:-20px; margin-bottom: -35px" class="fragment fade-out" data-fragment-index="1" -->
![New archi02](./slides/images/newarchi-RP-config.png) <!-- .element: style="background-color:white; height:480px; margin-top:-500px;" class="fragment" data-fragment-index="1" -->

<p style="margin-top:-50px;font-size: 150%;color:white" class="fragment">**How to configure statically dynamic infrastructures?**</p>

---

## One Reverse Proxy to rule them all

![Traefik](./slides/images/traefik-logo.svg)

-

### Dynamic configuration for dynamic infrastruture

![New archi](./slides/images/newarchi-Traefik.png) <!-- .element: style="background-color:white;"-->

-

## Træfik in details

* Reverse Proxy Dynamic <!-- .element: style="margin-top: 40px; margin-left:-300px"-->
* Written in GO (Single binary) <!-- .element: style="margin-left:-300px"-->
* Open Source <!-- .element: style="margin-left:-300px"-->
* Docker official image <!-- .element: style="margin-left:-300px"-->
* Multi-Backends <!-- .element: style="margin-left:-300px"-->
* Hot reloading <!-- .element: style="margin-left:-300px"-->
* Load-balancing: WRR, DRR <!-- .element: style="margin-left:-300px"-->
* Circuit breakers <!-- .element: style="margin-left:-300px"-->
* Websockets <!-- .element: style="margin-left:-300px"-->
* HTTP2 <!-- .element: style="margin-left:-300px"-->
* ... <!-- .element: style="margin-left:-300px"-->

![Features](./slides/images/wordcloud02.png) <!-- .element: style="border:none; float: right; width: 50%; margin-top: -500px; margin-right:-150px"-->

---

<!-- .slide: data-background="./slides/images/pray-cat.jpeg" -->

# DEMO  <!-- .element: style="float: right; width: 50%; margin-right:-200px; color: white"-->

---

## Let's talk about SSL...

* Auto-generated unsigned certificate <!-- .element: style="margin-top: 40px" class="fragment" data-fragment-index="1" -->
* Statically provided certificates <!-- .element: class="fragment" data-fragment-index="2" -->
* Dynamically provided certificates <!-- .element: class="fragment" data-fragment-index="3" -->
  * File and KV store <!-- .element: class="fragment" data-fragment-index="3" -->
* Let's Encrypt certificates <!-- .element: class="fragment" data-fragment-index="4" -->
  * SSL and DNS Challenges <!-- .element: class="fragment" data-fragment-index="4" -->
  * Dynamic <!-- .element: class="fragment" data-fragment-index="4" -->
  * Renewed automatically <!-- .element: class="fragment" data-fragment-index="4" -->
  * Stored in file or KV store <!-- .element: class="fragment" data-fragment-index="4" -->

![LE](./slides/images/letsencrypt-logo.svg) <!-- .element: style="background-color:white; border: none;float: right; margin-right:-150px" class="fragment" data-fragment-index="4" -->

Note:

4 moyens

-

## .. And High Avaibility

* Based on ETCD raft <!-- .element: style="margin-top: 40px" class="fragment" data-fragment-index="1" -->
  * One leader and  <!-- .element: class="fragment" data-fragment-index="2" --> _n_  <!-- .element: class="fragment" data-fragment-index="2" --> workers <!-- .element: class="fragment" data-fragment-index="2" -->
  * Automatic leader Election <!-- .element: class="fragment" data-fragment-index="2" -->
* Use external KV store : <!-- .element: style="margin-top: 20px" class="fragment" data-fragment-index="3" -->
  * Store and share configuration <!-- .element: class="fragment" data-fragment-index="3" -->
  * Store and share ACME certificates <!-- .element: class="fragment" data-fragment-index="3" -->
---

<!-- .slide: data-background="./slides/images/pray02.jpg" data-background-size="1500px" -->

# DEMO  <!-- .element: style="margin-top:200px; color: white"-->

---

## Some key figures

<p style="font-size: 200%;">**Træfik**</p>
Version 1.5</BR>
+12000 &#9734;</BR>
+30M Downloads</BR>
+1200 LGTM</BR>
+220 Contributors

<p style="margin-top:40px; font-size: 200%;" class="fragment" data-fragment-index="1">**Containous**</p>
<p class="fragment" data-fragment-index="1">Raised 1M€</p>
<p style="margin-top:-20px;" class="fragment" data-fragment-index="1">1 year old</p>

-

# COME TO THE TRÆFIK SIDE <!-- .element: style="margin-bottom: 100px"-->

<p style="font-size: 140%;">`docker run -it containous/jobs`</p>

# WE HAVE CHEESE <!-- .element: style="margin-top: 100px"-->
-

# I HAVE STICKERS

![Traefik](./slides/images/traefik-logo.png) <!-- .element: style="border:none" -->


---

# THANK YOU <!-- .element: style="margin-bottom: 100px;"-->

[traefik.io](http://traefik.io)
</BR>
[@traefikproxy](http://twitter.com/traefikproxy)
</BR>
[@nicomengin](http://twitter.com/nicomengin)
</BR>
[nmengin.io.github/madrid-20180117](https://nmengin.io.github/madrid-20180117)
