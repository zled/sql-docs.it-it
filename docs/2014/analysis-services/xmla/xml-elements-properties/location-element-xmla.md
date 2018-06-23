---
title: Elemento location (XMLA) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Location Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.location
- urn:schemas-microsoft-com:xml-analysis#Location
- http://schemas.microsoft.com/analysisservices/2003/engine#Location
helpviewer_keywords:
- Location element
ms.assetid: cea5e776-f435-425a-9bce-812d727a2b71
caps.latest.revision: 12
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 51b0838b9843658b4081f9464c63274631ed74be
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36168603"
---
# <a name="location-element-xmla"></a>Elemento Location (XMLA)
  Contiene informazioni su un server remoto per l'elemento padre [Backup](../xml-elements-commands/backup-element-xmla.md), [ripristinare](../xml-elements-commands/restore-element-xmla.md), o [Synchronize](../xml-elements-commands/synchronize-element-xmla.md) comando.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Backup> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <Location>  
```  
  
```  
  
<File>...</File> <!-- for Backup and Restore only -->  
<DataSourceID>...</DataSourceID>  
<DataSourceType>...</DataSourceType> <!-- for Restore and Synchronize only -->  
<ConnectionString>...</ConnectionString> <!-- for Restore and Synchronize only -->  
<Folders>...</Folders> <!-- for Restore and Synchronize only -->  
```  
  
```  
  
   </Location>  
   ...  
</Backup>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Backup](../xml-elements-commands/backup-element-xmla.md), [ripristinare](../xml-elements-commands/restore-element-xmla.md), [sincronizzare](../xml-elements-commands/synchronize-element-xmla.md)|  
  
## <a name="child-elements"></a>Elementi figlio  
  
|Predecessore o padre|Elemento figlio|  
|------------------------|-------------------|  
|[Backup](id-element-xmla.md), [File](file-element-xmla.md)|  
|[Ripristinare](connectionstring-element-xmla.md), [DataSourceID](datasourceid-element-xmla.md), [DataSourceType](type-element-xmla.md), [File](file-element-xmla.md), [cartelle](folders-element-xmla.md)|  
|[Sincronizza](../xml-elements-commands/synchronize-element-xmla.md)|[ConnectionString](connectionstring-element-xmla.md), [DataSourceID](datasourceid-element-xmla.md), [DataSourceType](type-element-xmla.md), [cartelle](folders-element-xmla.md)|  
  
## <a name="remarks"></a>Remarks  
 Per `Backup` comandi, il `Location` elemento fornisce informazioni sulla creazione di un file di backup remoto per un'istanza remota di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 Per i comandi `Restore`, l'elemento `Location` fornisce informazioni sull'identificazione e sulla connessione a un'istanza [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] remota, così come il file di backup remoto utilizzato per ripristinare partizioni remote su quell'istanza remota.  
  
 Per i comandi `Synchronize`, l'elemento `Location` descrive un'origine dati che deve essere utilizzata dall'istanza di destinazione o un'istanza remota definita sull'istanza di origine che deve essere sincronizzata con l'istanza di destinazione, a seconda del valore dell'elemento `DataSourceType` per il comando `Synchronize` padre.  
  
 Per ulteriori informazioni sul backup e ripristino di istanze remote, vedere [backup e ripristino di oggetti (XMLA)](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento BackupRemotePartitions &#40;XMLA&#41;](backupremotepartitions-element-xmla.md)   
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  