---
layout: post
title: "hola mundo"
date:   2022-03-07 04:39:26 -0600
categories: jekyll update
---


## Primer paso sera ejecutar el script de instalacion del docker en el cual lo primero que hacemos un set -x hace que el shell para salir si cualquier subcomando o canalización devuelve un estado distinto de cero.

set -x

## Por Racones ya sean esteticas o por facilitar el proceso a la cpu ponemos aprate las variables 
USERNAME=ubuntu

![img]({{ site.url }}/Screenshot_20220308_125101.png)

# Actualizamos el sistema
apt update

# Descargamos el script
curl -fsSL https://get.docker.com -o get-docker.sh

# Ejecutamos el script
sudo sh get-docker.sh

# Añadimos nuestro usuario al grupo docker
usermod -aG docker $USERNAME

# Actualizamos el grupo docker se hace aparte
#newgrp docker

# Iniciamos el servicio docker
systemctl start docker

# Configuramos para que el servicio se inicie automaticamente
systemctl enable docker
