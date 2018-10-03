---
title: Bloccare l'elemento (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Lock Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Lock
- microsoft.xml.analysis.lock
- http://schemas.microsoft.com/analysisservices/2003/engine#Lock
helpviewer_keywords:
- Lock command
ms.assetid: a819e805-4793-43bb-8af3-16a19f8bdab3
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: aee5d603c2708cb42b666d3cc0c9acc5ea208f0b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48079521"
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
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Command](../xml-elements-properties/command-element-xmla.md)|  
|Elementi figlio|[ID](../xml-elements-properties/id-element-xmla.md), [modalità](../xml-elements-properties/mode-element-xmla.md), [oggetto](../xml-elements-properties/object-element-xmla.md)|  
  
## <a name="remarks"></a>Note  
 Il comando `Lock` blocca un oggetto, per utilizzo condiviso o esclusivo, all'interno del contesto della transazione attualmente attiva. Solo amministratori del database o amministratori del server possono eseguire in modo esplicito un comando `Lock`. Un blocco su un oggetto impedisce alle transazioni di eseguire il commit finché non viene rimosso. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] supporta due tipi di blocchi, blocchi condivisi e blocchi esclusivi. Per altre informazioni sui tipi di blocco supportati da [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], vedere [modalità elemento &#40;XMLA&#41;](../xml-elements-properties/mode-element-xmla.md).  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] consente solo che i database vengano bloccati. L'elemento `Object` deve contenere un riferimento all'oggetto a un database [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Se l'elemento `Object` non viene specificato oppure fa riferimento a un oggetto diverso da un database `Object`, si verifica un errore.  
  
 Gli altri comandi eseguono implicitamente un comando `Lock` su un database [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Qualsiasi operazione che legge dati o metadati da un database, ad esempio qualsiasi metodo `Discover` o un metodo `Execute` che esegue un comando `Statement`, esercita implicitamente un blocco condiviso sul database. Qualsiasi transazione che consolida le modifiche nei dati o metadati con un oggetto su un database [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], ad esempio un metodo `Execute` che esegue un comando `Alter`, implicitamente esercita un blocco esclusivo sul database.  
  
 Tutti i blocchi sono contenuti nel contesto della transazione corrente. Quando viene eseguito il commit oppure il rollback della transazione corrente, tutti i blocchi definiti all'interno della transazione vengono rilasciati automaticamente.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento Unlock &#40;XMLA&#41;](lock-element-xmla.md)   
 [I comandi &#40;XMLA&#41;](xml-elements-commands.md)  
  
  
