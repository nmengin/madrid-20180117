# WHY TRAEFIK IS AWESOME <!-- .element: style="margin-left:-5px"-->

![Traefik](./slides/images/traefik.logo.horizontal.bright.svg) <!-- .element: style="border:none;" -->

Meetup DevOps - Madrid - 2018/01/17

<small>[Nicolas Mengin](http://twitter.com/nicomengin) - [Containous](http://twitter.com/containous)</small>

Note:

por venir tantos

---

## docker inspect me <!-- .element: style="margin-bottom:100px"-->

* Developer for 12 years <!-- .element: class="fragment" data-fragment-index="1" -->
* Part time DevOps <!-- .element: class="fragment" data-fragment-index="1" -->
* ❤ Java, Shell, Docker World, GO ❤ <!-- .element: class="fragment" data-fragment-index="1" -->
* Work @ Containous <!-- .element: class="fragment" data-fragment-index="2" -->
* Maintainer of <!-- .element: class="fragment" data-fragment-index="2" --> [Træfik](https://traefik.io) <!-- .element: class="fragment" data-fragment-index="2" -->
* French <!-- .element: class="fragment" data-fragment-index="3" -->
* ❤ Spain ❤ <!-- .element: class="fragment" data-fragment-index="4" -->

Note:

* desarrollador
* lengua materna

---

## Træfik explained to my mother

<div class="fragment">
```
Mum : "What are you doing in your new company?"
Me : "I am computing a Reverse Proxy."
Mum : "..."
Me : "Your Internet Box is like a proxy!"
```
</div>
<div class="fragment">
```
Me : "Træfik allows doing the reverse."
```
</div>
<div class="fragment">
```
Mum : "OK! It's like Nginx?!"
```
</div>
<div class="fragment">
```
Me : "Not exactly! Nginx is a web server.
      But, it can be used as Reverse Proxy too..."
```
</div>
<div class="fragment" >
```
Mum : "Understood! It's like HA Proxy!"
```
</div>
<div style="display: none;">
```
```
</div>
![But](./slides/images/greatBut.gif) <!-- .element: class="fragment" style="border:none"-->

Note:

* No sabia come empezar a hablar de Traefik y como presentarlo rapidamente
* Pensado a una dicusion que tuve con mi madre y os la voy a presentar
* No debería haber dicho eso
* Mi madre es muy sorprendente
* Despues, no sabia que contestarla... Pero tiene razon y es cierto que la primera pregunta

---

## Why another Reverse Proxy?

![Why](./slides/images/why.gif) <!-- .element: style="height:500px;width:600px;"-->

Note:

* Para entender bien, propuesto de hacer un poco de historia

-

## A long time ago in a galaxy far, far away.... <!-- .element: style="margin-left:-50px"-->

1. Deploy a service to expose <!-- .element: style="margin-top: 100px; margin-left:-400px" class="fragment" data-fragment-index="1" -->
1. Configure the Reverse Proxy <!-- .element: style="margin-left:-400px" class="fragment" data-fragment-index="2" -->
1. Reload/Restart it. <!-- .element: style="margin-left:-400px" class="fragment" data-fragment-index="3" -->

<p style="margin-top:200px;font-size: 200%;color:white" class="fragment">**In a static way!!**</p>

![Old archi](./slides/images/old-archi.png) <!-- .element: style="float: right; width: 60%; margin-right:-200px; margin-top:-500px"-->

Note:

* Aqui es una infraestructura como **fue hecho** antes : DB + servicios web + RP
* Para anadir un nuevo servicios, tuvimos que **despegar** lo
* Configurar el RP

-

## Static infrastructure is (almost) dead!

![New archi](./slides/images/newarchi-RP.png) <!-- .element: style="background-color:white; height:480px; margin-top:-20px; margin-bottom: -35px" class="fragment fade-out" data-fragment-index="1" -->
![New archi02](./slides/images/newarchi-RP-config.png) <!-- .element: style="background-color:white; height:480px; margin-top:-500px;" class="fragment" data-fragment-index="1" -->

<p style="margin-top:-40px;font-size: 125%;color:white" class="fragment">**How to configure dynamic infrastructures?**</p>

Note:

* Ahora, es el tiempo de los µ-servicios!
* Declaramos servicios para las API, los backoffices
* Podemos crear differentes replicas de uno servicios
* Todo **administrado** en containers Docker con un orchestrator como Kubernetes.

**TODO ES DYNAMICO**

* Pero, con los RP tradicionales, la configuracion sigue de ser statica en ficheros!
* La pregunta es : **Como configurar de manera dynamica?** Y la respuesta es ...

---

## One Reverse Proxy to rule them all

![Traefik](./slides/images/traefik.logo.bright.svg)

-

### Dynamic configuration for dynamic infrastruture

![New archi](./slides/images/newarchi-Traefik.png) <!-- .element: style="background-color:white;"-->

Note:

* Traefik va a escutar las API de los orchestratores para **anadir o suprimir las configuraciones de manera automática**

-

## Træfik in details

* Reverse Proxy Dynamic <!-- .element: style=" margin-left:-300px"-->
* Written in GO (Single binary) <!-- .element: style="margin-left:-300px"-->
* Open Source <!-- .element: style="margin-left:-300px"-->
* Docker official image <!-- .element: style="margin-left:-300px"-->
* Multi-Backends <!-- .element: style="margin-left:-300px"-->
* Hot reloading <!-- .element: style="margin-left:-300px"-->
* Load-balancing: WRR, DRR <!-- .element: style="margin-left:-300px"-->
* Circuit breakers <!-- .element: style="margin-left:-300px"-->
* Websockets <!-- .element: style="margin-left:-300px"-->
* HTTP2 <!-- .element: style="margin-left:-300px"-->
* Prometheus, DataDog, StatD <!-- .element: style="margin-left:-300px"-->
* ... <!-- .element: style="margin-left:-300px"-->

![Features](./slides/images/wordcloud.png) <!-- .element: style="border:none; float: right; width: 50%; margin-top: -550px; margin-right:-150px"-->

Note:

* Reverse Proxy Dynamic  Written in GO (Single binary)  Open Source  Docker official image
* Multi-Backends : Docker, SwarmMode, Kub, Meso/Marathon, Consul/ETCD2-3/ZK, DynamoDB, Eureka, RANCHER, Service Fabric (1.5)
* Hot reloading
* Load-balancing: WRR, DRR
* Circuit breakers
* Websockets
* HTTP2
* Monitoring : Prometheus, DataDog, StatD
* 1.1 : CLUSTER MODE BASIC AUTH GLOBAL / FRONTEND (1.3)  SESSION AFFINITY
* 1.2 :  HEALTHCHECKS TRAEFIK BUG
* 1.4 : GRPC - AUTH FORWARD SSL REDIRECT, CUSTOM ERROR PAGES CUSTOM HEADERS, PROXY PROTOCOL MULTI ARCH, HSTS...
* 1.5 : Rate limiting Dynamic TLS Custom Header Docker et Kube

---

<!-- .slide: data-background="./slides/images/pray-cat.jpeg" -->

# DEMO  <!-- .element: style="float: right; width: 50%; margin-right:-200px; color: white"-->

---

## Let's talk about Security...

* Auto-generated unsigned certificate <!-- .element: style="margin-top: 40px; margin-left: -150px" class="fragment" data-fragment-index="1" -->
* Statically provided certificates <!-- .element: style="margin-left: -150px" class="fragment" data-fragment-index="2" -->
* Dynamically provided certificates <!-- .element: style="margin-left: -150px"  class="fragment" data-fragment-index="3" -->
  * File and KV store <!-- .element:  class="fragment" data-fragment-index="3" -->
* Let's Encrypt certificates <!-- .element: style="margin-left: -150px"  class="fragment" data-fragment-index="4" -->
  * SSL and DNS Challenges <!-- .element: class="fragment" data-fragment-index="4" -->
  * Dynamic <!-- .element: class="fragment" data-fragment-index="4" -->
  * Renewed automatically <!-- .element: class="fragment" data-fragment-index="4" -->
  * Stored in file or KV store <!-- .element: class="fragment" data-fragment-index="4" -->

<div style="float: right; width: 40%; margin-top: -450px; margin-right: -200px" data-fragment-index="1" class="fragment">
<div data-fragment-index="2" class="fragment fade-out" >
```toml
[entryPoints]
  [entryPoints.https]
  address = ":443"
    [entryPoints.https.tls]
```
</div>
</div>
<div style="float: right; width: 62%; margin-top: -400px; margin-right: -300px" data-fragment-index="2" class="fragment">
<div data-fragment-index="3" class="fragment fade-out" >
```toml
[entryPoints]
  [entryPoints.https]
  address = ":443"
    [entryPoints.https.tls]
      [[entryPoints.https.tls.certificates]]
       CertFile = "/snitest.com.cert"
       KeyFile = "/snitest.com.key"
```
</div>
</div>
<div style="float: right;  width: 50%; margin-top: -350px; margin-right: -200px" data-fragment-index="3" class="fragment">
<div data-fragment-index="4" class="fragment fade-out" >
```toml
[entryPoints]
  [entryPoints.https]
  address = ":443"
    [entryPoints.https.tls]

[file]

[[tlsConfiguration]]
entryPoints = ["https"]
  [tlsConfiguration.certificate]
     CertFile = "/snitest.com.cert"
     KeyFile = "/snitest.com.key"
```
</div>
</div>
<div style="float: right; width: 40%; margin-top: -250px; margin-right: -200px" data-fragment-index="4" class="fragment">
```toml
[entryPoints]
  [entryPoints.https]
  address = ":443"
    [entryPoints.https.tls]

[acme]
email = "test@traefik.io"
storage = "/acme.json"
entryPoint = "https"
OnHostRule = true
```
</div>
![LE](./slides/images/letsencrypt-logo.svg) <!-- .element: style="display:none" class="fragment" data-fragment-index="4" -->

Note:

* Ahora os propueto de ver unas	**funcionalidades** necesarias en produccion
* En primero, los certificados SSL
* En traefik, hay 4 manera de utilisarlos

* Cuando un TLS entryPoint esta creado, desde la ultima version, Traefik va a crear un certificada self-signed. Se puede utilizar por un servidor privado o durante los tests de integracion de Traefik en una infraestructura.
* Certificados se pueden anadir de manera statica, directamente en un EntryPoints. Pero, de esta manera, no es posible de modificar o suprimir un certificado o anadir un nuevo certificado en un Entrypoint sin **reinicializar** a Traefik.
* Desde la ultima version, certificados se pueden anadir de manera dynamica. De esta manera, es posible de modificar o suprimir un certificado o anadir un nuevo certificado en un Entrypoint sin **reinicializar** a Traefik. Pero hoy, es solo conlos providers files y KV stores. **Kubernetes eb la proxima version**
* La ultima manera es de utilizar Let's Encypt en Traefik. Con un poco de configuracion, Traefik va a :
  * Crear un SSl o DNS Challenge
  * Y despues va crear y **prorrogar** los certificados de manera automatica y dynamica
  * Los certificados se pueden **preservar** en un fichero o un KV store

-

## .. And High Availability

* Based on<!-- .element: style="margin-top: 40px; margin-left: -150px" class="fragment" data-fragment-index="1" --> [Raft Consensus Algortihm](https://raft.github.io/) <!-- .element: style="margin-top: 40px" class="fragment" data-fragment-index="1" -->
  * One leader and  <!-- .element: class="fragment" data-fragment-index="2" --> _n_  <!-- .element: class="fragment" data-fragment-index="2" --> workers <!-- .element: class="fragment" data-fragment-index="2" -->
  * Automatic leader Election <!-- .element: class="fragment" data-fragment-index="2" -->
* Use external KV store : <!-- .element: style="margin-top: 20px; margin-left: -150px" class="fragment" data-fragment-index="3" -->
  * Store and share configuration <!-- .element: class="fragment" data-fragment-index="3" -->
  * Store and share ACME certificates <!-- .element: class="fragment" data-fragment-index="3" -->

![Cluster](./slides/images/cluster.svg) <!-- .element: style="background-color:white; height:600px; border: none; float: right; margin-top: -375px; margin-right:-225px;" class="fragment" data-fragment-index="4" -->

Note:

* La otra **funcionalidad** es la HA
* Traefik se puede utilizar en cluster que se baza en el raft.
* Cuando el leader se va, una nueva eleccion permitte de **sustituirlo con** une worker de manera automatica
* **preservar y conpartir**
* El grafico enena como functiona un cluster de Traefik con ACME. El leader va a hacer los challenges y escribir los nuevos certificados en el KV store. Los otros van a anadir los certificados desde el KV store.
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

<p style="font-size: 200%;" class="fragment" data-fragment-index="1">**Containous**</p>
<p class="fragment" data-fragment-index="1">Raised 1M€</p>
<p style="margin-top:-20px;" class="fragment" data-fragment-index="1">1 year old</p>

Note:

### TRAEFIK

* **descargas**
* **contribuyentes**

### Containous

* la empreza detras de Traefik
* **una recaudación de fondos**
-
# COME TO THE TRÆFIK SIDE <!-- .element: style="margin-top: 0px; margin-bottom: 50px"-->

<p style="font-size: 140%;">`docker run -it containous/jobs`</p>

# WE HAVE CHEESE <!-- .element: style="margin-top: 50px"-->
![Features](./slides/images/traefik-morbier.png) <!-- .element: style="border:none;  float: left; width: 12%; margin-top: -100px;"-->
![Features](./slides/images/traefik-raclette.svg) <!-- .element: style="border:none; float: right; width: 20%;  margin-top: -100px; margin-right:-150px"-->
![Features](./slides/images/traefik-roquefort.svg) <!-- .element: style="border:none; width: 25%;"-->

-

# ... AND STICKERS

![Traefik](./slides/images/traefik.logo.bright.svg) <!-- .element: style="border:none" -->


---

# THANK YOU <!-- .element: style="margin-bottom: 100px;"-->

[traefik.io](http://traefik.io)
</BR>
[@traefikproxy](http://twitter.com/traefikproxy)
</BR>
[@nicomengin](http://twitter.com/nicomengin)
</BR>
[nmengin.github.io/madrid-20180117](https://nmengin.github.io/madrid-20180117)
