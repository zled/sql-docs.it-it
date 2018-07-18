---
title: Set di righe MDSCHEMA_SETS | Documenti Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 666f8aa8889f2d15e9e62499e41ad9c0bc69fcff
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="mdschemasets-rowset"></a>Set di righe MDSCHEMA_SETS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Descrive i set attualmente definiti in un database, inclusi i set con ambito sessione.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il **MDSCHEMA_SETS** set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Description|  
|-----------------|--------------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Nome del database.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Non supportato.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Nome del cubo.|  
|**SET_NAME**|**DBTYPE_WSTR**|Il nome del set, come specificato nella **CREATE SET** istruzione.|  
|**AMBITO**|**DBTYPE_I4**|Ambito del set.<br /><br /> **MDSET_SCOPE_GLOBAL** (**1**)<br /><br /> **MDSET_SCOPE_SESSION** (**2**)|  
|**DESCRIPTION**|**DBTYPE_WSTR**|Non supportato.|  
|**ESPRESSIONE**|**DBTYPE_WSTR**|Espressione per il set.|  
|**DIMENSIONI**|**DBTYPE_WSTR**|Elenco delimitato da virgole delle gerarchie incluse nel set.|  
|**SET_CAPTION**|**DBTYPE_WSTR**|Etichetta o didascalia associata al set. L'etichetta o la didascalia viene utilizzata principalmente per scopi di visualizzazione.|  
|**SET_DISPLAY_FOLDER**|**DBTYPE_WSTR**|Una stringa che identifica il percorso della cartella di visualizzazione che l'applicazione client utilizza per mostrare il set. Il separatore di livello delle cartelle è definito dall'applicazione client. Per gli strumenti e i client forniti da [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], la barra rovesciata (\\) è il separatore di livello. Per fornire più cartelle di visualizzazione, utilizzare un punto e virgola (;) per separare le cartelle.|  
|**SET_EVALUATION_CONTEXT**|**DBTYPE_I4**|Contesto del set. Il set può essere statico o dinamico. I possibili valori della colonna sono i seguenti:<br /><br /> MDSET_RESOLUTION_STATIC=1<br /><br /> MDSET_RESOLUTION_DYNAMIC=2|  
  
 Il set di righe viene ordinato in base **CATALOG_NAME**, **SCHEMA_NAME**, **CUBE_NAME**.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il **MDSCHEMA_SETS** righe può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Facoltativa.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Facoltativa.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Facoltativa.|  
|**SET_NAME**|**DBTYPE_WSTR**|Facoltativa.|  
|**AMBITO**|**DBTYPE_I4**|Facoltativa.|  
|**HIERARCHY_UNIQUE_NAME**|**DBTYPE_WSTR**|Facoltativa.|  
|**CUBE_SOURCE**|**DBTYPE_UI2**|Facoltativa.<br /><br /> Nota: Solo una gerarchia può essere inclusa e le cui gerarchie corrispondono esattamente alla restrizione vengono restituiti solo i set denominati.|  
  
## <a name="see-also"></a>Vedere anche  
 [OLE DB per OLAP i rowset dello Schema](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
