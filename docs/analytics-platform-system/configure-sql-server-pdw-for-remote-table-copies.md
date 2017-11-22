---
title: Configurare SQL Server PDW per le copie della tabella remota (SQL Server PDW)
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: sql-non-specified
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: analytics-platform-system
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/13/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 496b4214-5891-404c-8237-c2a1e09db6d5
caps.latest.revision: "11"
ms.openlocfilehash: 5daa546ed4cf0eeed1c51713fd9e55aa88515380
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="configure-sql-server-pdw-for-remote-table-copies"></a>Configurare SQL Server PDW per copie tabella remota
Viene descritto come configurare SQL Server PDW per utilizzare la funzionalità di copia della tabella remota per copiare le tabelle per database SMP SQL Server nel server non strumento.  
  
In questo argomento viene descritto uno dei passaggi di configurazione per la configurazione di copia della tabella remota. Per un elenco di tutti i passaggi di configurazione, vedere [copia della tabella remota](remote-table-copy.md).  
  
## <a name="before-you-begin"></a>Prima di iniziare  
Per configurare SQL Server PDW per l'utilizzo di copia della tabella remota, è necessario:  
  
-   Dispone di un account di amministratore di sistema della piattaforma Analitica con la possibilità di accedere direttamente al  ***appliance_domain*-AD01** e  ***appliance_domain*-AD02** nodi.  
  
-   Conoscere il nome host o IP del server di destinazione.  
  
## <a name="HowToPDW"></a>Configurare SQL Server PDW per copia della tabella remota: aggiornare i nomi Host in DNS  
Il **CREATE REMOTE TABLE** istruzione utilizzata per le copie di tabella remota, specifica il server di destinazione utilizzando l'indirizzo IP o il nome IP del sistema Windows SMP. Per utilizzare il nome dell'IP, è necessario aggiungere voci per la risoluzione dei nomi corretta per il server DNS.  
  
Di seguito viene illustrato come aggiornare il server DNS.  
  
1.  Accedere al nodo attivo di Active Directory (in genere  ***appliance_domain*-AD01**).  
  
2.  Aprire Gestore DNS. Il file si trova in **strumenti di amministrazione** nel **avviare** menu.  
  
3.  Utilizzare la gestione di DNS per aggiungere il nome IP.  
  
## <a name="see-also"></a>Vedere anche  
<!-- MISSING LINKS 
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
[Utilizzare un server d'inoltro DNS per risolvere i nomi DNS Non strumento](use-a-dns-forwarder-to-resolve-non-appliance-dns-names.md)  
<!-- MISSING LINKS 
[Security - Configure Domain Trusts &#40;SQL Server PDW&#41;](../sqlpdw/security-configure-domain-trusts-sql-server-pdw.md)  
-->
  
