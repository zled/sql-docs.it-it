---
title: Set di righe DMSCHEMA_MINING_MODEL_XML | Documenti Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: aa57b1bed12f11bca349630e539510b162700cc1
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="dmschemaminingmodelxml-rowset"></a>Set di righe DMSCHEMA_MINING_MODEL_XML
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Restituisce la struttura XML del modello di data mining. Il formato della stringa XML segue lo standard PMML 2.1 (Predictive Model Markup Language).  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il **DMSCHEMA_MINING_MODEL_XML** set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Lunghezza|Description|  
|-----------------|--------------------|------------|-----------------|  
|**MODEL_CATALOG**|**DBTYPE_WSTR**||Nome del catalogo. Popolato con il nome del database di cui il modello è membro.|  
|**MODEL_SCHEMA**|**DBTYPE_WSTR**||Nome dello schema non qualificato. Questa colonna non è supportata da [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]; contiene sempre **NULL**.|  
|**MODEL_NAME**|**DBTYPE_WSTR**||Nome del modello. Questa colonna non può contenere **NULL**.|  
|**MODEL_TYPE**|**DBTYPE_WSTR**||Tipo di modello. È una stringa specifica del provider. Può essere **NULL**.|  
|**MODEL_GUID**|**DBTYPE_GUID**||GUID che identifica il modello. I provider che non utilizzano GUID per identificare le tabelle restituiscono **NULL**.|  
|**MODEL_PMML**|**DBTYPE_WSTR**||Rappresentazione XML del contenuto del modello in formato PMML.|  
|**SIZE**|**DBTYPE_UI4**||Numero di byte nella stringa XML.|  
|**PERCORSO**|**DBTYPE_WSTR**||Posizione del file XML. È **NULL** se un file fisico non viene utilizzato per l'archiviazione.|  
  
 Questo set di righe dello schema non è ordinato.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il set di righe DMSCHEMA_MINING_MODEL_XML può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|**MODEL_CATALOG**|**DBTYPE_W**STR|Facoltativa.|  
|**MODEL_SCHEMA**|**DBTYPE_WSTR**|Facoltativa.|  
|**MODEL_NAME**|**DBTYPE_WSTR**|Facoltativa.|  
|**MODEL_TYPE**|**DBTYPE_WSTR**|Facoltativa.|  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello Schema di Data Mining](../../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)  
  
  
