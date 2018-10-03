---
title: Set di righe DMSCHEMA_MINING_MODEL_CONTENT_PMML | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DMSCHEMA_MINING_MODEL_CONTENT_PMML
topic_type:
- apiref
helpviewer_keywords:
- DMSCHEMA_MINING_MODEL_CONTENT_PMML rowset
ms.assetid: fa05bb08-a955-4c8d-b57f-ffcd82470220
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 23d900676f0a3abf0891a951712dca5d58f65fab
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48075341"
---
# <a name="dmschemaminingmodelcontentpmml-rowset"></a>Set di righe DMSCHEMA_MINING_MODEL_CONTENT_PMML
  Restituisce la struttura XML del modello di data mining. Il formato della stringa XML segue lo standard PMML 2.1 (Predictive Model Markup Language).  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il `DMSCHEMA_MINING_MODEL_CONTENT_PMML` set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Length|Description|  
|-----------------|--------------------|------------|-----------------|  
|`MODEL_CATALOG`|`DBTYPE_WSTR`||Nome del catalogo popolato con il nome del database di cui il modello è membro.|  
|`MODEL_SCHEMA`|`DBTYPE_WSTR`||Nome dello schema non qualificato. Questa colonna non è supportata da [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; contiene sempre `NULL`.|  
|`MODEL_NAME`|`DBTYPE_WSTR`||Nome del modello. Questa colonna non può contenere `NULL`.|  
|`MODEL_TYPE`|`DBTYPE_WSTR`||Tipo di modello. È una stringa specifica del provider. Può essere `NULL`.|  
|`MODEL_GUID`|`DBTYPE_GUID`||GUID che identifica il modello. I provider che non utilizzano GUID per identificare le tabelle restituiscono `NULL`.|  
|`MODEL_PMML`|`DBTYPE_WSTR`||Rappresentazione XML del contenuto del modello in formato PMML.|  
|`SIZE`|`DBTYPE_UI4`||Numero di byte nella stringa XML.|  
|`LOCATION`|`DBTYPE_WSTR`||Posizione del file XML. È `NULL` se non è disponibile alcuna posizione.|  
  
 Questo set di righe dello schema non è ordinato.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il set di righe `DMSCHEMA_MINING_MODEL_CONTENT_PMML` può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|`MODEL_CATALOG`|`DBTYPE_WSTR`|Facoltativo.|  
|`MODEL_SCHEMA`|`DBTYPE_WSTR`|Facoltativo.|  
|`MODEL_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`MODEL_TYPE`|`DBTYPE_WSTR`|Facoltativo.|  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello schema di data mining](../../schema-rowsets/data-mining/data-mining-schema-rowsets.md) 
  
  
