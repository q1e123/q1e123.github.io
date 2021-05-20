---
layout: post
title:  Automatic PCB routing using OrCad
categories: [lesson]
tag: [electronics, orcad]
where: Electronics
permalink: /:categories/:title
desc:
---

# Automatic PCB routing using OrCad
This was tried using **17.4** version.

## Setup
In this phase you are going to setup line width of the routhing. 


### Open *Allegro Constraint Manager*
**Setup** - **Constraints...**

### Edit line width

In the **Worksheet Selector**:  
**Physical** - **Physical Constraint Set**

In the right you will see a table. To modify line width modify the **Min** and **Max** value under Line Width.

![Worksheet Selector]({{site.baseurl}}/assets/img/lessons/Electronics/Automatic-pcb-routing-orcad/worksheet-selector.png "Worksheet Selector")

## Automatic route
In this phase you are going to setup the parameters of automatic route and start the routing process.

### Open *Automatic router*

**Route** - **PCB Router** - **Automatic Route**

### Modify parameters of automatic router

![Automatic router]({{site.baseurl}}/assets/img/lessons/Electronics/Automatic-pcb-routing-orcad/automatic-router.png "Automatic router")

Depending on your needs, you will need to modify these parameters accordingly.

After press **Route** button. If you messed the parameters and you are not satisfied with the routing you can undo it by pressing the **Undo** button.

#### Reccomended setup
**Router Setup**
* **Strategy**
    * Use smart router
* **Options**
    * Enable diagonal routing

* **Routing Subclass**
    * Select only one

![Router Setup]({{site.baseurl}}/assets/img/lessons/Electronics/Automatic-pcb-routing-orcad/router-setup.png "Router Setup")


**Smart Router**
* **Fanout**  
    * Fanout if appropriate  
        * Via sharing
        * Pin sharing

![Smart Router]({{site.baseurl}}/assets/img/lessons/Electronics/Automatic-pcb-routing-orcad/smart-router.png "Smart Router")


