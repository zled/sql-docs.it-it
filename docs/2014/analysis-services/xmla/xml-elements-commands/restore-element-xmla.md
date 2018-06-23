---
title: Elemento Restore (XMLA) | Documenti Microsoft
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
- Restore Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Restore
- urn:schemas-microsoft-com:xml-analysis#Restore
- microsoft.xml.analysis.restore
helpviewer_keywords:
- Restore command
ms.assetid: bb5a0c92-3927-4fa4-975b-6e4d79e0a912
caps.latest.revision: 26
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 0e8eca537c61be64de403b4ad08bb0e64040937c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36169506"
---
# <a name="restore-element-xmla"></a>Elemento Restore (XMLA)
  Ripristina una [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] database da un file di backup.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Command>  
   <Restore>  
      <DatabaseName>...</DatabaseName>  
      <DatabaseID>...</DatabaseID>  
      <File>...</File>  
      <Security>...</Security>  
      <AllowOverwrite>...</AllowOverwrite>  
      <Password>...</Password>  
      <Locations>...</Locations>  
      <DbStorageLocation>...</DbStorageLocation>  
   </Restore>  
</Command>  
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
|Elementi padre|[Command](../xml-elements-properties/command-element-xmla.md)|  
|Elementi figlio|[AllowOverwrite](../xml-elements-properties/allowoverwrite-element-xmla.md), [DatabaseName](../xml-elements-properties/name-element-xmla.md), [DatabaseID](../xml-elements-properties/id-element-xmla.md), [File](../xml-elements-properties/file-element-xmla.md), [percorsi](../xml-elements-properties/locations-element-xmla.md), [Password](../xml-elements-properties/password-element-xmla.md), [Protezione](../xml-elements-properties/security-element-xmla.md), [DbStorageLocation](../xml-elements-properties/dbstoragelocation-element.md)|  
  
## <a name="remarks"></a>Remarks  
 Il `Restore` comando ripristina un' [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] database specificato nella `DatabaseName` elemento da un file di backup e facoltativamente Ripristina le partizioni remote da file di backup remoti.  
  
 A seconda della modalità di archiviazione utilizzata da oggetti archiviati nel file di backup, il `Restore` comando Ripristina le informazioni come elencato nella tabella seguente.  
  
|Modalità di archiviazione|Informazioni|  
|------------------|-----------------|  
|OLAP multidimensionale (MOLAP)|Dati di origine, aggregazioni e metadati|  
|OLAP ibrido (HOLAP)|Aggregazioni e metadati|  
|OLAP relazionale (ROLAP)|Metadati|  
  
 Durante un `Restore` comando, viene inserito un blocco esclusivo nel [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] database indicato con il `DatabaseName` elemento. Il blocco viene rilasciato dopo il `Restore` comando è stato completato.  
  
 Per ulteriori informazioni sul backup e ripristino di database, vedere [backup, ripristino e sincronizzazione di database &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
> [!IMPORTANT]  
>  Per ogni file di backup, l'utente che esegue il comando di ripristino deve disporre delle autorizzazioni per leggere dal percorso di backup specificato per ogni file. Per ripristinare un database di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] non installato nel server, l'utente deve inoltre essere un membro del ruolo del server per l'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] specifica. Per sovrascrivere un database di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] , l'utente deve avere uno dei ruoli seguenti: deve essere un membro del ruolo del server per l'istanza [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] o un membro di un ruolo del database con autorizzazioni Controllo completo (amministratore) per il database da ripristinare.  
  
> [!NOTE]  
>  Dopo avere ripristinato un database esistente, l'utente che ha effettuato l'operazione potrebbe perdere l'accesso al database ripristinato. Può verificarsi questa perdita di accesso se, al momento dell’esecuzione del backup, l'utente non era un membro del ruolo del server o non era un membro del ruolo del database con autorizzazioni Controllo completo (amministratore).  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento di backup &#40;XMLA&#41;](backup-element-xmla.md)   
 [Elemento batch &#40;XMLA&#41;](batch-element-xmla.md)   
 [Parallela elemento &#40;XMLA&#41;](../xml-elements-properties/parallel-element-xmla.md)   
 [Elemento Synchronize &#40;XMLA&#41;](synchronize-element-xmla.md)   
 [I comandi &#40;XMLA&#41;](xml-elements-commands.md)  
  
  