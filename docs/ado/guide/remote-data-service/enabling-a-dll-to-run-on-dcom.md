---
title: Attivazione di una DLL per l'esecuzione su DCOM | Documenti Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DLL on DCOM in RDS [ADO]
- DCOM in RDS [ADO]
- business objects in RDS [ADO]
ms.assetid: 5f1c2205-191c-4fb4-9bd9-84c878ea46ed
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e2d67a595c97547934b04794f036d58445e8c282
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="enabling-a-dll-to-run-on-dcom"></a>Attivazione di una DLL per l'esecuzione su DCOM
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Di seguito viene illustrato come abilitare una DLL di oggetto business di utilizzare DCOM e Microsoft Internet Information Services (HTTP) tramite Servizi componenti.  
  
1.  Nello snap-in MMC Servizi componenti, creare un nuovo pacchetto vuoto.  
  
     Utilizzare lo snap-in MMC Servizi componenti per creare un pacchetto e aggiungere la DLL in questo pacchetto. In questo modo la DLL accessibile tramite DCOM, ma rimuove l'accessibilità tramite IIS. (Se si archivia il Registro di sistema per il file DLL, il **Inproc** chiave è vuota; l'impostazione dell'attributo di attivazione, descritto più avanti in questo argomento, aggiunge un valore nel **Inproc** chiave.)  
  
2.  Installare un oggetto business nel pacchetto.  
  
     oppure  
  
     Importazione di [RDSServer](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) oggetto nel pacchetto.  
  
3.  Impostare l'attributo di attivazione per il pacchetto **nel processo di creazione** (applicazione libreria).  
  
     Per rendere la DLL accessibile tramite DCOM e IIS nello stesso computer, è necessario impostare l'attributo di attivazione del componente snap-in MMC Servizi componenti. Dopo aver impostato l'attributo su **nel processo di creazione**, si noterà che un **Inproc** chiave server nel Registro di sistema è stata aggiunta che punta a un componente di servizi di surrogati. dll.  
  
 Per ulteriori informazioni su Servizi componenti (o del servizio Microsoft Transaction, se si utilizza Windows NT) e su come eseguire questi passaggi, visitare il sito Web di Microsoft Transaction Server.



