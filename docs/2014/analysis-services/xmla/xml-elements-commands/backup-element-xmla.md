---
title: Eseguire il backup elemento (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Backup Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Backup
- http://schemas.microsoft.com/analysisservices/2003/engine#Backup
- microsoft.xml.analysis.backup
helpviewer_keywords:
- Backup command
ms.assetid: 5bcbc14c-9db9-45b2-99de-f3a265bcb0c4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 59efda960de14ae96b0c7c948b66c89980d8f990
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48216507"
---
# <a name="backup-element-xmla"></a>Elemento Backup (XMLA)
  Esegue il backup di un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] database in un file di backup.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Command>  
   <Backup>  
      <Object>...</Object>  
      <File>...</File>  
      <Security>...</Security>  
      <ApplyCompression>...</ApplyCompression>  
      <AllowOverwrite>...</AllowOverwrite>  
      <Password>...</Password>  
      <BackupRemotePartitions>...</BackupRemotePartitions>  
      <Locations>...</Locations>  
   </Backup>  
</Command>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Command](../xml-elements-properties/command-element-xmla.md)|  
|Elementi figlio|[AllowOverwrite](../xml-elements-properties/allowoverwrite-element-xmla.md), [ApplyCompression](../xml-elements-properties/applycompression-element-xmla.md), [BackupRemotePartitions](../xml-elements-properties/backupremotepartitions-element-xmla.md), [File](../xml-elements-properties/file-element-xmla.md), [posizioni](../xml-elements-properties/locations-element-xmla.md), [ Oggetto](../xml-elements-properties/object-element-xmla.md), [Password](../xml-elements-properties/password-element-xmla.md), [sicurezza](../xml-elements-properties/security-element-xmla.md)|  
  
## <a name="remarks"></a>Note  
 Il `Backup` comando esegue il backup il [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] database indicato con il [oggetto](../xml-elements-properties/object-element-xmla.md) elemento in un file di backup e facoltativamente esegue il backup di partizioni remote nei file di backup remoto. Se l'elemento `Object` fa riferimento a un oggetto diverso da un database [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], si verifica un errore.  
  
 Le informazioni di `Backup` comando esegue il backup dipende dalla modalità di archiviazione utilizzata dagli oggetti nel database. Nella tabella seguente sono identificate le informazioni delle quali viene eseguito il backup in base alla modalità di archiviazione utilizzata.  
  
|Modalità di archiviazione|Informazioni delle quali viene eseguito il backup|  
|------------------|-----------------------------------|  
|OLAP multidimensionale (MOLAP)|Dati di origine, aggregazioni e metadati|  
|OLAP ibrido (HOLAP)|Aggregazioni e metadati|  
|OLAP relazionale (ROLAP)|Metadati|  
  
 Durante un `Backup` comando, viene inserito un blocco condiviso nel [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] database indicato con il `Object` elemento. Il blocco condiviso viene rilasciato dopo il `Backup` completamento del comando.  
  
 Più `Backup` comandi possono essere eseguiti in parallelo, se i comandi sono inclusi nel [parallele](../xml-elements-properties/parallel-element-xmla.md) raccolta di un [Batch](batch-element-xmla.md) comando. La raccolta `Parallel` consente il backup di un database in più file di backup contemporaneamente.  
  
 Per altre informazioni sul backup e ripristino di database, vedere [backup, ripristino e sincronizzazione di database &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
> [!IMPORTANT]  
>  Per ogni file di backup, l'utente che esegue il comando di backup deve disporre delle autorizzazioni per scrivere nel percorso di backup specificato per ogni file. Inoltre, l'utente deve avere uno dei ruoli seguenti: deve essere un membro di un ruolo del server per l'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] oppure un membro di un ruolo del database con autorizzazioni Controllo completo (amministratore) sul database di cui eseguire il backup.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento Restore &#40;XMLA&#41;](restore-element-xmla.md)   
 [Elemento Synchronize &#40;XMLA&#41;](synchronize-element-xmla.md)   
 [I comandi &#40;XMLA&#41;](xml-elements-commands.md)  
  
  
