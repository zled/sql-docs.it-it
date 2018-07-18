---
title: Set di righe MDSCHEMA_FUNCTIONS | Microsoft Docs
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
- MDSCHEMA_FUNCTIONS
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_FUNCTIONS rowset
ms.assetid: 5253fa8c-b1ce-4504-aff6-a246b5e675c7
caps.latest.revision: 27
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 587d361eef197378fcc8b0347b9289ae2b81e99a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37159282"
---
# <a name="mdschemafunctions-rowset"></a>Set di righe MDSCHEMA_FUNCTIONS
  Descrive le funzioni disponibili per le applicazioni client connesse al database.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il **MDSCHEMA_FUNCTIONS** set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Length|Description|  
|-----------------|--------------------|------------|-----------------|  
|**NOME_FUNZIONE**|**DBTYPE_WSTR**||Nome della funzione.|  
|**DESCRIPTION**|**DBTYPE_WSTR**||Descrizione della funzione.|  
|**PARAMETER_LIST**|**DBTYPE_WSTR**||Elenco di parametri delimitato da virgole formattato come in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic. Ad esempio, un parametro potrebbe essere Name as String.|  
|**RETURN_TYPE**|**DBTYPE_I4**||Il **VARTYPE** del tipo di dati restituito della funzione.|  
|**ORIGINE**|**DBTYPE_I4**||Origine della funzione:<br /><br /> -1 per le funzioni MDX.<br />-2 per le funzioni definite dall'utente.|  
|**INTERFACE_NAME**|**DBTYPE_WSTR**||Nome dell'interfaccia per le funzioni definite dall'utente<br /><br /> Nome del gruppo per le funzioni MDX (Multidimensional Expressions).|  
|**LIBRARY_NAME**|**DBTYPE_WSTR**||Nome della libreria dei tipi per le funzioni definite dall'utente. **NULL** per le funzioni MDX.|  
|**NOME_DLL**|**DBTYPE_WSTR**||(Facoltativo) Nome dell'assembly che implementa la funzione definita dall'utente.<br /><br /> Restituisce **VT_NULL** per le funzioni MDX.|  
|**HELP_FILE**|**DBTYPE_WSTR**||(Facoltativo) Nome del file che contiene la documentazione della guida per la funzione definita dall'utente.<br /><br /> Restituisce **VT_NULL** per le funzioni MDX.|  
|**HELP_CONTEXT**|**DBTYPE_I4**||(Facoltativo) Restituisce l'ID del contesto della Guida per questa funzione.|  
|**OBJECT**|**DBTYPE_WSTR**||(Facoltativo) Nome generico della classe dell'oggetto a cui è applicabile una proprietà. Ad esempio, il set di righe corrispondente a < level_name >. I membri di funzione restituisce "**livello**".<br /><br /> Restituisce **VT_NULL** per funzioni definite dall'utente o funzioni MDX non di proprietà.|  
|**DIDASCALIA**|**DBTYPE_WSTR**||Didascalia di visualizzazione per la funzione.|  
  
 Il set di righe viene ordinato in base **ORIGIN**, **INTERFACE_NAME**, **nome_funzione**.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il **MDSCHEMA_FUNCTIONS** righe può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|**LIBRARY_NAME**|**DBTYPE_WSTR**|Facoltativo.|  
|**INTERFACE_NAME**|**DBTYPE_WSTR**|Facoltativo.|  
|**NOME_FUNZIONE**|**DBTYPE_WSTR**|Facoltativo.|  
|**ORIGINE**|**DBTYPE_I4**|Facoltativo.|  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello schema OLE DB per OLAP](ole-db-for-olap-schema-rowsets.md)  
  
  
