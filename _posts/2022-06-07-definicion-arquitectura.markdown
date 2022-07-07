---
layout: post
title: "Definición de arquitectura"
date: 2022-06-07 18:00:01 -0000
categories: arquitectura
---

# Arquitectura

![](/images/arquitectura.jpg)


## Front-end

Como primera capa de nuestra arquitectura, la que se comunicará con los usuarios, tanto los que utilizarán la aplicación
mobile (_Listeners & Artists_) como los usuarios de la página web (_Admins_).

Siendo este el contacto con los usuarios que no son desarrolladores, nos ocupamos de que la experiencia de usuario
sea la más amena e intuitiva que se podía lograr, haciendo que tanto el diseño como la distribución de las aplicaciones
sean integramente dedicadas a que el usuario se sienta cómodo.

Por ello se eligió React como la base para el desarrollo de ambas, React vanilla para la página web y React Native
para la aplicación en Android. Esta decisión fue tomada justamente porque entendemos que para cumplir con los criterios
mencionados en el párrafo anterior, React es el framework lider del mercado para cumplir con los más exigentes de los 
usuarios, de una manera sencilla y elegante de resolver los problemas que conllevan las interfaces de usuario.


## Back-end

Del lado oscuro de la aplicación, en el que solo nosotros desarrolladores tendremos contacto, nos encargamos de dividir
el trabajo en diferentes servicios, sabiendo que una aplicación de esta magnitud en una aplicación de monolito no
puede escalar de manera eficiente. 

Aún asi quisimos que para el desarrollo web y mobile esté el back-end centralizado, sobre todo por seguridad, pero también
por comodidad, por ello hicimos un servicio que funciona de middleware para el resto de microservicios.

### Middleware

Se encarga de toda la distribución de acciones a los diferentes microservicios, además de verificar los tokens por cuestiones
de seguridad.

### Streamable contents

Se encarga de manejar toda la información y acciones que poseen tanto las canciones, como los albums y las playlists.

### Users

Se encarga de manejar toda la información y acciones que poseen los usuarios: _Listeners_, _Artists_ y _Admins_


### Payments

Se encarga de manejar las acciones sensibles que tienen que ver con dinero de los usuarios. Algunas de estas son:

- Cambiar de subscripción a Premium
- Donar a un artista

### Metrics

Se encarga de almacenar todas las métricas de las aplicaciones para poder darlas de una manera entendible a los 
administradores en la página web. Almacena información de cosas como cuantos usuario se registaron con usuario y 
contraseña, o cuantos usuarios con federada. También cuantas canciones se subieron en los últimos dias. Y algunas cosas más.

## Kubernetes

Kubernetes es la plataforma que elegimos para hostear nuestros microservicios, siendo el software lider en el mercado
cuando se trata de manejar grandes aplicaciones separada en microservicios.
