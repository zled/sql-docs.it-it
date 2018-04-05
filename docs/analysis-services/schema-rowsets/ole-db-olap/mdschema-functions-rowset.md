---
title: Set di righe MDSCHEMA_FUNCTIONS | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- MDSCHEMA_FUNCTIONS
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- MDSCHEMA_FUNCTIONS rowset
ms.assetid: 5253fa8c-b1ce-4504-aff6-a246b5e675c7
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e8a03e34bf6ea617e650132f2a81fb065a014d80
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="mdschemafunctions-rowset"></a>Set di righe MDSCHEMA_FUNCTIONS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Descrive le funzioni disponibili per le applicazioni client connesse al database.  
  
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
|**OGGETTO**|**DBTYPE_WSTR**|(Facoltativo) Nome generico della classe dell'oggetto a cui è applicabile una proprietà. Ad esempio, il set di righe corrispondente a < level_name >. Risultato della funzione membri "**livello**".<br /><br /> Restituisce **VT_NULL** per funzioni definite dall'utente o funzioni MDX non di proprietà.|  
|**DIDASCALIA**|**DBTYPE_WSTR**|Didascalia di visualizzazione per la funzione.|  
  
 Il set di righe viene ordinato in base **origine**, **INTERFACE_NAME**, **nome_funzione**.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il **MDSCHEMA_FUNCTIONS** righe può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|**LIBRARY_NAME**|**DBTYPE_WSTR**|Facoltativo.|  
|**INTERFACE_NAME**|**DBTYPE_WSTR**|Facoltativo.|  
|**NOME_FUNZIONE**|**DBTYPE_WSTR**|Facoltativo.|  
|**ORIGINE**|**DBTYPE_I4**|Facoltativo.|  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello schema OLE DB per OLAP](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
