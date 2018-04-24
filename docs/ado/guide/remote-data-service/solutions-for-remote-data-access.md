---
title: Soluzioni per l'accesso a dati remoti | Documenti Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS [ADO]
ms.assetid: d311cc67-7db7-4c43-9590-d465564695e4
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 84030d05131d8a410690a6896b5173da356240c3
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="solutions-for-remote-data-access"></a>Soluzioni per l'accesso a dati remoti
## <a name="the-issue"></a>Il problema  
 ADO consente all'applicazione di accedere direttamente e modificare origini dati (detta anche un sistema a due livelli). Ad esempio, se la connessione all'origine dati che contiene i dati, che è una connessione diretta in un sistema a due livelli.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Tuttavia, è consigliabile accedere a origini dati indirettamente tramite un intermediario, ad esempio Microsoft® Internet Information Services (IIS). Questa disposizione è detto anche un sistema a tre livelli. IIS è un sistema client/server che fornisce un modo efficiente per un'applicazione locale o dal client richiamare un programma remoto o nel server, in Internet o intranet. Il programma server accede all'origine dati e, facoltativamente, elabora i dati acquisiti.  
  
 Ad esempio, la pagina Web intranet contiene un'applicazione scritta in Microsoft® Visual Basic Scripting Edition (VBScript), che si connette a IIS. IIS a sua volta si connette all'origine dei dati effettivi, recupera i dati, viene elaborato in qualche modo e quindi restituisce le informazioni elaborate all'applicazione.  
  
 In questo esempio, l'applicazione mai connessi direttamente a origine dati. Stato di IIS. IIS i dati di accedere tramite ADO.  
  
> [!NOTE]
>  L'applicazione client/server non deve essere basata su Internet o intranet (ovvero, basata sul Web), può essere costituito esclusivamente programmi compilati su una rete locale. Tuttavia, il caso tipico è un'applicazione basata sul Web.  
  
 Poiché per alcuni controlli visuali, ad esempio una griglia, una casella di controllo o un elenco, è possono utilizzare le informazioni restituite, le informazioni restituite devono essere facilmente usate da un controllo visivo.  
  
 Si desidera un'interfaccia di programmazione di applicazioni semplice ed efficiente che supporta i sistemi a tre livelli che restituisce informazioni come facilmente come se fosse stato recuperato in un sistema a due livelli. Remote Data Service (RDS) è questa interfaccia.  
  
## <a name="the-solution"></a>Soluzione  
 Servizi Desktop remoto definisce un modello di programmazione, la sequenza di attività necessarie per accedere e aggiornare un'origine dati, per ottenere l'accesso ai dati tramite un intermediario, ad esempio Internet Information Services (IIS). Il modello di programmazione riepiloga l'intera funzionalità di RDS.  
  
## <a name="see-also"></a>Vedere anche  
 [Modello di programmazione di base di servizi desktop remoto](../../../ado/guide/remote-data-service/basic-rds-programming-model.md)   
 [Scenario di servizi desktop remoto](../../../ado/guide/remote-data-service/rds-scenario.md)   
 [Esercitazione di servizi desktop remoto](../../../ado/guide/remote-data-service/rds-tutorial.md)   
 [Utilizzo e sicurezza per RDS](../../../ado/guide/remote-data-service/rds-usage-and-security.md)


