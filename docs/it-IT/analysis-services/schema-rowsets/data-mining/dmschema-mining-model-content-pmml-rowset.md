---
title: Set di righe DMSCHEMA_MINING_MODEL_CONTENT_PMML | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DMSCHEMA_MINING_MODEL_CONTENT_PMML
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DMSCHEMA_MINING_MODEL_CONTENT_PMML rowset
ms.assetid: fa05bb08-a955-4c8d-b57f-ffcd82470220
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 153624dce91c2b94707170e94c9da3c497da02e6
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="dmschemaminingmodelcontentpmml-rowset"></a>Set di righe DMSCHEMA_MINING_MODEL_CONTENT_PMML
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Restituisce la struttura XML del modello di data mining. Il formato della stringa XML segue lo standard PMML 2.1 (Predictive Model Markup Language).  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il **DMSCHEMA_MINING_MODEL_CONTENT_PMML** set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Lunghezza|Description|  
|-----------------|--------------------|------------|-----------------|  
|**MODEL_CATALOG**|**DBTYPE_WSTR**||Nome del catalogo popolato con il nome del database di cui il modello è membro.|  
|**MODEL_SCHEMA**|**DBTYPE_WSTR**||Nome dello schema non qualificato. Questa colonna non è supportata da [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; contiene sempre **NULL**.|  
|**MODEL_NAME**|**DBTYPE_WSTR**||Nome del modello. Questa colonna non può contenere **NULL**.|  
|**MODEL_TYPE**|**DBTYPE_WSTR**||Tipo di modello. È una stringa specifica del provider. Può essere **NULL**.|  
|**MODEL_GUID**|**DBTYPE_GUID**||GUID che identifica il modello. I provider che non utilizzano GUID per identificare le tabelle restituiscono **NULL**.|  
|**MODEL_PMML**|**DBTYPE_WSTR**||Rappresentazione XML del contenuto del modello in formato PMML.|  
|**SIZE**|**DBTYPE_UI4**||Numero di byte nella stringa XML.|  
|**PERCORSO**|**DBTYPE_WSTR**||Posizione del file XML. È **NULL** se è disponibile alcuna posizione.|  
  
 Questo set di righe dello schema non è ordinato.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il **DMSCHEMA_MINING_MODEL_CONTENT_PMML** righe può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|**MODEL_CATALOG**|**DBTYPE_WSTR**|Facoltativa.|  
|**MODEL_SCHEMA**|**DBTYPE_WSTR**|Facoltativa.|  
|**MODEL_NAME**|**DBTYPE_WSTR**|Facoltativa.|  
|**MODEL_TYPE**|**DBTYPE_WSTR**|Facoltativa.|  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello Schema di Data Mining](../../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)  
  
  
