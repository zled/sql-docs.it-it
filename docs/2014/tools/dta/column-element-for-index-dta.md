---
title: Elemento Column per Index (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Column element
ms.assetid: ba9fac20-26bd-4333-940e-842c15241b46
caps.latest.revision: 14
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: bfd0483abe0b5c5134f34361040cb46e033e6214
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37175007"
---
# <a name="column-element-for-index-dta"></a>Elemento Column per Index (DTA)
  Specifica le colonne sulle quali viene creato l'indice per una configurazione specificata dall'utente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
<Create>  
  <Index>  
    <Name>...</Name>  
    <Column [Type | SortOrder]>  
     ...code removed here...  
     </Column>  
```  
  
## <a name="element-attributes"></a>Attributi elemento  
  
|Attributo della colonna|Description|  
|----------------------|-----------------|  
|`Type`|Facoltativo. Specifica il tipo di colonna dell'indice. Usare un tipo di dati **string** per specificare questo attributo con uno dei valori consentiti seguenti:<br /><br /> `KeyColumn`:<br />                  Specifica che alla colonna viene fatto riferimento mediante una chiave di indice. Per impostare questo attributo, utilizzare la sintassi seguente:<br />`<Column Type="KeyColumn">`<br />Per altre informazioni sulle colonne chiave, vedere [Descrizione di indici cluster e non cluster](../../relational-databases/indexes/clustered-and-nonclustered-indexes-described.md).<br /><br /> `IncludedColumn`: Specifica che la colonna è una colonna inclusa (invece di una colonna chiave). Per impostare questo attributo, utilizzare la sintassi seguente:<br />`<Column Type="IncludedColumn">`<br />Per altre informazioni sulle colonne incluse, vedere [Creare indici con colonne incluse](../../relational-databases/indexes/create-indexes-with-included-columns.md).|  
|`SortOrder`|Facoltativo. Specifica l'ordinamento della colonna. Usare un tipo di dati **string** per specificare un ordinamento **"Ascending"** o **"Descending"** come segue:<br /><br /> `<Column SortOrder="Ascending">`|  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|**Tipo di dati e lunghezza**|Nessuna.|  
|**Valore predefinito**|Nessuna.|  
|**Occorrenza**|È possibile specificare un massimo di 1024 colonne per l'elemento `Index`.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elementi|  
|------------------|--------------|  
|**Elemento padre**|[Indice elemento &#40;DTA&#41;](index-element-dta.md)|  
|**Elementi figlio**|[Nome di elemento per la colonna &#40;DTA&#41;](name-element-for-column-dta.md)|  
  
## <a name="example"></a>Esempio  
 Per un esempio di utilizzo di questo elemento, vedere [Esempio di file di input XML con configurazione specificata dall'utente &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento ai file di input XML &#40;Ottimizzazione guidata motore di database&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
