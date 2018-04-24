---
title: Configurare Parallel Data Warehouse per la tabella remota copie | Documenti Microsoft
description: Viene descritto come configurare Parallel Data Warehouse per utilizzare la funzionalità di copia della tabella remota per copiare le tabelle ai database SMP SQL Server nei server non strumento.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 3f71a0c67639918820bca8f6f8f38b9f354154f3
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="configure-parallel-data-warehouse-for-remote-table-copies"></a>Configurare Parallel Data Warehouse per le copie di tabella remota
Viene descritto come configurare SQL Server PDW per utilizzare la funzionalità di copia della tabella remota per copiare le tabelle per database SMP SQL Server nel server non strumento.  
  
In questo argomento viene descritto uno dei passaggi di configurazione per la configurazione di copia della tabella remota. Per un elenco di tutti i passaggi di configurazione, vedere [copia della tabella remota](remote-table-copy.md).  
  
## <a name="before-you-begin"></a>Prima di iniziare  
Per configurare SQL Server PDW per l'utilizzo di copia della tabella remota, è necessario:  
  
-   Dispone di un account di amministratore di sistema della piattaforma Analitica con la possibilità di accedere direttamente al ***appliance_domain *-AD01** e ***appliance_domain *-AD02** nodi.  
  
-   Conoscere il nome host o IP del server di destinazione.  
  
## <a name="HowToPDW"></a>Configurare SQL Server PDW per copia della tabella remota: aggiornare i nomi Host in DNS  
Il **CREATE REMOTE TABLE** istruzione utilizzata per le copie di tabella remota, specifica il server di destinazione utilizzando l'indirizzo IP o il nome IP del sistema Windows SMP. Per utilizzare il nome dell'IP, è necessario aggiungere voci per la risoluzione dei nomi corretta per il server DNS.  
  
Di seguito viene illustrato come aggiornare il server DNS.  
  
1.  Accedere al nodo attivo di Active Directory (in genere ***appliance_domain *-AD01**).  
  
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
  
