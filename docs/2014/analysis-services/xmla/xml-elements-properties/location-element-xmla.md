---
title: Elemento location (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a0277ab50eb7390d3272c309df8dc865ff088c89
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48107612"
---
# <a name="location-element-xmla"></a>Elemento Location (XMLA)
  Contiene informazioni su un server remoto per l'elemento padre [Backup](../xml-elements-commands/backup-element-xmla.md), [ripristinare](../xml-elements-commands/restore-element-xmla.md), o [Sincronizza](../xml-elements-commands/synchronize-element-xmla.md) comando.  
  
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
|Elementi padre|[Copia di backup](../xml-elements-commands/backup-element-xmla.md), [ripristinare](../xml-elements-commands/restore-element-xmla.md), [sincronizzare](../xml-elements-commands/synchronize-element-xmla.md)|  
  
## <a name="child-elements"></a>Elementi figlio  
  
|Predecessore o padre|Elemento figlio|  
|------------------------|-------------------|  
|[Copia di backup](id-element-xmla.md), [File](file-element-xmla.md)|  
|[Ripristinare](connectionstring-element-xmla.md), [DataSourceID](datasourceid-element-xmla.md), [DataSourceType](type-element-xmla.md), [File](file-element-xmla.md), [cartelle](folders-element-xmla.md)|  
|[Sincronizza](../xml-elements-commands/synchronize-element-xmla.md)|[ConnectionString](connectionstring-element-xmla.md), [DataSourceID](datasourceid-element-xmla.md), [DataSourceType](type-element-xmla.md), [cartelle](folders-element-xmla.md)|  
  
## <a name="remarks"></a>Note  
 Per la `Backup` comandi, le `Location` elemento fornisce informazioni sulla creazione di un file di backup remoto per un'istanza remota di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 Per i comandi `Restore`, l'elemento `Location` fornisce informazioni sull'identificazione e sulla connessione a un'istanza [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] remota, così come il file di backup remoto utilizzato per ripristinare partizioni remote su quell'istanza remota.  
  
 Per i comandi `Synchronize`, l'elemento `Location` descrive un'origine dati che deve essere utilizzata dall'istanza di destinazione o un'istanza remota definita sull'istanza di origine che deve essere sincronizzata con l'istanza di destinazione, a seconda del valore dell'elemento `DataSourceType` per il comando `Synchronize` padre.  
  
 Per altre informazioni sul backup e ripristino di istanze remote, vedere [backup e ripristino di oggetti (XMLA)](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento BackupRemotePartitions &#40;XMLA&#41;](backupremotepartitions-element-xmla.md)   
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
