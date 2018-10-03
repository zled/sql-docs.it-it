---
title: Set di righe DBSCHEMA_PROVIDER_TYPES | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DBSCHEMA_PROVIDER_TYPES
topic_type:
- apiref
helpviewer_keywords:
- DBSCHEMA_PROVIDER_TYPES rowset
ms.assetid: 255e01ba-53a9-478d-9b86-45faba76710e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2840e67e8ddb1b412164bacc6c26ff9ac0c90e10
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48049187"
---
# <a name="dbschemaprovidertypes-rowset"></a>Set di righe DBSCHEMA_PROVIDER_TYPES
  Identifica i tipi di dati (di base) supportati dal provider di dati.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il `DBSCHEMA_PROVIDER_TYPES` set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Length|Description|  
|-----------------|--------------------|------------|-----------------|  
|`TYPE_NAME`|`DBTYPE_WSTR`||Nome del tipo di dati specifico del provider.|  
|`DATA_TYPE`|`DBTYPE_UI2`||Indicatore del tipo di dati.|  
|`COLUMN_SIZE`|`DBTYPE_UI4`||Lunghezza di una colonna o un parametro non numerico che fa riferimento alla lunghezza massima o alla lunghezza definita per questo tipo dal provider. Per i dati di tipo carattere, si tratta della lunghezza massima o definita in caratteri. Per i tipi di dati DateTime, si tratta della lunghezza della rappresentazione di stringa (presupponendo la precisione massima consentita del componente delle frazioni di secondo).<br /><br /> Se il tipo di dati è numerico, si tratta del limite superiore rispetto alla precisione massima del tipo di dati.|  
|`LITERAL_PREFIX`|`DBTYPE_WSTR`||Carattere o caratteri utilizzati per aggiungere come prefisso un valore letterale di questo tipo in un comando di testo.|  
|`LITERAL_SUFFIX`|`DBTYPE_WSTR`||Carattere o caratteri utilizzati per aggiungere come suffisso un valore letterale di questo tipo in un comando di testo.|  
|`CREATE_PARAMS`|`DBTYPE_WSTR`||Parametri di creazione specificati dal consumer al momento della creazione di una colonna di questo tipo di dati. Ad esempio, il tipo di dati SQL `DECIMAL,` richiede una precisione e una scala. In questo caso, i parametri di creazione potrebbero essere costituiti dalla stringa "precision,scale". In un comando di testo per creare una colonna `DECIMAL` con una precisione pari a 10 e una scala pari a 2, il valore della colonna `TYPE_NAME` potrebbe essere `DECIMAL()` e la specifica del tipo completo sarebbe `DECIMAL(10,2)`.<br /><br /> I parametri di creazione sono visualizzati come un elenco di valori delimitato da virgole, nell'ordine in cui devono essere forniti e senza essere racchiusi tra parentesi. Se un parametro di creazione è lunghezza, lunghezza massima, precisione, scala, valore di inizializzazione o incremento, utilizzare rispettivamente "lunghezza", "lunghezza massima", "precisione", "scala", "valore di inizializzazione" e "incremento". Se il parametro di creazione è un altro valore, il provider determina il testo da utilizzare per descrivere il parametro di creazione.<br /><br /> Se il tipo di dati richiede parametri di creazione, nel nome del tipo vengono generalmente visualizzati i caratteri "()", che indicano la posizione in cui inserire i parametri di creazione. Se il nome del tipo non include "()", i parametri di creazione vengono racchiusi tra parentesi e aggiunti al nome del tipo di dati.|  
|`IS_NULLABLE`|`DBTYPE_BOOL`||Valore booleano che indica se il tipo di dati ammette valori Null.<br /><br /> `VARIANT_TRUE` indica che il tipo di dati ammette valori Null.<br /><br /> `VARIANT_FALSE` indica che il tipo di dati non ammette valori null.<br /><br /> `NULL` indica che non è noto se il tipo di dati ammette valori Null.|  
|`CASE_SENSITIVE`|`DBTYPE_BOOL`||Valore booleano che indica che i dati sono di tipo carattere e che viene rilevata la distinzione tra maiuscole e minuscole.<br /><br /> `VARIANT_TRUE` indica che i dati non sono di tipo carattere e che viene rilevata la distinzione tra maiuscole e minuscole.<br /><br /> `VARIANT_FALSE` indica che i dati non sono di tipo carattere o che non viene rilevata la distinzione tra maiuscole e minuscole.|  
|`SEARCHABLE`|`DBTYPE_UI4`||Valore integer che indica come è possibile utilizzare il tipo di dati nelle ricerche se il provider supporta `ICommandText`; in caso contrario, `NULL`.<br /><br /> I possibili valori della colonna sono i seguenti:<br /><br /> -   `DB_UNSEARCHABLE` indica il tipo di dati non può essere utilizzato un `WHERE` clausola.<br />-   `DB_LIKE_ONLY` indica che il tipo di dati può essere utilizzato una `WHERE` clausola solo con il `LIKE` predicato.<br />-   `DB_ALL_EXCEPT_LIKE` indica che il tipo di dati può essere utilizzato una `WHERE` clausola con tutti gli operatori di confronto tranne `LIKE`.<br />-   `DB_SEARCHABLE` indica che il tipo di dati può essere utilizzato un `WHERE` clausola con qualsiasi operatore di confronto.|  
|`UNSIGNED_ATTRIBUTE`|`DBTYPE_BOOL`||Valore booleano che indica se il tipo di dati è senza segno.<br /><br /> `VARIANT_TRUE` indica che il tipo di dati è senza segno.<br /><br /> `VARIANT_FALSE` indica che il tipo di dati è con segno.<br /><br /> `NULL` indica che non è applicabile al tipo di dati.|  
|`FIXED_PREC_SCALE`|`DBTYPE_BOOL`||Valore booleano che indica se il tipo di dati ha precisione e scala fisse.<br /><br /> `VARIANT_TRUE` indica che il tipo di dati ha precisione e scala fisse.<br /><br /> `VARIANT_FALSE` indica che il tipo di dati non ha precisione e scala fisse.|  
|`AUTO_UNIQUE_VALUE`|`DBTYPE_BOOL`||Valore booleano che indica se il tipo di dati viene incrementato automaticamente.<br /><br /> `VARIANT_TRUE` indica che i valori di questo tipo possono essere incrementati automaticamente.<br /><br /> `VARIANT_FALSE` indica che i valori di questo tipo non possono essere incrementati automaticamente.<br /><br /> Se questo valore è `VARIANT_TRUE`, il fatto che una colonna di questo tipo venga sempre incrementata automaticamente dipende dalla proprietà della colonna `DBPROP_COL_AUTOINCREMENT` del provider. Se la proprietà `DBPROP_COL_AUTOINCREMENT` è di lettura/scrittura, il fatto che una colonna di questo tipo venga incrementata automaticamente o meno dipende dall'impostazione della proprietà `DBPROP_COL_AUTOINCREMENT`. Se `DBPROP_COL_AUTOINCREMENT` è una proprietà di sola lettura, l'incremento automatico si applica a tutte le colonne di questo tipo oppure non si applica a nessuna.|  
|`LOCAL_TYPE_NAME`|`DBTYPE_WSTR`||La versione localizzata di `TYPE_NAME`. `NULL` viene restituito se il nome localizzato non è supportato dal provider di dati.|  
|`MINIMUM_SCALE`|`DBTYPE_I2`||Se l'indicatore del tipo è `DBTYPE_VARNUMERIC`, `DBTYPE_DECIMAL` oppure `DBTYPE_NUMERIC`, numero minimo di cifre consentite a destra del separatore decimale. In caso contrario, `NULL`.|  
|`MAXIMUM_SCALE`|`DBTYPE_I2`||Se l'indicatore del tipo è `DBTYPE_VARNUMERIC`, `DBTYPE_DECIMAL` oppure `DBTYPE_NUMERIC`, numero massimo di cifre consentite a destra del separatore decimale; in caso contrario, N`U`LL.|  
|`GUID`|`DBTYPE_GUID`||(Destinato all'utilizzo futuro) `GUID` del tipo, se il tipo viene descritto in una libreria dei tipi. In caso contrario, `NULL`.|  
|`TYPELIB`|`DBTYPE_WSTR`||(Destinato all'utilizzo futuro) Libreria dei tipi contenente la descrizione del tipo, se il tipo viene descritto in una libreria dei tipi. In caso contrario, NULL.|  
|`VERSION`|`DBTYPE_WSTR`||(Destinato all'utilizzo futuro) Versione della definizione del tipo. I provider potrebbero ritenere opportuno assegnare una versione alle definizioni del tipo. È possibile che provider diversi utilizzino schemi di controllo delle versioni diversi, ad esempio un timestamp o un numero (integer o float). `NULL` se non supportato.|  
|`IS_LONG`|`DBTYPE_BOOL`||Valore booleano che indica se il tipo di dati è un oggetto BLOB (Binary Large Object) e contiene dati molto lunghi.<br /><br /> `VARIANT_TRUE` indica che il tipo di dati è un oggetto `BLOB` che contiene dati molto lunghi; la definizione dei dati molto lunghi è specifica del provider.<br /><br /> `VARIANT_FALSE` indica che il tipo di dati è un oggetto `BLOB` che non contiene dati molto lunghi oppure non è un oggetto `BLOB`.<br /><br /> Questo valore determina l'impostazione del flag `DBCOLUMNFLAGS_ISLONG` restituito da `GetColumnInfo` in `IColumnsInfo` e da `GetParameterInfo` in `ICommandWithParameters`.|  
|`BEST_MATCH`|`DBTYPE_BOOL`||Valore booleano che indica se il tipo di dati è una corrispondenza più appropriata.<br /><br /> `VARIANT_TRUE` indica che il tipo di dati è la corrispondenza più appropriata tra tutti i tipi di dati nell'archivio dati e il tipo di dati OLE DB indicato dal valore nella colonna `DATA_TYPE`.<br /><br /> `VARIANT_FALSE` indica che il tipo di dati non è la corrispondenza più appropriata.<br /><br /> Per ciascun set di righe in cui il valore della colonna `DATA_TYPE` è identico, la colonna `BEST_MATCH` viene impostata su `VARIANT_TRUE` in una sola riga.|  
|`IS_FIXEDLENGTH`|`DBTYPE_BOOL`||Valore booleano che indica se la colonna è a lunghezza fissa.<br /><br /> `VARIANT_TRUE` indica che le colonne di questo tipo create da Data Definition Language (DDL) saranno a lunghezza fissa.<br /><br /> `VARIANT_FALSE` indica che le colonne di questo tipo create da Data Definition Language (DDL) saranno a lunghezza variabile.<br /><br /> Se il campo è `NULL`, non è noto se il provider eseguirà il mapping di questo campo con una colonna a lunghezza fissa o a lunghezza variabile.|  
  
 Il set di righe viene ordinato in base a `DATA_TYPE`.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il set di righe `DBSCHEMA_PROVIDER_TYPES` può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|`DATA_TYPE`|`DBTYPE_UI2`||  
|`BEST_MATCH`|`DBTYPE_BOOL`||  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello schema OLE DB](ole-db-schema-rowsets.md)  
  
  
