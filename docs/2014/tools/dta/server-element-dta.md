---
title: Elemento Server (DTA) | Microsoft Docs
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
- Server element
ms.assetid: 9fe0bfb4-3aa6-4eb2-a83e-c0d0e7d4e9f6
caps.latest.revision: 16
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c152b69c2d19be43c833e2f6418225f233e46074
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37236041"
---
# <a name="server-element-dta"></a>Elemento Server (DTA)
  Contiene le informazioni di identificazione del server sul quale risiede il database che si desidera ottimizzare.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
<DTAInput>  
    <Server>  
    ...code removed here...  
    </Server>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|**Tipo di dati e lunghezza**|Nessuna.|  
|**Valore predefinito**|Nessuna.|  
|**Occorrenza**|Obbligatorio una sola volta per ogni `DTAInput` elemento.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elementi|  
|------------------|--------------|  
|**Elemento padre**|[Elemento DTAInput &#40;DTA&#41;](dtainput-element-dta.md)|  
|**Elementi figlio**|[Nome di elemento per il Server &#40;DTA&#41;](name-element-for-server-dta.md)<br /><br /> [Elemento database per Server &#40;DTA&#41;](database-element-for-server-dta.md)|  
  
## <a name="remarks"></a>Note  
 È possibile specificare una sola `Server` (elemento) per il `DTAInput` elemento. Questo elemento appartiene al nome **ServerDetailsTypecomplexType** nell'XML Schema di DTA. Non confondere questa `Server` con quello che è l'elemento figlio dell'elemento di `Configuration` elemento. Per altre informazioni, vedere [Elemento Server per Configuration &#40;DTA&#41;](server-element-for-configuration-dta.md).  
  
## <a name="example"></a>Esempio  
 L'esempio seguente mostra come specificare la tabella **Sales.SalesPerson** nel database **AdventureWorks** in SERVER001:  
  
```xml  
<Server>  
  <Name>SERVER001</Name>  
  <Database>  
    <Name>AdventureWorks</Name>  
    <Schema>  
      <Name>Sales</Name>  
      <Table>  
        <Name>SalesPerson</Name>  
      </Table>  
    </Schema>  
  </Database>  
</Server  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento ai file di input XML &#40;Ottimizzazione guidata motore di database&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
