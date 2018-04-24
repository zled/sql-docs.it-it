---
title: ADCPROP_AUTORECALC_ENUM | Documenti Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADCPROP_AUTORECALC_ENUM
helpviewer_keywords:
- ADCPROP_AUTORECALC_ENUM [ADO]
ms.assetid: ded4f087-87b9-4efa-8026-bde53d3e9e8a
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5cac0bdaf0980913cbbcbde4147bafece3de8a0a
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="adcpropautorecalcenum"></a>ADCPROP_AUTORECALC_ENUM
Specifica quando il [MSDataShape](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) provider nuovamente Calcola l'aggregazione e le colonne calcolate in un Recordset gerarchico.  
  
 Queste costanti vengono utilizzate solo con il **MSDataShape** provider e **Recordset** "**ricalcolo automatico**" proprietà dinamica, che fa riferimento il [ADO Indice delle proprietà dinamiche](../../../ado/reference/ado-api/ado-dynamic-property-index.md) e documentate nel [servizio cursore per OLE DB](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) o [Microsoft Data shaping per OLE DB](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) documentazione.  
  
|Costante|Value|Description|  
|--------------|-----------|-----------------|  
|**adRecalcAlways**|1|Valore predefinito. Ricalcola ogni volta che il **MSDataShape** provider determina i valori modificati da cui dipendono le colonne calcolate.|  
|**adRecalcUpFront**|0|Viene calcolata solo quando viene creato inizialmente la gerarchica **Recordset**.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Queste costanti non dispongono di equivalenti ADO/WFC.
