---
title: Set di righe MDSCHEMA_HIERARCHIES | Documenti Microsoft
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
- MDSCHEMA_HIERARCHIES
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- MDSCHEMA_HIERARCHIES rowset
ms.assetid: 2e5b2a81-366e-4d5b-af1e-1d372bf596d9
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 7ecdc6817c5a2d7e1e88b909080a3156c55f40eb
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="mdschemahierarchies-rowset"></a>Set di righe MDSCHEMA_HIERARCHIES
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Descrive ogni gerarchia all'interno di una dimensione specifica.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il **MDSCHEMA_HIERARCHIES** set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Description|  
|-----------------|--------------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Nome del catalogo a cui appartiene questa gerarchia. **NULL** se il provider non supporta i cataloghi.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Non supportato|  
|**CUBE_NAME**|**DBTYPE_WSTR**|(Obbligatorio) Nome del cubo a cui appartiene questa gerarchia.|  
|**DIMENSION_UNIQUE_NAME**|**DBTYPE_WSTR**|Nome univoco della dimensione a cui appartiene questa gerarchia. Per i provider che generano nomi univoci tramite qualificazione, i singoli componenti di tale nome sono delimitati.|  
|**HIERARCHY_NAME**|**DBTYPE_WSTR**|Il nome della gerarchia. Vuoto se è presente una sola gerarchia nella dimensione. Ciò avrà sempre un valore [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|**HIERARCHY_UNIQUE_NAME**|**DBTYPE_WSTR**|Nome univoco della gerarchia.|  
|**HIERARCHY_GUID**|**DBTYPE_GUID**|Non supportato|  
|**HIERARCHY_CAPTION**|**DBTYPE_WSTR**|Etichetta o didascalia associata alla gerarchia. Utilizzata principalmente a scopo di visualizzazione. Se non esiste una didascalia, **HIERARCHY_NAME** viene restituito. Se la dimensione non contiene una gerarchia o dispone di una sola gerarchia, questa colonna conterrà il nome della dimensione.|  
|**DIMENSION_TYPE**|**DBTYPE_I2**|Tipo della dimensione. Tra i valori validi sono inclusi i seguenti:<br /><br /> **MD_DIMTYPE_UNKNOWN** (**0**)<br /><br /> **MD_DIMTYPE_TIME** (**1**)<br /><br /> **MD_DIMTYPE_MEASURE** (**2**)<br /><br /> **MD_DIMTYPE_OTHER** (**3**)<br /><br /> **MD_DIMTYPE_QUANTITATIVE** (**5**)<br /><br /> **MD_DIMTYPE_ACCOUNTS** (**6**)<br /><br /> **MD_DIMTYPE_CUSTOMERS** (**7**)<br /><br /> **MD_DIMTYPE_PRODUCTS** (**8**)<br /><br /> **MD_DIMTYPE_SCENARIO** (**9**)<br /><br /> **MD_DIMTYPE_UTILIY** (**10**)<br /><br /> **MD_DIMTYPE_CURRENCY** (**11**)<br /><br /> **MD_DIMTYPE_RATES** (**12**)<br /><br /> **MD_DIMTYPE_CHANNEL** (**13**)<br /><br /> **MD_DIMTYPE_PROMOTION** (**14**)<br /><br /> **MD_DIMTYPE_ORGANIZATION** (**15**)<br /><br /> **MD_DIMTYPE_BILL_OF_MATERIALS** (**16**)<br /><br /> **MD_DIMTYPE_GEOGRAPHY** (**17**)|  
|**HIERARCHY_CARDINALITY**|**DBTYPE_UI4**|Numero di membri nella gerarchia.|  
|**DEFAULT_MEMBER**|**DBTYPE_WSTR**|Membro predefinito per questa gerarchia. Si tratta di un nome univoco. È necessario che ogni gerarchia disponga di un membro predefinito.|  
|**ALL_MEMBER**|**DBTYPE_WSTR**|Membro al livello più elevato del rollup.|  
|**DESCRIPTION**|**DBTYPE_WSTR**|Descrizione leggibile della gerarchia. **NULL** se è presente alcuna descrizione.|  
|**STRUTTURA**|**DBTYPE_I2**|Struttura della gerarchia. Tra i valori validi sono inclusi i seguenti:<br /><br /> **MD_STRUCTURE_FULLYBALANCED** (**0**)<br /><br /> **MD_STRUCTURE_RAGGEDBALANCED** (**1**)<br /><br /> **MD_STRUCTURE_UNBALANCED** (**2**)<br /><br /> **MD_STRUCTURE_NETWORK** (**3**)|  
|**IS_VIRTUAL**|**DBTYPE_BOOL**|Restituisce sempre **False**.|  
|**IS_READWRITE**|**DBTYPE_BOOL**|Valore booleano che indica se il writeback nella colonna delle dimensioni è abilitato.<br /><br /> Restituisce **TRUE** se il **writeback nella dimensione** colonna che rappresenta questa gerarchia è abilitata.|  
|**DIMENSION_UNIQUE_SETTINGS**|**DBTYPE_I4**|Restituisce sempre **MDDIMENSIONS_MEMBER_KEY_UNIQUE** (**1**).|  
|**DIMENSION_MASTER_UNIQUE_NAME**|**DBTYPE_WSTR**|Restituisce sempre **NULL**.|  
|**DIMENSION_IS_VISIBLE**|**DBTYPE_BOOL**|Restituisce sempre **true**. Se la dimensione non è visibile, non verrà visualizzata nel set di righe dello schema.|  
|**HIERARCHY_ORDINAL**|**DBTYPE_UI4**|Numero ordinale della gerarchia tra tutte le gerarchie del cubo.|  
|**DIMENSION_IS_SHARED**|**DBTYPE_BOOL**|Restituisce sempre **TRUE**.|  
|**HIERARCHY_IS_VISIBLE**|**DBTYPE_BOOL**|Valore booleano che indica se la gerarchia è visibile.<br /><br /> Restituisce **TRUE** se la gerarchia è visibile; in caso contrario, **FALSE**.|  
|**HIERARCHY_ORIGIN**|**DBTYPE_UI2**|Maschera di bit che determina l'origine della gerarchia:<br /><br /> **MD_USER_DEFINED** identifica le gerarchie definite dall'utente e ha un valore di **0x0000001**.<br /><br /> **MD_SYSTEM_ENABLED** identifica le gerarchie di attributi e ha un valore di **0x0000002**.<br /><br /> **MD_SYSTEM_INTERNAL** identifica gli attributi senza gerarchie e ha un valore di **0x0000004**.<br /><br /> <br /><br /> Si noti che una gerarchia dell'attributo padre/figlio è sia **MD_USER_DEFINED** e **MD_SYSTEM_ENABLED**.|  
|**HIERARCHY_DISPLAY_FOLDER**|**DBTYPE_WSTR**|Il percorso da utilizzare durante la visualizzazione della gerarchia nell'interfaccia utente. I nomi delle cartelle saranno separati da un punto e virgola (;). Cartelle nidificate sono indicate da una barra rovesciata (\\).|  
|**INSTANCE_SELECTION**|**DBTYPE_UI2**|Hint per l'applicazione client relativo alla modalità di visualizzazione della gerarchia. Tra i valori validi sono inclusi i seguenti:<br /><br /> **MD_INSTANCE_SELECTION_NONE**<br /><br /> **MD_INSTANCE_SELECTION_DROPDOWN**<br /><br /> **MD_INSTANCE_SELECTION_LIST**<br /><br /> **MD_INSTANCE_SELECTION_FILTEREDLIST**<br /><br /> **MD_INSTANCE_SELECTION_MANDATORYFILTER**|  
|**GROUPING_BEHAVIOR**|**DBTYPE_I2**|Enumerazione tramite cui viene specificato il comportamento di raggruppamento previsto dei client per questa gerarchia. Di seguito sono indicati i valori possibili:<br /><br /> **EncourageGrouping** (1)<br /><br /> **DiscourageGrouping** (2)|  
|**STRUCTURE_TYPE**|**DBTYPE_WSTR**|Indica il tipo di gerarchia. Tra i valori validi sono inclusi i seguenti:<br /><br /> **Naturale**<br /><br /> **Non naturali**<br /><br /> **Unknown**|  
  
 Il set di righe viene ordinato in base **CATALOG_NAME**, **SCHEMA_NAME**, **CUBE_NAME**, **DIMENSION_UNIQUE_NAME**, **HIERARCHY_ NOME**.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il **MDSCHEMA_HIERARCHIES** righe può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Facoltativo.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Facoltativo.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Facoltativo.|  
|**DIMENSION_UNIQUE_NAME**|**DBTYPE_WSTR**|Facoltativo.|  
|**HIERARCHY_NAME**|**DBTYPE_WSTR**|Facoltativo.|  
|**HIERARCHY_UNIQUE_NAME**|**DBTYPE_WSTR**|Facoltativo.|  
|**HIERARCHY_ORIGIN**|**DBTYPE_UI2**|(Facoltativo) Una restrizione predefinita è attiva su MD_USER_DEFINED e MD_SYSTEM_ENABLED.|  
|**CUBE_SOURCE**|**DBTYPE_UI2**|(Facoltativo) Restrizione predefinita è un valore pari a 1. Una bitmap con uno dei valori validi seguenti:<br /><br /> 1 CUBO<br /><br /> 2 DIMENSIONE|  
|**HIERARCHY_VISIBILITY**|**DBTYPE_UI2**|(Facoltativo) Restrizione predefinita è un valore pari a 1. Una bitmap con uno dei valori validi seguenti:<br /><br /> 1 Visibile<br /><br /> 2 Non visibile|  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello schema OLE DB per OLAP](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
