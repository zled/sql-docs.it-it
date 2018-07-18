---
title: Set di righe MDSCHEMA_FUNCTIONS | Documenti Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7e6786f53ddc48c457857f58128c3f16959420d5
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34036102"
---
# <a name="mdschemafunctions-rowset"></a>Set di righe MDSCHEMA_FUNCTIONS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Descrive le funzioni disponibili per le applicazioni client connesse al database.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il **MDSCHEMA_FUNCTIONS** set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Description|  
|-----------------|--------------------|-----------------|  
|**NOME_FUNZIONE**|**DBTYPE_WSTR**|Nome della funzione.|  
|**DESCRIPTION**|**DBTYPE_WSTR**|Descrizione della funzione.|  
|**PARAMETER_LIST**|**DBTYPE_WSTR**|Elenco di parametri delimitato da virgole formattato come in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic. Ad esempio, un parametro potrebbe essere Name as String.|  
|**RETURN_TYPE**|**DBTYPE_I4**|Il **VARTYPE** del tipo di dati restituito della funzione.|  
|**ORIGINE**|**DBTYPE_I4**|Origine della funzione:<br /><br /> 1 per le funzioni MDX.<br /><br /> 2 per le funzioni definite dall'utente.|  
|**INTERFACE_NAME**|**DBTYPE_WSTR**|Nome dell'interfaccia per le funzioni definite dall'utente<br /><br /> Nome del gruppo per le funzioni MDX (Multidimensional Expressions).|  
|**LIBRARY_NAME**|**DBTYPE_WSTR**|Nome della libreria dei tipi per le funzioni definite dall'utente. **NULL** per le funzioni MDX.|  
|**NOME_DLL**|**DBTYPE_WSTR**|(Facoltativo) Nome dell'assembly che implementa la funzione definita dall'utente.<br /><br /> Restituisce **VT_NULL** per le funzioni MDX.|  
|**HELP_FILE**|**DBTYPE_WSTR**|(Facoltativo) Nome del file che contiene la documentazione della guida per la funzione definita dall'utente.<br /><br /> Restituisce **VT_NULL** per le funzioni MDX.|  
|**HELP_CONTEXT**|**DBTYPE_I4**|(Facoltativo) Restituisce l'ID del contesto della Guida per questa funzione.|  
|**OBJECT**|**DBTYPE_WSTR**|(Facoltativo) Nome generico della classe dell'oggetto a cui è applicabile una proprietà. Ad esempio, il set di righe corrispondente a < level_name >. Risultato della funzione membri "**livello**".<br /><br /> Restituisce **VT_NULL** per funzioni definite dall'utente o funzioni MDX non di proprietà.|  
|**DIDASCALIA**|**DBTYPE_WSTR**|Didascalia di visualizzazione per la funzione.|  
  
 Il set di righe viene ordinato in base **origine**, **INTERFACE_NAME**, **nome_funzione**.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il **MDSCHEMA_FUNCTIONS** righe può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|**LIBRARY_NAME**|**DBTYPE_WSTR**|Facoltativa.|  
|**INTERFACE_NAME**|**DBTYPE_WSTR**|Facoltativa.|  
|**NOME_FUNZIONE**|**DBTYPE_WSTR**|Facoltativa.|  
|**ORIGINE**|**DBTYPE_I4**|Facoltativa.|  
  
## <a name="see-also"></a>Vedere anche  
 [OLE DB per OLAP i rowset dello Schema](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
