---
title: Elemento database per Workload (DTA) | Documenti Microsoft
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
- Database element
ms.assetid: 112fca2a-37e5-4162-b2e7-b56eb8ab0c6f
caps.latest.revision: 12
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 6380708319286a984ef54ef3820fab22821047bf
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36065013"
---
# <a name="database-element-for-workload-dta"></a>Elemento Database per Workload (DTA)
  Specifica il database in cui è contenuta la tabella di traccia del carico di lavoro.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
<Workload>  
  <Database>  
   ...code removed here...  
  </Database>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|**Tipo di dati e lunghezza**|Nessuna.|  
|**Valore predefinito**|Nessuna.|  
|**Occorrenza**|Obbligatorio una sola volta se non viene specificato un altro tipo di carico di lavoro. È necessario specificare un `EventString`, una `File`, o una `Database` elemento figlio per il `Workload` padre, ma solo un tipo può essere utilizzato. Se ad esempio si specifica un carico di lavoro con l'elemento `Database`, non sarà possibile specificare anche un carico di lavoro con l'elemento `File` nello stesso file di input XML.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elementi|  
|------------------|--------------|  
|**Elemento padre**|[Elemento Workload &#40;DTA&#41;](workload-element-dta.md)|  
|**Elementi figlio**|[Nome di elemento per il Database &#40;DTA&#41;](name-element-for-database-dta.md)<br /><br /> [Elemento schema per il Database &#40;DTA&#41;](schema-element-for-database-dta.md)|  
  
## <a name="remarks"></a>Remarks  
 Questo elemento appartiene al nome **DatabaseDetailsTypecomplexType** nell'XML Schema di Ottimizzazione guidata motore di database. Questo elemento `Database` non deve essere confuso con quello il cui padre radice è l'elemento `Configuration`. Vedere [Elemento Database per Configuration &#40;DTA&#41;](database-element-for-configuration-dta.md).  
  
## <a name="example"></a>Esempio  
 Per un esempio di utilizzo di questo `Database` elemento, vedere l'esempio di codice [Workload-elemento &#40;DTA&#41;](workload-element-dta.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento ai file di input XML &#40;Ottimizzazione guidata motore di database&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  