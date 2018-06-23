---
title: Set di righe DMSCHEMA_MINING_MODEL_XML | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- DMSCHEMA_MINING_MODEL_XML
topic_type:
- apiref
helpviewer_keywords:
- DMSCHEMA_MINING_MODEL_XML rowset
ms.assetid: f58b00e9-3f72-4cff-b448-21a9fb529772
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 37bfb0f304e8204f28f83589a6c16625c178444c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36156581"
---
# <a name="dmschemaminingmodelxml-rowset"></a>Set di righe DMSCHEMA_MINING_MODEL_XML
  Restituisce la struttura XML del modello di data mining. Il formato della stringa XML segue lo standard PMML 2.1 (Predictive Model Markup Language).  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il `DMSCHEMA_MINING_MODEL_XML` set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Length|Description|  
|-----------------|--------------------|------------|-----------------|  
|`MODEL_CATALOG`|`DBTYPE_WSTR`||Nome del catalogo. Popolato con il nome del database di cui il modello è membro.|  
|`MODEL_SCHEMA`|`DBTYPE_WSTR`||Nome dello schema non qualificato. Questa colonna non è supportata da [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; contiene sempre `NULL`.|  
|`MODEL_NAME`|`DBTYPE_WSTR`||Nome del modello. Questa colonna non può contenere `NULL`.|  
|`MODEL_TYPE`|`DBTYPE_WSTR`||Tipo di modello. È una stringa specifica del provider. Può essere `NULL`.|  
|`MODEL_GUID`|`DBTYPE_GUID`||GUID che identifica il modello. I provider che non utilizzano GUID per identificare le tabelle restituiscono `NULL`.|  
|`MODEL_PMML`|`DBTYPE_WSTR`||Rappresentazione XML del contenuto del modello in formato PMML.|  
|`SIZE`|`DBTYPE_UI4`||Numero di byte nella stringa XML.|  
|`LOCATION`|`DBTYPE_WSTR`||Posizione del file XML. È `NULL` se non viene utilizzato un file fisico per l'archiviazione.|  
  
 Questo set di righe dello schema non è ordinato.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il set di righe DMSCHEMA_MINING_MODEL_XML può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|`MODEL_CATALOG`|`DBTYPE_W`STR|Facoltativo.|  
|`MODEL_SCHEMA`|`DBTYPE_WSTR`|Facoltativo.|  
|`MODEL_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`MODEL_TYPE`|`DBTYPE_WSTR`|Facoltativo.|  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello schema di data mining](../../schema-rowsets/data-mining/data-mining-schema-rowsets.md) 
  
  