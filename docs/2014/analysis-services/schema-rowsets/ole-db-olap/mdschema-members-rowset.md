---
title: Set di righe mdschema_members | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MDSCHEMA_MEMBERS
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_MEMBERS rowset
ms.assetid: 0b1aada0-67f8-4ef6-81b2-0100b65e0c2f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: dbe7db640163f539ba15e8418177846564731148
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48133901"
---
# <a name="mdschemamembers-rowset"></a>Set di righe MDSCHEMA_MEMBERS
  Descrive i membri all'interno di un database.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il `MDSCHEMA_MEMBERS` set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Length|Description|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||Nome del database a cui appartiene il membro.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||Nome dello schema a cui appartiene il membro.|  
|`CUBE_NAME`|`DBTYPE_WSTR`||Nome del cubo a cui appartiene il membro.|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`||Nome univoco della dimensione a cui appartiene il membro.|  
|`HIERARCHY_UNIQUE_NAME`|`DBTYPE_WSTR`||Nome univoco della gerarchia a cui appartiene il membro.|  
|`LEVEL_UNIQUE_NAME`|`DBTYPE_WSTR`||Nome univoco del livello a cui appartiene il membro.|  
|`LEVEL_NUMBER`|`DBTYPE_UI4`||Distanza del membro dalla radice della gerarchia. Il livello radice è zero (0).|  
|`MEMBER_ORDINAL`|`DBTYPE_UI4`||(Deprecato) Restituisce sempre `0`.|  
|`MEMBER_NAME`|`DBTYPE_WSTR`||Nome del membro.|  
|`MEMBER_UNIQUE_NAME`|`DBTYPE_WSTR`||Nome univoco del membro.|  
|`MEMBER_TYPE`|`DBTYPE_I4`||Tipo del membro:<br /><br /> -   `MDMEMBER_TYPE_REGULAR` (`1`)<br />-   `MDMEMBER_TYPE_ALL` (`2`)<br />-   `MDMEMBER_TYPE_MEASURE` (`3`)<br />-   `MDMEMBER_TYPE_FORMULA` (`4`)<br />-   `MDMEMBER_TYPE_UNKNOWN` (`0`)<br />-   `MDMEMBER_TYPE_FORMULA` ha la precedenza su `MDMEMBER_TYPE_MEASURE`. Ad esempio, se nella dimensione Measures esiste un membro di tipo formula (calcolato), questo verrà elencato come `MDMEMBER_TYPE_FORMULA`.|  
|`MEMBER_GUID`|`DBTYPE_GUID`||GUID del membro. `NULL` se non è presente alcuna GUID.|  
|`MEMBER_CAPTION`|`DBTYPE_WSTR`||Etichetta o didascalia associata al membro. Utilizzata principalmente a scopo di visualizzazione. Se non esiste una didascalia, viene restituito `MEMBER_NAME`.|  
|`CHILDREN_CARDINALITY`|`DBTYPE_UI4`||Numero di elementi figlio del membro. Poiché può trattarsi di una stima, è necessario che i consumer non considerino questo valore come il conteggio esatto. I provider restituiscono la migliore stima possibile.|  
|`PARENT_LEVEL`|`DBTYPE_UI4`||Distanza dell'elemento padre del membro dal livello radice della gerarchia. Il livello radice è zero (0).|  
|`PARENT_UNIQUE_NAME`|`DBTYPE_WSTR`||Nome univoco del nodo padre del membro. `NULL` viene restituito per tutti i membri al livello di radice.|  
|`PARENT_COUNT`|`DBTYPE_UI4`||Numero di elementi padre del membro.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Questa colonna restituisce sempre un valore `NULL`.<br /><br /> Questa colonna esiste per garantire la compatibilità con le versioni precedenti.|  
|`EXPRESSION`|`DBTYPE_WSTR`||Espressione per i calcoli, se il membro è di tipo `MDMEMBER_TYPE_FORMULA`.|  
|`MEMBER_KEY`|`DBTYPE_WSTR`||Valore della colonna chiave del membro. Restituisce `NULL` se il membro dispone di una chiave composta.|  
|`IS_PLACEHOLDERMEMBER`|`DBTYPE_BOOL`||Valore booleano che indica se un membro è un membro segnaposto per una posizione vuota in una gerarchia della dimensione.<br /><br /> È valido solo se la proprietà `MDX Compatibility` è stata impostata su 2.|  
|`IS_DATAMEMBER`|`DBTYPE_BOOL`||Valore booleano che indica se il membro è un membro dati.<br /><br /> Restituisce True se il membro è un membro dei dati.|  
|`SCOPE`|`DBTYPE_I4`||Ambito del membro. Il membro può essere un membro calcolato della sessione o un membro calcolato globale. In questa colonna viene restituito `NULL` per i membri non calcolati.<br /><br /> I possibili valori della colonna sono i seguenti:<br /><br /> -MDMEMBER_SCOPE_GLOBAL=1 = 1<br />-MDMEMBER_SCOPE_SESSION=2 = 2|  
|`Zero or more additional columns`|`DBTYPE_UI2`||Non viene restituita alcuna proprietà se i membri possono essere restituiti da più livelli. Ad esempio, se l'operatore di albero corrisponde a `PARENT` e `SELF` per una gerarchia non di tipo padre-figlio, non viene restituita alcuna proprietà del membro.<br /><br /> Si applica alle gerarchie incomplete dove gli operatori di albero possono restituire membri da livelli diversi, ad esempio se il livello precedente contiene spazi vuoti ed è necessario che il membro disponga di un elemento padre.|  
  
 Il set di righe viene ordinato in base a `CATALOG_NAME`, `SCHEMA_NAME`, `CUBE_NAME`, `DIMENSION_UNIQUE_NAME`, `HIERARCHY_UNIQUE_NAME`, `LEVEL_UNIQUE_NAME`, `LEVEL_NUMBER`, `MEMBER_ORDINAL`.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il set di righe `MDSCHEMA_MEMBERS` può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`HIERARCHY_UNIQUE_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`LEVEL_UNIQUE_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`LEVEL_NUMBER`|`DBTYPE_UI4`|Facoltativo.|  
|`MEMBER_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`MEMBER_UNIQUE_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`MEMBER_CAPTION`|`DBTYPE_WSTR`|Facoltativo.|  
|`MEMBER_TYPE`|`DBTYPE_I4`|Facoltativo.|  
|`TREE_OP`|`DBTYPE_I4`|(Facoltativo) Si applica solo a un singolo membro:<br /><br /> -   `MDTREEOP_ANCESTORS` (`0x20`) restituisce tutti i predecessori.<br />-   `MDTREEOP_CHILDREN` (`0x01`) restituisce solo gli elementi figlio immediati.<br />-   `MDTREEOP_SIBLINGS` (`0x02`) restituisce i membri allo stesso livello.<br />-   `MDTREEOP_PARENT` (`0x04`) restituisce solo l'oggetto padre.<br />-   `MDTREEOP_SELF` (`0x08`) restituisce se stesso nell'elenco di righe restituite.<br />-   `MDTREEOP_DESCENDANTS` (`0x10`) restituisce tutti i discendenti.|  
|`CUBE_SOURCE`|`DBTYPE_UI2`|(Facoltativo) Bitmap con uno dei seguenti valori validi:<br /><br /> -1 CUBO<br />-DIMENSIONE DI 2<br /><br /> La restrizione predefinita è impostata sul valore 1.|  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello schema OLE DB per OLAP](ole-db-for-olap-schema-rowsets.md)  
  
  
