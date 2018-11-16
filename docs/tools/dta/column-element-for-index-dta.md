---
title: Elemento Column per Index (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Column element
ms.assetid: ba9fac20-26bd-4333-940e-842c15241b46
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 77972892b2efcac8554f79ea9c41720f9ae40277
ms.sourcegitcommit: 0f7cf9b7ab23df15624d27c129ab3a539e8b6457
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2018
ms.locfileid: "51290817"
---
# <a name="column-element-for-index-dta"></a>Elemento Column per Index (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
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
  
 **Type**: facoltativo. Specifica il tipo di colonna dell'indice. Usare un tipo di dati **string** per specificare questo attributo con uno dei valori consentiti seguenti:  
  
-   **KeyColumn**  
  
     Specifica che alla colonna viene fatto riferimento mediante una chiave di indice. Per impostare questo attributo, utilizzare la sintassi seguente:  
  
    ```  
    <Column Type="KeyColumn">  
    ```  
  
     Per altre informazioni sulle colonne chiave, vedere [Descrizione di indici cluster e non cluster](../../relational-databases/indexes/clustered-and-nonclustered-indexes-described.md).  
  
-   **IncludedColumn**  
  
     Specifica che la colonna è una colonna inclusa, anziché una colonna chiave. Per impostare questo attributo, utilizzare la sintassi seguente:  
  
    ```  
    <Column Type="IncludedColumn">  
    ```  
  
     Per altre informazioni sulle colonne incluse, vedere [Creare indici con colonne incluse](../../relational-databases/indexes/create-indexes-with-included-columns.md).  
  
 **SortOrder**: facoltativo. Specifica l'ordinamento della colonna. Usare un tipo di dati **string** per specificare un ordinamento **"Ascending"** o **"Descending"** come segue:  
  
```  
<Column SortOrder="Ascending">  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|**Tipo di dati e lunghezza**|Nessuna.|  
|**Valore predefinito**|Nessuna.|  
|**Occorrenza**|È possibile specificare un massimo di 1024 colonne per l'elemento **Index** .|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elementi|  
|------------------|--------------|  
|**Elemento padre**|[Elemento Index &#40;DTA&#41;](../../tools/dta/index-element-dta.md)|  
|**Elementi figlio**|[Elemento Name per Column &#40;DTA&#41;](../../tools/dta/name-element-for-column-dta.md)|  
  
## <a name="example"></a>Esempio  
 Per un esempio di utilizzo di questo elemento, vedere [Esempio di file di input XML con configurazione specificata dall'utente &#40;DTA&#41;](../../tools/dta/xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento ai file di input XML&#40; (Ottimizzazione guidata motore di database)&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
