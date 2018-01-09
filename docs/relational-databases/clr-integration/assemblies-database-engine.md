---
title: Assembly (motore di Database) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- assemblies [CLR integration]
- assemblies [CLR integration], about assemblies
- managed code [SQL Server], assemblies
ms.assetid: 4b146437-3061-47f6-9e8c-26eeea10b54e
caps.latest.revision: "28"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: daad8dc42b5bf8825ce20ce631a3dedc37f7f303
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="assemblies-database-engine"></a>Assembly (Motore di database)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]In questa sezione vengono fornite informazioni utili per comprendere, progettare e implementare assembly.  
  
 Gli assembly sono file DLL utilizzati in un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per distribuire funzioni, stored procedure, trigger, aggregazioni definite dall'utente e tipi definiti dall'utente che vengono scritti in uno dei linguaggi di codice gestito ospitati dal [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Common language runtime (CLR), anziché in [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 Un assembly di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è un oggetto che fa riferimento a un modulo di applicazione gestito (file con estensione dll) creato nel linguaggio CLR di [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]. Un assembly contiene i metadati della classe e codice gestito. Il caricamento di un assembly in un'istanza di SQL Server è il primo passaggio da eseguire per creare uno degli oggetti di database seguenti:  
  
-   Funzioni CLR. Per ulteriori informazioni, vedere [creare funzioni CLR](../../relational-databases/user-defined-functions/create-clr-functions.md).  
  
-   Stored procedure CLR. Per ulteriori informazioni, vedere [Stored procedure CLR](http://msdn.microsoft.com/library/bbdd51b2-a9b4-4916-ba6f-7957ac6c3f33).  
  
-   Trigger CLR. Per ulteriori informazioni, vedere [creare trigger CLR](../../relational-databases/triggers/create-clr-triggers.md).  
  
-   Funzioni di aggregazione definite dall'utente. Per ulteriori informazioni, vedere [le aggregazioni definite dall'utente di creare](../../relational-databases/user-defined-functions/create-user-defined-aggregates.md).  
  
-   Tipi definiti dall'utente. Per ulteriori informazioni, vedere [User-Defined Type](../../relational-databases/native-client/features/using-user-defined-types.md).  
  
 Gli assembly svolgono le funzioni seguenti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   Includono il codice gestito che esegue le funzionalità di uno o più degli oggetti di database CLR elencati in precedenza.  
  
-   Contengono i metadati che includono il numero di versione e la lingua dell'assembly, una chiave pubblica facoltativa che identifica l'elenco delle classi dell'assembly, i metodi definiti nell'assembly e l'architettura del processore dell'assembly.  
  
-   Gestiscono il livello di accesso del codice gestito alle risorse esterne tramite l'impostazione delle autorizzazioni di accesso per il codice.  
  
-   Includono i metadati relativi alle dipendenze da altri assembly a cui viene fatto riferimento nell'assembly.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Progettazione di assembly](../../relational-databases/clr-integration/assemblies-designing.md)|Descrive gli elementi da tenere in considerazione prima di creare un assembly, che includono l'assemblaggio degli assembly, le autorizzazioni di accesso per il codice e altre restrizioni.|  
|[Implementazione di assembly](../../relational-databases/clr-integration/assemblies-implementing.md)|Illustra come creare ed eliminare gli assembly, come e quando modificare gli assembly e come recuperare i metadati relativi agli assembly.|  
|[Recupero di informazioni sugli assembly](../../relational-databases/clr-integration/assemblies-getting-information.md)|Elenca le viste del catalogo e le funzioni sulle quali è possibile eseguire query relative agli assembly.|  
  
## <a name="see-also"></a>Vedere anche  
 [Concetti relativi alla programmazione dell'integrazione con CLR &#40;Common Language Runtime&#41;](../../relational-databases/clr-integration/common-language-runtime-clr-integration-programming-concepts.md)  
  
  
