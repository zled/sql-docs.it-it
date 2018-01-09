---
title: Attributi personalizzati per routine CLR | Documenti Microsoft
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
- routines [CLR integration]
- SqlFacet attribute
- SqlTrigger attribute
- SqlProcedure attribute
- custom attributes [CLR integration]
- SqlUserDefinedAggregate attribute
- attributes [CLR integration]
- SqlMethod attribute
- SqlFunction attribute
- common language runtime [SQL Server], attributes
- SqlUserDefinedTypeAttribute attribute
ms.assetid: 95069d22-b05d-4670-b053-15ee2a664e33
caps.latest.revision: "82"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d9f7d12c087ad75ab8734d4e1e722402abf04a09
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="clr-integration-custom-attributes-for-clr-routines"></a>Attributi personalizzati di integrazione CLR per le routine CLR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Gli attributi elencati possono essere applicati per le routine di common language runtime (CLR), tipi definiti dall'utente e aggregazioni definite dall'utente che sono registrate in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Se l'attributo non viene applicato, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] assume il valore predefinito. Gli attributi elencati vengono definiti nel **Microsoft.SqlServer.Server** dello spazio dei nomi.  
  
## <a name="the-sqluserdefinedaggregate-attribute"></a>Attributo SqlUserDefinedAggregate  
 Il **SqlUserDefinedAggregate** attributo indica che il metodo deve essere registrato come una funzione di aggregazione definita dall'utente. Ogni aggregazione definita dall'utente deve essere annotata con questo attributo.  
  
 Per ulteriori informazioni, vedere [SqlUserDefinedAggregateAttribute](http://go.microsoft.com/fwlink/?LinkId=124626).  
  
## <a name="the-sqlfunction-attribute"></a>Attributo SqlFunction  
 Il **SqlFunction** attributo indica il metodo deve essere registrato come una funzione, con il set di attributi di funzione appropriata.  
  
 Per ulteriori informazioni, vedere [SqlFunctionAttribute](http://go.microsoft.com/fwlink/?LinkId=128019).  
  
## <a name="the-sqlfacet-attribute"></a>Attributo SqlFacet  
 Il **SqlFacet** attributo viene utilizzato per restituire le informazioni relative al tipo restituito di un'espressione di tipo definito dall'utente (UDT).  
  
 Per ulteriori informazioni, vedere [SqlFacetAttribute](http://go.microsoft.com/fwlink/?LinkId=128020).  
  
## <a name="the-sqlprocedure-attribute"></a>Attributo SqlProcedure  
 Il **SqlProcedure** attributo indica il metodo deve essere registrato come stored procedure. Questo attributo viene utilizzato solo da Visual Studio per registrare automaticamente il metodo specificato come stored procedure. Non viene utilizzato da [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Per ulteriori informazioni, vedere [SqlProcedureAttribute](http://go.microsoft.com/fwlink/?LinkId=128021).  
  
## <a name="the-sqltrigger-attribute"></a>Attributo SqlTrigger  
 Il **SqlTrigger** attributo indica il metodo deve essere registrato come trigger.  
  
 Per ulteriori informazioni, vedere [SqlTriggerContext](http://go.microsoft.com/fwlink/?LinkId=128022) e [SqlTriggerAttribute](http://go.microsoft.com/fwlink/?LinkId=203898).  
  
## <a name="the-sqluserdefinedtypeattribute"></a>Attributo SqlUserDefinedTypeAttribute  
 È possibile applicare l'attributo SqlUserDefinedTypeAttribute a una definizione di classe nell'assembly. In questo caso, in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] viene creato un tipo definito dall'utente associato alla definizione di classe che include l'attributo personalizzato.  
  
 Per ulteriori informazioni, vedere [SqlUserDefinedTypeAttribute](http://go.microsoft.com/fwlink/?LinkId=128024).  
  
## <a name="the-sqlmethod-attribute"></a>Attributo SqlMethod  
 Il **SqlMethod** attributo viene utilizzato per indicare le proprietà di accesso determinismo e dati di un metodo o una proprietà in un tipo definito dall'utente.  
  
 Per ulteriori informazioni, vedere [SqlMethodAttribute](http://go.microsoft.com/fwlink/?LinkId=128025).  
  
## <a name="see-also"></a>Vedere anche  
 [Aggregazioni CLR definite dall'utente](../../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md)   
 [Funzioni CLR definite dall'utente](../../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md)   
 [Tipi CLR definiti dall'utente](../../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)   
 [Stored procedure CLR](http://msdn.microsoft.com/library/bbdd51b2-a9b4-4916-ba6f-7957ac6c3f33)   
 [Trigger CLR](http://msdn.microsoft.com/library/302a4e4a-3172-42b6-9cc0-4a971ab49c1c)  
  
  
