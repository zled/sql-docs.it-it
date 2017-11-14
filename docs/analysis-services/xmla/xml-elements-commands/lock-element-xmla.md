---
title: Bloccare l'elemento (XMLA) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: xmla
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Lock Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Lock
- microsoft.xml.analysis.lock
- http://schemas.microsoft.com/analysisservices/2003/engine#Lock
helpviewer_keywords:
- Lock command
ms.assetid: a819e805-4793-43bb-8af3-16a19f8bdab3
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: df377150443acf63e4f67cd4f8f4952f36277a32
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="lock-element-xmla"></a>Elemento Lock (XMLA)
  Blocca un oggetto specificato in un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Command>  
   <Lock>  
      <ID>...</ID>  
      <Object>...</Object>  
      <Mode>...</Mode>  
   </Lock>  
</Command>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Elementi figlio|[ID](../../../analysis-services/xmla/xml-elements-properties/id-element-xmla.md), [modalità](../../../analysis-services/xmla/xml-elements-properties/mode-element-xmla.md), [oggetto](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)|  
  
## <a name="remarks"></a>Osservazioni  
 Il **blocco** comando Blocca un oggetto, per utilizzo condiviso o esclusivo, all'interno del contesto della transazione attualmente attiva. Solo gli amministratori di database o gli amministratori del server possono eseguire in modo esplicito un **blocco** comando. Un blocco su un oggetto impedisce alle transazioni di eseguire il commit finché non viene rimosso. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] supporta due tipi di blocchi, blocchi condivisi e blocchi esclusivi. Per ulteriori informazioni sui tipi di blocco supportati da [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], vedere [elemento Mode &#40; XMLA &#41; ](../../../analysis-services/xmla/xml-elements-properties/mode-element-xmla.md).  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] consente solo che i database vengano bloccati. Il **oggetto** elemento deve contenere un riferimento a un [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] database. Se il **oggetto** elemento non è specificato o se il **oggetto** elemento fa riferimento a un oggetto diverso da un database, si verifica un errore.  
  
 Altri comandi eseguono implicitamente un **blocco** comando un [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] database. Qualsiasi operazione che legge dati o metadati da un database, ad esempio **Discover** metodo o un **Execute** metodo in esecuzione un **istruzione** comando, applica implicitamente un oggetto condiviso blocco del database. Qualsiasi transazione che esegue il commit delle modifiche nei dati o metadati per un oggetto su un [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] database, ad esempio un **Execute** metodo in esecuzione un **Alter** comando, applica implicitamente un blocco esclusivo sul database.  
  
 Tutti i blocchi sono contenuti nel contesto della transazione corrente. Quando viene eseguito il commit oppure il rollback della transazione corrente, tutti i blocchi definiti all'interno della transazione vengono rilasciati automaticamente.  
  
## <a name="see-also"></a>Vedere anche  
 [Sblocca elemento &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/unlock-element-xmla.md)   
 [Comandi &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  

