---
title: Elemento DatabaseName (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DatabaseName Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.databasename
- http://schemas.microsoft.com/analysisservices/2003/engine#DatabaseName
- urn:schemas-microsoft-com:xml-analysis#DatabaseName
helpviewer_keywords:
- DatabaseName element
ms.assetid: 5cfd9a1f-da53-497a-b677-c51be4641bd0
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c4727f3554b654687484e6bd273a0d88e557215e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48172681"
---
# <a name="databasename-element-xmla"></a>Elemento DatabaseName (XMLA)
  Identifica la [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] database da ripristinare dall'elemento padre [ripristinare](../xml-elements-commands/restore-element-xmla.md) comando.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Restore>  
   ...  
   <DatabaseName>...</DatabaseName>  
   ...  
</Restore>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Ripristina](../xml-elements-commands/restore-element-xmla.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Note  
 L'elemento `DatabaseName` identifica il database in cui il comando `Restore` ripristina un file di backup. Se questo elemento non è specificato o contiene una stringa vuota, viene utilizzato il nome del database contenuto nel file di backup.  
  
 Se il database esiste già nell'istanza di destinazione, si verifica un errore a meno che l'elemento `AllowOverwrite` per il comando padre `Restore` non sia impostato su `True`.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento AllowOverwrite &#40;XMLA&#41;](allowoverwrite-element-xmla.md)   
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
