---
title: Esecuzione di oggetti Business in Servizi componenti | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- component services in RDS [ADO]
ms.assetid: 3077d0b6-42d6-4f10-8e5d-42e6204f1109
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: abb4f5b48c17c720c94ced62139c534acebf2e05
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="running-business-objects-in-component-services"></a>Esecuzione di oggetti Business in Servizi componenti
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Gli oggetti business possono essere file eseguibili (.exe) o librerie a collegamento dinamico (DLL). La configurazione utilizzata per eseguire l'oggetto business dipende se l'oggetto è un file con estensione dll o .exe:  
  
-   Gli oggetti business creati come file .exe possono essere chiamati tramite DCOM. Se vengono utilizzati tramite Internet Information Services (IIS), sono soggette a ulteriori marshalling dei dati, che può rallentare le prestazioni di client.  
  
-   Gli oggetti business creati come file con estensione DLL possono essere utilizzati tramite IIS e, pertanto anche tramite HTTP. Possono inoltre essere utilizzati su DCOM solo tramite Servizi componenti o tramite Microsoft Transaction Server, se si utilizza Windows NT. Oggetto business dll dovrà essere registrato nel computer del server IIS di accedervi tramite IIS. Per informazioni su come configurare una DLL per l'esecuzione su DCOM, vedere la sezione [attivazione di una DLL per l'esecuzione su DCOM](../../../ado/guide/remote-data-service/enabling-a-dll-to-run-on-dcom.md).  
  
> [!NOTE]
>  Quando gli oggetti di business nel livello intermedio vengono implementati come componenti di Servizi componenti utilizzando **GetObjectContext**, **SetComplete**, e **SetAbort**, il business gli oggetti possono utilizzare Servizi componenti (o MTS, se si utilizza Windows NT) gli oggetti di contesto per mantenere il proprio stato tra più chiamate del client. Questo scenario è possibile con DCOM, che viene in genere implementato tra client e server in una rete intranet attendibili. In questo caso, il [RDS. DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md) oggetto e [CreateObject](../../../ado/reference/rds-api/createobject-method-rds.md) metodo sul lato client vengono sostituiti da oggetto contesto di transazione e **CreateInstance** (metodo), che sono fornite dal **ITransactionContext** l'interfaccia e implementati da Servizi componenti.  
  
## <a name="see-also"></a>Vedere anche  
 [Nozioni fondamentali su RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)


