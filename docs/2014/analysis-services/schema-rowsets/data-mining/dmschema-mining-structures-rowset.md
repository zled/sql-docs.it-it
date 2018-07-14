---
title: Set di righe DMSCHEMA_MINING_STRUCTURES | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- DMSCHEMA_MINING_STRUCTURES
topic_type:
- apiref
helpviewer_keywords:
- DMSCHEMA_MINING_STRUCTURES rowset
ms.assetid: 6224556b-08a0-496e-bd7c-632c3e833e26
caps.latest.revision: 36
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ab600b39e4a8347e470153cf21510554605d1c71
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37323071"
---
# <a name="dmschemaminingstructures-rowset"></a>Set di righe DMSCHEMA_MINING_STRUCTURES
  Enumera informazioni sulle strutture di data mining nel catalogo corrente.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il `DMSCHEMA_MINING_STRUCTURES` set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Length|Description|  
|-----------------|--------------------|------------|-----------------|  
|`STRUCTURE_CATALOG`|`DBTYPE_WSTR`||Nome del catalogo.|  
|`STRUCTURE_SCHEMA`|`DBTYPE_WSTR`||Nome dello schema non qualificato. `NULL` se gli schemi non sono supportati dal provider.|  
|`STRUCTURE_NAME`|`DBTYPE_WSTR`||Nome della struttura. Questa colonna non può contenere `NULL`.|  
|`STRUCTURE_GUID`|`DBTYPE_GUID`||GUID che identifica la struttura in modo univoco. `NULL` se non sono supportati dal provider.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Una descrizione breve della struttura. `NULL` se non è associata alcuna descrizione alla struttura.|  
|`STRUCTURE_PROPID`|`DBTYPE_UI4`||ID di proprietà della struttura. `NULL` se non sono supportati dal provider.|  
|`DATE_CREATED`|`DBTYPE_DBTIMESTAMP`||Data di creazione della struttura. `NULL` se non è disponibile dal provider.|  
|`DATE_MODIFIED`|`DBTYPE_DBTIMESTAMP`||Data dell'ultima modifica della struttura. `NULL` se non è disponibile dal provider.|  
|`CREATION_STATEMENT`|`DBTYPE_WSTR`||(Facoltativo) Istruzione utilizzata per creare il modello di data mining originale.|  
|`IS_POPULATED`|`DBTYPE_BOOL`||Valore booleano che indica se la struttura è popolata.<br /><br /> È `VARIANT_TRUE` se la struttura è popolata. In caso contrario è `VARIANT_FALSE`.|  
|`LAST_PROCESSED`|`DBTYPE_DBTIMESTAMP`||Data dell'ultima elaborazione della struttura. `NULL` se non è disponibile dal provider.|  
|`HOLDOUT_MAXPERCENT`|`DBTYPE_ UI1`||Valore specificato dall'utente che indica la percentuale massima di case di input riservata come set di test.<br /><br /> 0 o `NULL` indica che non vi sono limiti.|  
|`HOLDOUT_MAXCASES`|`DBTYPE_UI8`||Valore specificato dall'utente che indica il numero massimo di case di input riservati come set di test.<br /><br /> 0 o `NULL` indica che non vi sono limiti.|  
|`HOLDOUT_SEED`|`DBTYPE_UI8`||Valore specificato dall'utente utilizzato come valore di inizializzazione per il partizionamento ripetibile.<br /><br /> 0 indica che come valore di inizializzazione viene utilizzato un hash dell'ID della struttura di data mining.|  
|`HOLDOUT_ACTUAL_SIZE`|`DBTYPE_UI8`||Se la struttura di data mining viene elaborata, indica la dimensione effettiva del set di dati di test, espressa in numero di case.<br /><br /> `NULL` indica che la struttura di data mining non viene elaborata.|  
  
 Il set di righe viene ordinato in base a `STRUCTURE_CATALOG`, `STRUCTURE_SCHEMA`, `STRUCTURE_NAME`.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il set di righe `DMSCHEMA_MINING_STRUCTURES` può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|`STRUCTURE_CATALOG`|`DBTYPE_WSTR`|Facoltativo.|  
|`STRUCTURE_SCHEMA`|`DBTYPE_WSTR`|Facoltativo.|  
|`STRUCTURE_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello schema di data mining](../../schema-rowsets/data-mining/data-mining-schema-rowsets.md) 
  
  
