---
title: Elemento password (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Password Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Password
- urn:schemas-microsoft-com:xml-analysis#Password
- microsoft.xml.analysis.password
helpviewer_keywords:
- Password element
ms.assetid: 8a0603bd-f6a1-4b86-84f1-c83d0b03951b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a72d111dd6bccec8b6b40440a0e40e5a6669d87e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48159181"
---
# <a name="password-element-xmla"></a>Elemento Password (XMLA)
  Determina la password da utilizzare dall'elemento padre [Backup](../xml-elements-commands/backup-element-xmla.md) oppure [ripristinare](../xml-elements-commands/restore-element-xmla.md) comando per la crittografia o decrittografia di un file di backup.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Backup> <!-- or Restore -->  
   ...  
   <Password>...</Password>  
   ...  
</Backup>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Copia di backup](../xml-elements-commands/backup-element-xmla.md), [ripristinare](../xml-elements-commands/restore-element-xmla.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Per i comandi `Backup`, se l'elemento `Password` non è incluso o contiene una stringa vuota, il file di backup non viene crittografato.  
  
 Per i comandi `Restore`, se l'elemento `Password` non è incluso o contiene una stringa vuota, durante il tentativo di ripristinare un file di backup crittografato si verifica un errore.  
  
 Se in un comando `Location` o `Backup` sono inclusi elementi `Restore`, lo stesso elemento `Password` viene utilizzato sia per i file di backup che per quelli di backup remoto. Per altre informazioni sui file di backup remoti, vedere [backup, ripristino e sincronizzazione di database &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento location &#40;XMLA&#41;](location-element-xmla.md)   
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
