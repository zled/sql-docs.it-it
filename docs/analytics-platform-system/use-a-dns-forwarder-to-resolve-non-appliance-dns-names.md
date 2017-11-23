---
title: Utilizzare un server d'inoltro DNS per risolvere i nomi DNS Non strumento (AP)
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: sql-non-specified
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: analytics-platform-system
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 123d8a83-b7fd-4dc9-90d4-fa01af2d629d
caps.latest.revision: "21"
ms.openlocfilehash: 6e91828bcc64a47d942959a2522af0e53041e027
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="use-a-dns-forwarder-to-resolve-non-appliance-dns-names"></a>Utilizzare un server d'inoltro DNS per risolvere i nomi DNS Non strumento
Un server d'inoltro DNS può essere configurato sui nodi di servizi di dominio Active Directory (***appliance_domain*-AD01** e  ***appliance_domain*-AD02**) del dispositivo di sistema della piattaforma Analitica per consentire gli script e applicazioni software per accedere a server esterni.  
  
## <a name="ResolveDNS"></a>Utilizzo di un server d'inoltro DNS  
Il dispositivo di sistema della piattaforma Analitica è configurato per impedire la risoluzione dei nomi DNS del server che non sono presenti nel dispositivo. Alcuni processi, ad esempio Windows Software Update Services (WSUS), saranno necessario accedere ai server di fuori del dispositivo. Per supportare questo scenario di utilizzo Analitica piattaforma del sistema DNS può essere configurato per supportare un server d'inoltro nome esterno che consentirà di host di sistema della piattaforma Analitica e macchine virtuali (VM) da usare server DNS esterni per la risoluzione dei nomi di fuori del dispositivo. Configurazione personalizzata di suffissi DNS non è supportata, ovvero che è necessario utilizzare nomi di dominio completo per risolvere un nome server non strumento.  
  
**Per creare un server d'inoltro DNS con la GUI di DNS**  
  
1.  Eseguire l'accesso di  ***appliance_domain*-AD01** nodo.  
  
2.  Aprire Gestore DNS (**dnsmgmt.msc**).  
  
3.  Fare doppio clic il nome del server e quindi fare clic su **proprietà**.  
  
4.  Scegliere il **avanzate** scheda, deselezionare il **disabilitare la ricorsione (anche server d'inoltro disabilita)** opzione e quindi fare clic su **applica**.)  
  
5.  Fare clic su di **server d'inoltro** scheda e quindi fare clic su **modifica**.  
  
6.  Immettere l'indirizzo IP per il server DNS esterno che forniranno la risoluzione dei nomi. Le macchine virtuali e i server (host) del dispositivo si connetteranno a server esterni con i nomi di dominio completo.  
  
7.  Ripetere i passaggi da 1 a 6 nel  ***appliance_domain*-AD02** nodo  
  
**Per creare un server d'inoltro DNS mediante Windows PowerShell**  
  
1.  Eseguire l'accesso di  ***appliance_domain*-AD01**nodo.  
  
2.  Eseguire lo script di Windows PowerShell seguente dal  ***appliance_domain*-AD01** nodo. Prima di eseguire lo script di Windows PowerShell, sostituire gli indirizzi IP con gli indirizzi IP dei server DNS non strumento.  
  
    ```  
    $DNS=Get-WmiObject -class "MicrosoftDNS_Server"  -Namespace "root\microsoftdns"  
    $DNS.Forwarders = ("xxx.xxx.xxx.xxx", "xxx.xxx.xxx.xxx")  
    $DNS.put()  
    ```  
  
3.  Eseguire lo stesso comando sul  ***appliance_domain*-AD02** nodo.  
  
## <a name="configuring-dns-resolution-for-wsus"></a>Configurazione di risoluzione DNS per Windows Server Update Services  
SQL Server PDW 2012 fornisce integrata per la manutenzione e l'applicazione di patch funzionalità. SQL Server PDW utilizza Microsoft Update e altre tecnologie di manutenzione di Microsoft. Per abilitare gli aggiornamenti, il dispositivo deve essere in grado di connettersi a un repository WSUS azienda o nel repository di WSUS pubblica di Microsoft.  
  
Per i clienti che sceglie di configurare il dispositivo per cercare gli aggiornamenti per il repository WSUS pubblico di Microsoft, le istruzioni seguenti impostare i dettagli di configurazione appropriata nel dispositivo.  
  
> [!NOTE]  
> L'amministratore di rete del cliente deve fornire l'indirizzo IP per un server DNS aziendale in grado di risolvere nomi **Microsoft.com**.  
  
1.  Utilizzo di desktop remoto, accedere a una VM di VMM (<fabric domain>- VMM) usando l'account di amministratore di dominio dell'infrastruttura.  
  
2.  Aprire il pannello di controllo, fare clic su **rete e Internet**, quindi fare clic su **centro rete e condivisione**.  
  
3.  Nell'elenco delle connessioni, fare clic su **VMSEthernet**, quindi fare clic su **proprietà**.  
  
4.  Selezionare **Internet Protocol versione 4 (TCP/IPv4)**, quindi fare clic su **proprietà**.  
  
5.  Nel **server DNS alternativo** , aggiungere l'indirizzo IP fornito dall'amministratore di rete del cliente.  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
