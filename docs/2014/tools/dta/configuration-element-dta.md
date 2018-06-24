---
title: Elemento Configuration (DTA) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- XML
helpviewer_keywords:
- Configuration element
ms.assetid: 1478e56f-57c4-4441-bac9-1ac91453839b
caps.latest.revision: 16
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 6cca142282c59539d54d5e1d42d5d2269ac41635
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36062330"
---
# <a name="configuration-element-dta"></a>Elemento Configuration (DTA)
  Definisce una configurazione specificata dall'utente costituita da strutture di progettazione fisica esistenti e ipotetiche da analizzare in Ottimizzazione guidata motore di database durante l'ottimizzazione di un carico di lavoro.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
<DTAInput>  
    <Server>...</Server>  
    <Workload>...</Workload>  
    <TuningOptions>...</TuningOptions  
    <Configuration [SpecificationMode="Relative" | "Absolute"]>  
    ...code removed here...  
    </Configuration>  
</DTAInput>  
```  
  
## <a name="element-attributes"></a>Attributi elemento  
  
|Attributo di configurazione|Description|  
|-----------------------------|-----------------|  
|`SpecificationMode`|Facoltativo. Indica se Ottimizzazione guidata motore di database deve analizzare la configurazione specificata in relazione alla configurazione esistente corrente o come configurazione autonoma completamente nuova. Usare un tipo di dati **string** per specificare questo attributo con uno dei valori consentiti seguenti:<br /><br /> `Relative`: <br />                  Valuta la configurazione specificata in relazione alla configurazione esistente corrente delle strutture di progettazione fisica (indici, viste indicizzate, partizionamento) nel database sottoposto a ottimizzazione. Esempio: <br />`<Configuration SpecificationMode="Relative">`<br /><br /> `Absolute`: <br />                  Valuta la configurazione specificata come configurazione autonoma. Se viene specificato Absolute, Ottimizzazione guidata motore di database non prende in considerazione la configurazione esistente. Esempio:<br />`<Configuration SpecificationMode="Absolute">`|  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|**Tipo di dati e lunghezza**|Nessuna.|  
|**Valore predefinito**|Nessuna.|  
|**Occorrenza**|Facoltativo. Può utilizzare una sola volta per ogni `DTAInput` elemento.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elementi|  
|------------------|--------------|  
|**Elemento padre**|[Elemento DTAInput &#40;DTA&#41;](dtainput-element-dta.md)|  
|**Elementi figlio**|[Elemento server per la configurazione &#40;DTA&#41;](server-element-for-configuration-dta.md)|  
  
## <a name="example"></a>Esempio  
 Per un esempio di utilizzo di questo elemento, vedere [Esempio di file di input XML con configurazione specificata dall'utente &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento ai file di input XML &#40;Ottimizzazione guidata motore di database&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  