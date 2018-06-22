---
title: Identificatori di escape di SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8a73e945-daa6-4e5d-93da-10f000f1f3a2
caps.latest.revision: 6
author: mgblythe
ms.author: mblythe
manager: jhubbard
ms.openlocfilehash: b11d666165c266467fbdbe46a5d95fb8d7dbad70
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36064481"
---
# <a name="escape-sql-server-identifiers"></a>Identificatori di escape di SQL Server
  Spesso è possibile utilizzare l'apice inverso di Windows PowerShell (`) come carattere di escape per i caratteri consentiti negli identificatori delimitati di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ma non per i nomi dei percorsi di Windows PowerShell. Tuttavia, alcuni caratteri non supportano l'utilizzo dei caratteri di escape. Ad esempio, non è possibile utilizzare i caratteri di escape per i due punti (:) in Windows PowerShell. Gli identificatori che contengono tale carattere devono essere codificati. La codifica è più affidabile dell'utilizzo dei caratteri di escape in quanto è supportata da tutti i caratteri.  
  
## <a name="before-you-begin"></a>Prima di iniziare  
 L'apice inverso (`) è posto generalmente sul tasto superiore sinistro della tastiera, sotto il tasto ESC.  
  
## <a name="examples"></a>Esempi  
 Di seguito è riportato un esempio di utilizzo dei caratteri di escape in un carattere #:  
  
```  
cd SQLSERVER:\SQL\MyComputer\MyInstance\MyDatabase\MySchema\`#MyTempTable  
```  
  
 Di seguito viene riportato un esempio dell'utilizzo di caratteri di escape parentesi in caso di specifica (impostazioni locali) come nome del computer:  
  
```  
Set-Location SQLSERVER:\SQL\`(local`)\DEFAULT  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Identificatori di SQL Server in PowerShell](sql-server-identifiers-in-powershell.md)   
 [Provider PowerShell per SQL Server](sql-server-powershell-provider.md)   
 [SQL Server PowerShell](sql-server-powershell.md)  
  
  