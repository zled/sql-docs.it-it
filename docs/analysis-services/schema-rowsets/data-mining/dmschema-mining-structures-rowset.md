---
title: Set di righe DMSCHEMA_MINING_STRUCTURES | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- DMSCHEMA_MINING_STRUCTURES
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DMSCHEMA_MINING_STRUCTURES rowset
ms.assetid: 6224556b-08a0-496e-bd7c-632c3e833e26
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c648aeb0603661e249f205e43cfbb1d8c6dc125c
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="dmschemaminingstructures-rowset"></a>Set di righe DMSCHEMA_MINING_STRUCTURES
  Enumera informazioni sulle strutture di data mining nel catalogo corrente.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il **DMSCHEMA_MINING_STRUCTURES** set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Lunghezza|Description|  
|-----------------|--------------------|------------|-----------------|  
|**STRUCTURE_CATALOG**|**DBTYPE_WSTR**||Nome del catalogo.|  
|**STRUCTURE_SCHEMA**|**DBTYPE_WSTR**||Nome dello schema non qualificato. **NULL** se gli schemi non sono supportati dal provider.|  
|**NOME_STRUTTURA**|**DBTYPE_WSTR**||Nome della struttura. Questa colonna non può contenere **NULL**.|  
|**STRUCTURE_GUID**|**DBTYPE_GUID**||GUID che identifica la struttura in modo univoco. **NULL** se non è supportato dal provider.|  
|**DESCRIPTION**|**DBTYPE_WSTR**||Una descrizione breve della struttura. **NULL** se non è associata alla struttura alcuna descrizione.|  
|**STRUCTURE_PROPID**|**DBTYPE_UI4**||ID di proprietà della struttura. **NULL** se non è supportato dal provider.|  
|**DATE_CREATED**|**DBTYPE_DBTIMESTAMP**||Data di creazione della struttura. **NULL** se non è disponibile dal provider.|  
|**DATE_MODIFIED**|**DBTYPE_DBTIMESTAMP**||Data dell'ultima modifica della struttura. **NULL** se non è disponibile dal provider.|  
|**CREATION_STATEMENT**|**DBTYPE_WSTR**||(Facoltativo) Istruzione utilizzata per creare il modello di data mining originale.|  
|**IS_POPULATED**|**DBTYPE_BOOL**||Valore booleano che indica se la struttura è popolata.<br /><br /> **VARIANT_TRUE** se la struttura viene popolata; **VARIANT_FALSE** in caso contrario.|  
|**LAST_PROCESSED**|**DBTYPE_DBTIMESTAMP**||Data dell'ultima elaborazione della struttura. **NULL** se non è disponibile dal provider.|  
|**HOLDOUT_MAXPERCENT**|**DBTYPE UI1**||Valore specificato dall'utente che indica la percentuale massima di case di input riservata come set di test.<br /><br /> 0 o **NULL** indica nessun limite.|  
|**HOLDOUT_MAXCASES**|**DBTYPE_UI8**||Valore specificato dall'utente che indica il numero massimo di case di input riservati come set di test.<br /><br /> 0 o **NULL** indica nessun limite.|  
|**HOLDOUT_SEED**|**DBTYPE_UI8**||Valore specificato dall'utente utilizzato come valore di inizializzazione per il partizionamento ripetibile.<br /><br /> 0 indica che come valore di inizializzazione viene utilizzato un hash dell'ID della struttura di data mining.|  
|**HOLDOUT_ACTUAL_SIZE**|**DBTYPE_UI8**||Se la struttura di data mining viene elaborata, indica la dimensione effettiva del set di dati di test, espressa in numero di case.<br /><br /> **NULL** indica che la struttura di data mining non è elaborata.|  
  
 Il set di righe viene ordinato in base **STRUCTURE_CATALOG**, **STRUCTURE_SCHEMA**, **nome_struttura**.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il **DMSCHEMA_MINING_STRUCTURES** righe può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|**STRUCTURE_CATALOG**|**DBTYPE_WSTR**|Facoltativa.|  
|**STRUCTURE_SCHEMA**|**DBTYPE_WSTR**|Facoltativa.|  
|**NOME_STRUTTURA**|**DBTYPE_WSTR**|Facoltativa.|  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello Schema di Data Mining](../../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)  
  
  

