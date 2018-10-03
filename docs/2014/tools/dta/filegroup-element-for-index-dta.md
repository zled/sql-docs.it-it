---
title: Elemento filegroup per Index (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Filegroup element [DTA]
ms.assetid: 7078d2fb-fa77-44fc-beb3-c095088fcb85
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 71de5e0e883961af7737ba0aec5495fa59d2b453
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48196611"
---
# <a name="filegroup-element-for-index-dta"></a>Elemento Filegroup per Index (DTA)
  Specifica il filegroup in cui creare l'indice per una configurazione specificata dall'utente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
<Index>  
  <Name>...</Name>  
  <Column>  
    <Name>...</Name>  
  <Filegroup>...</Filegroup>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|**Tipo di dati e lunghezza**|`string`, lunghezza illimitata.|  
|**Valore predefinito**|Nessuno|  
|**Occorrenza**|Facoltativa. Può usare una sola volta per ogni `Index` elemento. Questo elemento non può essere usato se la `PartitionScheme` e `PartitionColumn` gli elementi vengono specificati per il `Index` elemento.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elementi|  
|------------------|--------------|  
|**Elemento padre**|[Indice elemento &#40;DTA&#41;](index-element-dta.md)|  
|**Elementi figlio**|Nessuno|  
  
## <a name="example"></a>Esempio  
 Per un esempio di utilizzo di questo elemento, vedere [Esempio di file di input XML con configurazione specificata dall'utente &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento ai file di input XML &#40;Ottimizzazione guidata motore di database&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
