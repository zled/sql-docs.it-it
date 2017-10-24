---
title: Set di righe DBSCHEMA_PROVIDER_TYPES | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- DBSCHEMA_PROVIDER_TYPES
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DBSCHEMA_PROVIDER_TYPES rowset
ms.assetid: 255e01ba-53a9-478d-9b86-45faba76710e
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 6906aec1d1c1dd53b8c833d59483aa0453cf284b
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="dbschemaprovidertypes-rowset"></a>Set di righe DBSCHEMA_PROVIDER_TYPES
  Identifica i tipi di dati (di base) supportati dal provider di dati.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il **DBSCHEMA_PROVIDER_TYPES** set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Description|  
|-----------------|--------------------|-----------------|  
|**TYPE_NAME**|**DBTYPE_WSTR**|Nome del tipo di dati specifico del provider.|  
|**DATA_TYPE**|**DBTYPE_UI2**|Indicatore del tipo di dati.|  
|**COLUMN_SIZE**|**DBTYPE_UI4**|Lunghezza di una colonna o un parametro non numerico che fa riferimento alla lunghezza massima o alla lunghezza definita per questo tipo dal provider. Per i dati di tipo carattere, si tratta della lunghezza massima o definita in caratteri. Per i tipi di dati DateTime, si tratta della lunghezza della rappresentazione di stringa (presupponendo la precisione massima consentita del componente delle frazioni di secondo).<br /><br /> Se il tipo di dati è numerico, si tratta del limite superiore rispetto alla precisione massima del tipo di dati.|  
|**:: SQLGETTYPEINFO**|**DBTYPE_WSTR**|Carattere o caratteri utilizzati per aggiungere come prefisso un valore letterale di questo tipo in un comando di testo.|  
|**SQL_VARCHAR**|**DBTYPE_WSTR**|Carattere o caratteri utilizzati per aggiungere come suffisso un valore letterale di questo tipo in un comando di testo.|  
|**CREATE_PARAMS**|**DBTYPE_WSTR**|Parametri di creazione specificati dal consumer al momento della creazione di una colonna di questo tipo di dati. Ad esempio, il tipo di dati SQL **decimale,** necessarie una precisione e scala. In questo caso, i parametri di creazione potrebbero essere costituiti dalla stringa "precision,scale". In un comando di testo per creare un **decimale** colonna con una precisione pari a 10 e una scala di 2, il valore di **TYPE_NAME** colonna potrebbe essere **DECIMAL()** e il tipo completo Specifica sarebbe **10,2**.<br /><br /> I parametri di creazione sono visualizzati come un elenco di valori delimitato da virgole, nell'ordine in cui devono essere forniti e senza essere racchiusi tra parentesi. Se un parametro di creazione è lunghezza, lunghezza massima, precisione, scala, valore di inizializzazione o incremento, utilizzare rispettivamente "lunghezza", "lunghezza massima", "precisione", "scala", "valore di inizializzazione" e "incremento". Se il parametro di creazione è un altro valore, il provider determina il testo da utilizzare per descrivere il parametro di creazione.<br /><br /> Se il tipo di dati richiede parametri di creazione, nel nome del tipo vengono generalmente visualizzati i caratteri "()", che indicano la posizione in cui inserire i parametri di creazione. Se il nome del tipo non include "()", i parametri di creazione vengono racchiusi tra parentesi e aggiunti al nome del tipo di dati.|  
|**IS_NULLABLE**|**DBTYPE_BOOL**|Valore booleano che indica se il tipo di dati ammette valori Null.<br /><br /> **VARIANT_TRUE** indica che il tipo di dati ammette valori null.<br /><br /> **VARIANT_FALSE** indica che il tipo di dati non ammette valori null.<br /><br /> **NULL**: indica che non è noto se il tipo di dati è nullable.|  
|**CASE_SENSITIVE**|**DBTYPE_BOOL**|Valore booleano che indica che i dati sono di tipo carattere e che viene rilevata la distinzione tra maiuscole e minuscole.<br /><br /> **VARIANT_TRUE** indica che il tipo di dati è un tipo di carattere e tra maiuscole e minuscole.<br /><br /> **VARIANT_FALSE** indica che il tipo di dati non è un tipo di carattere o non è tra maiuscole e minuscole.|  
|**RICERCA**|**DBTYPE_UI4**|Valore intero che indica il tipo di dati come utilizzare nelle ricerche se il provider supporta **ICommandText**; in caso contrario, **NULL**. I possibili valori della colonna sono i seguenti:<br /><br /> **DB_UNSEARCHABLE** indica che il tipo di dati non può essere utilizzato in un **dove** clausola.<br /><br /> **DB_LIKE_ONLY** indica il tipo di dati può essere utilizzato in un **in** clausola solo con il **come** predicato.<br /><br /> **DB_ALL_EXCEPT_LIKE** indica il tipo di dati può essere utilizzato in un **in** clausola con tutti gli operatori di confronto tranne **come**.<br /><br /> **DB_SEARCHABLE** indica il tipo di dati può essere utilizzato in un **dove** clausola con qualsiasi operatore di confronto.|  
|**UNSIGNED_ATTRIBUTE**|**DBTYPE_BOOL**|Valore booleano che indica se il tipo di dati è senza segno.<br /><br /> **VARIANT_TRUE** indica che il tipo di dati è senza segno.<br /><br /> **VARIANT_FALSE** indica che il tipo di dati è firmato.<br /><br /> **NULL** indica che questo non è applicabile al tipo di dati.|  
|**FIXED_PREC_SCALE**|**DBTYPE_BOOL**|Valore booleano che indica se il tipo di dati ha precisione e scala fisse.<br /><br /> **VARIANT_TRUE** indica che il tipo di dati ha una precisione e scala fisse.<br /><br /> **VARIANT_FALSE** indica che il tipo di dati non dispone di una precisione e scala fisse.|  
|**AUTO_UNIQUE_VALUE**|**DBTYPE_BOOL**|Valore booleano che indica se il tipo di dati viene incrementato automaticamente.<br /><br /> **VARIANT_TRUE** indica che i valori di questo tipo possono essere incrementati automaticamente.<br /><br /> **VARIANT_FALSE** indica che i valori di questo tipo non possono essere incrementata automaticamente.<br /><br /> Se questo valore è **VARIANT_TRUE**, una colonna di questo tipo venga sempre incrementata automaticamente dipende il provider o meno **DBPROP_COL_AUTOINCREMENT** proprietà della colonna. Se il **DBPROP_COL_AUTOINCREMENT** o meno una colonna di questo tipo venga incrementata automaticamente dipende dall'impostazione di proprietà è di lettura/scrittura, il **DBPROP_COL_AUTOINCREMENT** proprietà. Se **DBPROP_COL_AUTOINCREMENT** è una proprietà di sola lettura, tutte o nessuna delle colonne di questo tipo vengono incrementati automaticamente.|  
|**LOCAL_TYPE_NAME**|**DBTYPE_WSTR**|La versione localizzata di **TYPE_NAME**. **NULL** viene restituito se un nome localizzato non è supportato dal provider di dati.|  
|**MINIMUM_SCALE**|**DBTYPE_I2**|Se l'indicatore del tipo è **DBTYPE_VARNUMERIC**, **DBTYPE_DECIMAL**, o **DBTYPE_NUMERIC**, il numero minimo di cifre consentito a destra del separatore decimale. In caso contrario, **NULL**.|  
|**MAXIMUM_SCALE**|**DBTYPE_I2**|Il numero massimo di cifre consentito a destra del separatore decimale se l'indicatore del tipo è **DBTYPE_VARNUMERIC**, **DBTYPE_DECIMAL**, o **DBTYPE_NUMERIC**; in caso contrario, N**U**LL.|  
|**GUID**|**DBTYPE_GUID**|(Destinato all'utilizzo futuro) Il **GUID** del tipo, se il tipo è descritto in una libreria dei tipi. In caso contrario, **NULL**.|  
|**LIBRERIA DEI TIPI**|**DBTYPE_WSTR**|(Destinato all'utilizzo futuro) Libreria dei tipi contenente la descrizione del tipo, se il tipo viene descritto in una libreria dei tipi. In caso contrario, NULL.|  
|**VERSIONE**|**DBTYPE_WSTR**|(Destinato all'utilizzo futuro) Versione della definizione del tipo. I provider potrebbero ritenere opportuno assegnare una versione alle definizioni del tipo. È possibile che provider diversi utilizzino schemi di controllo delle versioni diversi, ad esempio un timestamp o un numero (integer o float). **NULL** se non è supportato.|  
|**IS_LONG**|**DBTYPE_BOOL**|Valore booleano che indica se il tipo di dati è un oggetto BLOB (Binary Large Object) e contiene dati molto lunghi.<br /><br /> **VARIANT_TRUE** indica che il tipo di dati è un **BLOB** che contiene dati molto lunghi; la definizione di dati molto lunghi è specifica del provider.<br /><br /> **VARIANT_FALSE** indica che il tipo di dati è un **BLOB** che non contiene dati molto lunghi o non è un **BLOB**.<br /><br /> Questo valore determina l'impostazione del **DBCOLUMNFLAGS_ISLONG** flag restituito da **GetColumnInfo** in **IColumnsInfo** e **GetParameterInfo** in **ICommandWithParameters**.|  
|**BEST_MATCH**|**DBTYPE_BOOL**|Valore booleano che indica se il tipo di dati è una corrispondenza più appropriata.<br /><br /> **VARIANT_TRUE** indica che il tipo di dati è la corrispondenza più appropriata tra tutti i tipi di dati nell'archivio dati e il tipo di dati OLE DB indicato dal valore nella **DATA_TYPE** colonna.<br /><br /> **VARIANT_FALSE** indica che il tipo di dati non è la migliore corrispondenza.<br /><br /> Per ogni set di righe in cui il valore della **DATA_TYPE** colonna è lo stesso, il **BEST_MATCH** colonna è impostata su **VARIANT_TRUE** solo in una riga.|  
|**IS_FIXEDLENGTH**|**DBTYPE_BOOL**|Valore booleano che indica se la colonna è a lunghezza fissa.<br /><br /> **VARIANT_TRUE** indica che le colonne di questo tipo create dal linguaggio di definizione dei dati (DDL) saranno di lunghezza fissa.<br /><br /> **VARIANT_FALSE** indica che le colonne di questo tipo create dal DDL saranno di lunghezza variabile.<br /><br /> Se il campo è **NULL**, non è noto se il provider eseguirà il mapping in questo campo con una colonna a lunghezza fissa o a lunghezza variabile.|  
  
 Il set di righe viene ordinato in base **DATA_TYPE**.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il **DBSCHEMA_PROVIDER_TYPES** righe può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|  
|-----------------|--------------------|  
|**DATA_TYPE**|**DBTYPE_UI2**|  
|**BEST_MATCH**|**DBTYPE_BOOL**|  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello Schema OLE DB](../../../analysis-services/schema-rowsets/ole-db/ole-db-schema-rowsets.md)  
  
  

