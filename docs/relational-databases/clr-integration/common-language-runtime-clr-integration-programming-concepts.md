---
title: Common Language Runtime (CLR) integrazione programmazione di concetti | Documenti Microsoft
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: clr
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- CLR [SQL Server] See common language runtime [SQL Server]
- Database Engine [SQL Server], .NET Framework
- .NET Framework [SQL Server], Database Engine programming
- common language runtime [SQL Server]
- .NET Framework [SQL Server]
ms.assetid: 951bf851-3e6e-4361-ae6a-2bcd5b837ebd
caps.latest.revision: 59
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 41c8382d933a02d26ca47bfc76acc4d2563fce62
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="common-language-runtime-clr-integration-programming-concepts"></a>Concetti relativi alla programmazione dell'integrazione con CLR (Common Language Runtime)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  A partire da [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è inclusa l'integrazione del componente CRL (Common Language Runtime) di .NET Framework per [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. È pertanto possibile scrivere stored procedure, trigger, tipi definiti dall'utente, funzioni definite dall'utente, funzioni di aggregazione definite dall'utente e funzioni di flusso con valori di tabella usando qualsiasi linguaggio di .NET Framework, inclusi [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic .NET e [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C#.  
  
 Lo spazio dei nomi Microsoft.SqlServer.Server include la funzionalità principali per la programmazione CLR in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Lo spazio dei nomi Microsoft.SqlServer.Server, tuttavia, viene trattato nella documentazione di .NET Framework SDK. Questa documentazione non è inclusa nella documentazione online di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  Per impostazione predefinita, durante l'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene installato .NET Framework, ma non .NET Framework SDK. Se SDK non è installato nel computer né incluso nella raccolta della documentazione online, i collegamenti al contenuto SDK presenti in questa sezione non funzionano. Installare .NET Framework SDK, Una volta installato, aggiungere SDK alla documentazione Online e al sommario seguendo le istruzioni in [l'installazione di .NET Framework SDK](http://technet.microsoft.com/library/bb686823\(v=SQL.105\).aspx).  
  
> [!NOTE]  
>  Funzionalità Common Language Runtime, ad esempio le funzioni utente CLR sono *non* supportata per Database SQL di Azure.  
  
 Nella tabella seguente vengono elencati gli argomenti disponibili in questa sezione.  
  
 [Common Language Runtime & #40; Common Language Runtime & #41; Panoramica dell'integrazione](../../relational-databases/clr-integration/common-language-runtime-integration-overview.md)  
 Viene fornita una breve panoramica di CLR e vengono descritti i motivi e le modalità dell'utilizzo di questa tecnologia in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Vengono inoltre descritti i vantaggi dell'utilizzo di CLR per creare oggetti di database.  
  
 [Assembly &#40;Motore di database&#41;](../../relational-databases/clr-integration/assemblies-database-engine.md)  
 Viene descritto come usare gli assembly in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per distribuire funzioni, stored procedure, trigger, aggregazioni definite dall'utente e tipi definiti dall'utente scritti usando uno dei linguaggi di codice gestito di Common Language Runtime (CLR) di [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework e non [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 [Compilazione di oggetti di Database con Common Language Runtime & #40; Common Language Runtime & #41; Integrazione di](../../relational-databases/clr-integration/database-objects/building-database-objects-with-common-language-runtime-clr-integration.md)  
 Vengono descritti i tipi di oggetti che è possibile compilare usando CLR e vengono esaminati i requisiti per la compilazione di oggetti di database CLR.  
  
 [Accesso ai dati da oggetti di database CLR](../../relational-databases/clr-integration/data-access/data-access-from-clr-database-objects.md)  
 Viene descritto il modo in cui una routine CLR può accedere a dati archiviati in un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Sicurezza dell'integrazione con CLR](../../relational-databases/clr-integration/security/clr-integration-security.md)  
 Viene descritto il modello di sicurezza dell'integrazione CLR.  
  
 [Debug di oggetti di Database CLR](../../relational-databases/clr-integration/debugging-clr-database-objects.md)  
 Vengono descritte le limitazioni e i requisiti per il debug di oggetti di database CLR.  
  
 [Distribuzione di oggetti di Database CLR](../../relational-databases/clr-integration/deploying-clr-database-objects.md)  
 Viene descritta la distribuzione di assembly in server di produzione.  
  
 [Gestione degli assembly di integrazione CLR](../../relational-databases/clr-integration/assemblies/managing-clr-integration-assemblies.md)  
 Viene descritto come creare ed eliminare assembly di integrazione CLR.  
  
 [Monitoraggio e risoluzione dei problemi di oggetti di Database gestiti](../../relational-databases/clr-integration/monitoring-and-troubleshooting-managed-database-objects.md)  
 Vengono fornite informazioni sugli strumenti che è possibile usare per monitorare e risolvere i problemi relativi agli oggetti di database e agli assembly gestiti in esecuzione in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Scenari di utilizzo ed esempi di Common Language Runtime & #40; Common Language Runtime & #41; Integrazione di](http://msdn.microsoft.com/library/33aac25f-abb4-4f29-af88-4a0dacd80ae7)  
 Vengono descritti gli scenari di utilizzo e gli esempi di codice che usano oggetti CLR.  
  
## <a name="see-also"></a>Vedere anche  
 [Assembly & #40; motore di Database & #41;](../../relational-databases/clr-integration/assemblies-database-engine.md)   
 [Installazione di .NET Framework SDK](http://technet.microsoft.com/library/bb686823\(v=SQL.105\).aspx)  
  
  
