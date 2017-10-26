---
title: Guida di riferimento a PowerShell per il motore di database | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3c379a43-c497-47dd-8e7d-2b015c068bb7
caps.latest.revision: 8
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: dc3df1d697b05201ac48520c1e344c28648cdfaf
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="database-engine-powershell-reference"></a>Guida di riferimento a PowerShell per il motore di database
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] include un set di cmdlet di Windows PowerShell per l'esecuzione di azioni comuni nel [!INCLUDE[ssDE](../includes/ssde-md.md)]. È possibile inoltre convertire espressioni di query e Uniform Resource Name (URN) nei percorsi di SQL Server PowerShell o utilizzarli per specificare uno o più oggetti in [!INCLUDE[ssDE](../includes/ssde-md.md)].  
  
## <a name="database-engine-cmdlets"></a>Cmdlet del motore di database  
 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] include un numero relativamente basso di cmdlet per il [!INCLUDE[ssDE](../includes/ssde-md.md)]. La maggior parte degli script di PowerShell che funzionano con [!INCLUDE[ssDE](../includes/ssde-md.md)] utilizzano il provider di PowerShell per SQL Server e i modelli a oggetti di facilità di gestione di SQL Server. Per altre informazioni, vedere [Provider PowerShell per SQL Server](../relational-databases/scripting/sql-server-powershell-provider.md).  
  
 Per informazioni sulla Guida dei cmdlet di SQL Server in un ambiente Windows PowerShell, vedere [Visualizzazione della Guida di SQL Server PowerShell](../relational-databases/scripting/get-help-sql-server-powershell.md).  
  
### <a name="in-this-section"></a>Argomenti della sezione  
 In questa sezione sono incluse informazioni sui cmdlet indicati.  
  
|Descrizione|Cmdlet|  
|-----------------|------------|  
|Esegue script Transact-SQL e XQuery, ad esempio script che possono essere eseguiti tramite l'utilità **sqlcmd** .|[Cmdlet Invoke-Sqlcmd](../powershell/invoke-sqlcmd-cmdlet.md)|  
|Valuta se un oggetto Motore di database è conforme alla gestione basata su criteri.|[cmdlet Invoke-PolicyEvaluation](../powershell/invoke-policyevaluation-cmdlet.md)|  
  
### <a name="information-about-other-cmdlets"></a>Informazioni su altri cmdlet  
 I cmdlet **Encode-Sqlname** e **Decode-Sqlname** consentono di specificare identificatori SQL Server che contengono caratteri non supportati nei percorsi di Windows PowerShell. Per altre informazioni, vedere [Identificatori di SQL Server in PowerShell](../relational-databases/scripting/sql-server-identifiers-in-powershell.md).  
  
 Usare il cmdlet **Convert-UrnToPath** per convertire l'URN (Uniform Resource Name) di un oggetto [!INCLUDE[ssDE](../includes/ssde-md.md)] in un percorso del provider PowerShell SQL Server. Per altre informazioni, vedere [Conversione di URN in percorsi di provider di SQL Server](../relational-databases/scripting/convert-urns-to-sql-server-provider-paths.md).  
  
## <a name="query-expressions-and-unique-resource-names"></a>Espressioni di query e Unique Resource Name  
 Le espressioni di query sono stringhe che utilizzano una sintassi analoga a XPath per specificare un set di criteri utilizzato per enumerare uno o più oggetti in una gerarchia del modello a oggetti. L'URN (Unique Resource Name) è un tipo specifico di stringa di espressione di query che identifica un singolo oggetto in modo univoco. Per altre informazioni, vedere [Espressioni di query e Uniform Resource Name](../powershell/query-expressions-and-uniform-resource-names.md).  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server PowerShell](../relational-databases/scripting/sql-server-powershell.md)  
  
  

