---
title: Convertire URN in percorsi di provider di SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c9b1b8f1-b117-4e87-9704-2170f62c5c8b
caps.latest.revision: 8
author: mgblythe
ms.author: mblythe
manager: jhubbard
ms.openlocfilehash: 925eec025bb2943845748acd30e8f24693245ae2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36166687"
---
# <a name="convert-urns-to-sql-server-provider-paths"></a>Conversione di URN in percorsi di provider di SQL Server
  Il modello SMO ( [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Management Objects) consente di compilare URN (Uniform Resource Name) per gli oggetti. Ogni URN identifica in modo univoco un oggetto SMO e può essere convertito in un percorso del provider PowerShell per SQL Server utilizzando il `Convert-UrnToPath` cmdlet.  
  
## <a name="converting-urns-to-paths"></a>Conversione di URN in percorsi  
 Ciascun URN dispone delle stesse informazioni di un percorso dell'oggetto, ma in formato diverso. Ad esempio, di seguito è riportato il percorso di una tabella:  
  
 SQLSERVER:\SQL\MyComputer\DEFAULT\Databases\AdventureWorks2012\Tables\Person.Address  
  
 Di seguito è riportato l'URN dello stesso oggetto:  
  
 Server[@Name='MyComputer']\Database[@Name='AdventureWorks2012']\Table[@Name='Address' and @Schema='Person']  
  
 Se è stato creato un oggetto SMO in uno script di PowerShell, è possibile fare riferimento alla proprietà `Urn` per ottenere l'URN dell'oggetto e quindi utilizzare il cmdlet `Convert-UrnToPath` per convertire la stringa URN SMO in un percorso di Windows PowerShell. È quindi possibile utilizzare il provider per passare a posizioni diverse nel percorso.  
  
 Se i nomi di nodo contengono caratteri estesi non supportati nei nomi di percorso di Windows PowerShell, `Convert-UrnToPath` li codifica nella rappresentazione esadecimale. Ad esempio, "My:Table" viene restituito come "My%3ATable".  
  
 Per esempi dell'utilizzo del cmdlet, in Windows PowerShell eseguire:  
  
```  
Get-Help Convert-UrnToPath -Examples  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Espressioni di query e Uniform Resource Name](../powershell/query-expressions-and-uniform-resource-names.md)   
 [Provider PowerShell per SQL Server](../powershell/sql-server-powershell-provider.md)   
 [SQL Server PowerShell](../powershell/sql-server-powershell.md)  
  
  