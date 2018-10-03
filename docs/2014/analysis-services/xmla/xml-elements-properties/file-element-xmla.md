---
title: File di elemento (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- File Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.file
- http://schemas.microsoft.com/analysisservices/2003/engine#File
- urn:schemas-microsoft-com:xml-analysis#File
helpviewer_keywords:
- File element
ms.assetid: 3dfd0e9b-746b-4ce5-8a95-610d2e573739
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a5ae3390405bc7a722934f3b3fb3652825b2ea03
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48125451"
---
# <a name="file-element-xmla"></a>Elemento File (XMLA)
  Identifica un file da utilizzare dall'elemento padre [Backup](../xml-elements-commands/backup-element-xmla.md) oppure [ripristinare](../xml-elements-commands/restore-element-xmla.md) comando o dall'elemento padre [percorso](location-element-xmla.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Backup> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <File>...</File>  
   ...  
</Backup>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|None|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Copia di backup](../xml-elements-commands/backup-element-xmla.md), [posizione](location-element-xmla.md), [ripristinare](../xml-elements-commands/restore-element-xmla.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 L'elemento `File` contiene un nome file UNC e l'elemento padre determina l'utilizzo dell'elemento `File`.  
  
 Per i comandi `Backup`, l'elemento `File` determina il nome del file di backup creato dal comando `Backup`. Se un percorso non è specificato come parte del nome file, il percorso specificato nella `BackupDir` proprietà di configurazione per l'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] viene usato. Se il file specificato è già presente, si verifica un errore, a meno che l'elemento `AllowOverwrite` del comando padre `Backup` non sia impostato su `True`.  
  
 Per i comandi `Restore`, l'elemento `File` determina il nome del file di backup da ripristinare tramite il `Restore`.  
  
 Per gli elementi `Location`, l'elemento `File` descrive un file di backup remoto per un'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] che contiene partizioni remote. Per altre informazioni sul backup e ripristino di partizioni remote, vedere [backup, ripristino e sincronizzazione di database &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento AllowOverwrite &#40;XMLA&#41;](allowoverwrite-element-xmla.md)   
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
