---
title: Set di righe MDSCHEMA_SETS | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MDSCHEMA_SETS
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_SETS rowset
ms.assetid: abb00dc0-2b83-48d6-b2ba-6615c1488d06
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1e3008fc6b56146c22a7508398dcc3896a697644
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48059534"
---
# <a name="mdschemasets-rowset"></a>Set di righe MDSCHEMA_SETS
  Descrive i set attualmente definiti in un database, inclusi i set con ambito sessione.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il `MDSCHEMA_SETS` set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Length|Description|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||Nome del database.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||Non supportato.|  
|`CUBE_NAME`|`DBTYPE_WSTR`||Nome del cubo.|  
|`SET_NAME`|`DBTYPE_WSTR`||Nome del set, come specificato nell'istruzione `CREATE SET`.|  
|`SCOPE`|`DBTYPE_I4`||Ambito del set.<br /><br /> -   `MDSET_SCOPE_GLOBAL` (`1`)<br />-   `MDSET_SCOPE_SESSION` (`2`)|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Non supportato.|  
|`EXPRESSION`|`DBTYPE_WSTR`||Espressione per il set.|  
|`DIMENSIONS`|`DBTYPE_WSTR`||Elenco delimitato da virgole delle gerarchie incluse nel set.|  
|`SET_CAPTION`|`DBTYPE_WSTR`||Etichetta o didascalia associata al set. L'etichetta o la didascalia viene utilizzata principalmente per scopi di visualizzazione.|  
|`SET_DISPLAY_FOLDER`|`DBTYPE_WSTR`||Una stringa che identifica il percorso della cartella di visualizzazione che l'applicazione client utilizza per mostrare il set. Il separatore di livello delle cartelle è definito dall'applicazione client. Per gli strumenti e i client forniti da [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], la barra rovesciata (\\) è il separatore di livello. Per fornire più cartelle di visualizzazione, usare un punto e virgola (;) per separare le cartelle.|  
|`SET_EVALUATION_CONTEXT`|`DBTYPE_I4`||Contesto del set. Il set può essere statico o dinamico.<br /><br /> I possibili valori della colonna sono i seguenti:<br /><br /> -MDSET_RESOLUTION_STATIC = 1<br />-MDSET_RESOLUTION_DYNAMIC = 2|  
  
 Il set di righe viene ordinato in base a `CATALOG_NAME`, `SCHEMA_NAME`, `CUBE_NAME`.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il set di righe `MDSCHEMA_SETS` può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`SET_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`SCOPE`|`DBTYPE_I4`|Facoltativo.|  
|`HIERARCHY_UNIQUE_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`CUBE_SOURCE`|`DBTYPE_UI2`|Facoltativo. **Nota:** solo una gerarchia può essere inclusa, e le cui gerarchie corrispondono esattamente alla restrizione vengono restituiti solo i set denominati.|  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello schema OLE DB per OLAP](ole-db-for-olap-schema-rowsets.md)  
  
  
