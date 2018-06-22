---
title: Elemento EventString (DTA) | Documenti Microsoft
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
- EventString element
ms.assetid: f76c37b4-2f6e-4274-8ee2-87e89d98e8a2
caps.latest.revision: 12
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 6155627f60694cf1a21d39893e40b106b9df0886
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36063012"
---
# <a name="eventstring-element-dta"></a>Elemento EventString (DTA)
  Specifica il carico di lavoro di uno script [!INCLUDE[tsql](../../includes/tsql-md.md)] direttamente nel file di input XML.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
<Workload>  
    <EventString Weight="...">  
    ...code removed here...  
    </EventString>  
</Workload>  
```  
  
## <a name="element-attributes"></a>Attributi elemento  
  
|attribute|Description|  
|---------------|-----------------|  
|`Weight`|Facoltativo. Specifica il fattore di ponderazione, o fattore di importanza, della query per l'evento specificato. Utilizzare un `float` tipo di dati per specificare il peso. Ad esempio, `Weight`="100.01". Il valore minimo che è possibile specificare per `Weight` è "0".|  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|**Tipo di dati e lunghezza**|`string`, lunghezza è illimitata.|  
|**Valore predefinito**|Nessuna.|  
|**Occorrenza**|Obbligatorio una sola volta se non viene specificato un altro tipo di carico di lavoro. È necessario specificare un `EventString`, una `File`, o una `Database` elemento figlio per il `Workload` padre, ma solo un tipo può essere utilizzato. Ad esempio, se si specifica un carico di lavoro con la `EventString` elemento, quindi è possibile specificare anche un carico di lavoro con il `File` elemento nello stesso file di input XML.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elementi|  
|------------------|--------------|  
|**Elemento padre**|[Elemento Workload &#40;DTA&#41;](workload-element-dta.md)|  
|**Elementi figlio**|Nessuna.|  
  
## <a name="example"></a>Esempio  
 Per un esempio di utilizzo di questo elemento, vedere [Esempio di file di input XML con carico di lavoro inline &#40;DTA&#41;](xml-input-file-sample-with-inline-workload-dta.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento ai file di input XML &#40;Ottimizzazione guidata motore di database&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  