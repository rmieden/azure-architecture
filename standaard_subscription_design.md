--
layout: default
title: Standaard Landing Zone subscription design
--
**Functionele beschrijving**
Dit ontwerp beschrijft een landing zone subscriptie met al de standaard geleverde resources die standaard aanwezig zijn in de subscriptie op het moment dat deze uitgerold wordt. 
Een landing zone bestaat uit en productie subscriptie en optioneel een non-productie subscriptie welke onder een bepaalde Management Group geplaatst worden. Welke Management Group dat is, wordt bepaald door de workload en de informatie die in de subscriptie opgeslagen wordt. Deze subscripties zijn binnen de Hub-Spoke netwerk topologie een Spoke. 
Een subscriptie wordt bij oplevering voorzien van de volgende functionaliteiten:
* Een netwerk dat voorzien is van een 4-tal subnets die het zoneringsconcept ondersteunen en elk voorzien zijn van een Network Security Group (NSG) ter bescherming van de resources die voorzien zijn van een Network Interface in dat subnet. Dit netwerk is standaard gekoppeld aan de Hub, wat communicatie met andere Spokes mogelijk maakt. 
* Een NetworkWatcher die de flow logs van de NSGs op slaat.
* Een Key Vault waar secrets en certificaten opgeslagen kunnen worden. Deze Key Vault worden tevens uitgerust met een standaard rotatiemechanisme van de secrets. De frequentie van dit mechanisme is 90 dagen.
* Een Service Recovery Vault waarin Backups geplaatst kunnen worden.
* Optioneel een Log Analytics Workspace (LAW) voor de opslag van performance metrics van applicaties.

Management van Virtual Machines (VM) wordt standaard gedaan vanuit een management server in de Platform subscriptie. Deze management server is alleen toegankelijk via een Azure Bastion dienst. Deze toegang wordt gelogd, is alleen mogelijk op basis van RBAC en is voorzien van MFA. Vanaf de management server is het mogelijk op de workload VMs in te loggen. Deze toegang wordt met behulp van NSGs mogelijk gemaakt. Indien gewenst is het ook mogelijk een management server in het management subnet van de landing zone uit te rollen en via Azure Bastion op die management server in te loggen. Dit is een verplichte toepassing voor die landing zones die voor leveranciers bedoeld zijn. 

