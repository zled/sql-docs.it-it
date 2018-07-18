---
title: File di elemento (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: eb80a091c9b9585a6efc29088d15139db7033efb
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "37969999"
---
# <a name="file-element-xmla"></a>Elemento File (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Identifica un file da utilizzare dall'elemento padre [Backup](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md) oppure [ripristinare](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md) comando o dall'elemento padre [percorso](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Backup> <!-- or one of the elements listed below in the Element relationships table -->  
   ...  
   <File>...</File>  
   ...  
</Backup>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche di elementi  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|None|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Elementi-relazioni  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Copia di backup](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md), [posizione](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md), [ripristinare](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Il **File** elemento contiene un nome file UNC e l'elemento padre determina l'uso delle **File** elemento.  
  
 Per la **Backup** comandi, il **File** elemento determina il nome del file di backup creato dal **Backup** comando. Se un percorso non è specificato come parte del nome file, il percorso specificato nella **BackupDir** proprietà di configurazione per l'istanza di Analysis Services viene utilizzata. Se il file specificato esiste già, si verifica un errore, a meno che il **AllowOverwrite** dell'elemento padre **Backup** command è impostato su **True**.  
  
 Per **ripristinare** comandi, il **File** elemento determina il nome del file di backup da ripristinare tramite il **Restore** comando.  
  
 Per **posizione** gli elementi, il **File** elemento descrive un file di backup remoto per un [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza contenente le partizioni remote. Per altre informazioni sul backup e ripristino di partizioni remote, vedere [backup, ripristino e sincronizzazione di database &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Vedere anche
 [Elemento AllowOverwrite &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/allowoverwrite-element-xmla.md)   
 [Proprietà &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
