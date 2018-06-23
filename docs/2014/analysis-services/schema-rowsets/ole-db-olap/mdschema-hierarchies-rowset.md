---
title: Set di righe MDSCHEMA_HIERARCHIES | Documenti Microsoft
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
- MDSCHEMA_HIERARCHIES
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_HIERARCHIES rowset
ms.assetid: 2e5b2a81-366e-4d5b-af1e-1d372bf596d9
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: e8c6fa75c935256235d64ad337500923b5974c68
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36069504"
---
# <a name="mdschemahierarchies-rowset"></a>Set di righe MDSCHEMA_HIERARCHIES
  Descrive ogni gerarchia all'interno di una determinata dimensione.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il `MDSCHEMA_HIERARCHIES` set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Length|Description|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||Nome del catalogo a cui appartiene questa gerarchia. `NULL` se il provider non supporta i cataloghi.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||Non supportato|  
|`CUBE_NAME`|`DBTYPE_WSTR`||(Obbligatorio) Nome del cubo a cui appartiene questa gerarchia.|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`||Nome univoco della dimensione a cui appartiene questa gerarchia. Per i provider che generano nomi univoci tramite qualificazione, i singoli componenti di tale nome sono delimitati.|  
|`HIERARCHY_NAME`|`DBTYPE_WSTR`||Il nome della gerarchia. Vuoto se è presente una sola gerarchia nella dimensione. Ciò avrà sempre un valore [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|`HIERARCHY_UNIQUE_NAME`|`DBTYPE_WSTR`||Nome univoco della gerarchia.|  
|`HIERARCHY_GUID`|`DBTYPE_GUID`||Non supportato|  
|`HIERARCHY_CAPTION`|`DBTYPE_WSTR`||Etichetta o didascalia associata alla gerarchia. Utilizzata principalmente a scopo di visualizzazione. Se non esiste una didascalia, viene restituito `HIERARCHY_NAME`. Se la dimensione non contiene una gerarchia o dispone di una sola gerarchia, questa colonna conterrà il nome della dimensione.|  
|`DIMENSION_TYPE`|`DBTYPE_I2`||Tipo della dimensione. Tra i valori validi sono inclusi i seguenti:<br /><br /> -   `MD_DIMTYPE_UNKNOWN` (`0`)<br />-   `MD_DIMTYPE_TIME` (`1`)<br />-   `MD_DIMTYPE_MEASURE` (`2`)<br />-   `MD_DIMTYPE_OTHER` (`3`)<br />-   `MD_DIMTYPE_QUANTITATIVE` (`5`)<br />-   `MD_DIMTYPE_ACCOUNTS` (`6`)<br />-   `MD_DIMTYPE_CUSTOMERS` (`7`)<br />-   `MD_DIMTYPE_PRODUCTS` (`8`)<br />-   `MD_DIMTYPE_SCENARIO` (`9`)<br />-   `MD_DIMTYPE_UTILIY` (`10`)<br />-   `MD_DIMTYPE_CURRENCY` (`11`)<br />-   `MD_DIMTYPE_RATES` (`12`)<br />-   `MD_DIMTYPE_CHANNEL` (`13`)<br />-   `MD_DIMTYPE_PROMOTION` (`14`)<br />-   `MD_DIMTYPE_ORGANIZATION` (`15`)<br />-   `MD_DIMTYPE_BILL_OF_MATERIALS` (`16`)<br />-   `MD_DIMTYPE_GEOGRAPHY` (`17`)|  
|`HIERARCHY_CARDINALITY`|`DBTYPE_UI4`||Numero di membri nella gerarchia.|  
|`DEFAULT_MEMBER`|`DBTYPE_WSTR`||Membro predefinito per questa gerarchia. Si tratta di un nome univoco. È necessario che ogni gerarchia disponga di un membro predefinito.|  
|`ALL_MEMBER`|`DBTYPE_WSTR`||Membro al livello più elevato del rollup.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Descrizione leggibile della gerarchia. `NULL` se non sono presenti descrizioni.|  
|`STRUCTURE`|`DBTYPE_I2`||Struttura della gerarchia. Tra i valori validi sono inclusi i seguenti:<br /><br /> -   `MD_STRUCTURE_FULLYBALANCED` (`0`)<br />-   `MD_STRUCTURE_RAGGEDBALANCED` (`1`)<br />-   `MD_STRUCTURE_UNBALANCED` (`2`)<br />-   `MD_STRUCTURE_NETWORK` (`3`)|  
|`IS_VIRTUAL`|`DBTYPE_BOOL`||Restituisce sempre `False`.|  
|`IS_READWRITE`|`DBTYPE_BOOL`||Valore booleano che indica se il writeback nella colonna delle dimensioni è abilitato.<br /><br /> Viene restituito `TRUE` se la colonna `Write Back to dimension` che rappresenta questa gerarchia è abilitata.|  
|`DIMENSION_UNIQUE_SETTINGS`|`DBTYPE_I4`||Viene sempre restituito `MDDIMENSIONS_MEMBER_KEY_UNIQUE` (`1`).|  
|`DIMENSION_MASTER_UNIQUE_NAME`|`DBTYPE_WSTR`||Restituisce sempre `NULL`.|  
|`DIMENSION_IS_VISIBLE`|`DBTYPE_BOOL`||Restituisce sempre `true`. Se la dimensione non è visibile, non verrà visualizzata nel set di righe dello schema.|  
|`HIERARCHY_ORDINAL`|`DBTYPE_UI4`||Numero ordinale della gerarchia tra tutte le gerarchie del cubo.|  
|`DIMENSION_IS_SHARED`|`DBTYPE_BOOL`||Restituisce sempre `TRUE`.|  
|`HIERARCHY_IS_VISIBLE`|`DBTYPE_BOOL`||Valore booleano che indica se la gerarchia è visibile.<br /><br /> Restituisce `TRUE` se la gerarchia è visibile; altrimenti restituisce `FALSE`.|  
|`HIERARCHY_ORIGIN`|`DBTYPE_UI2`||Maschera di bit che determina l'origine della gerarchia:<br /><br /> -   `MD_USER_DEFINED` Identifica le gerarchie definite dall'utente e ha un valore di `0x0000001`.<br />-   `MD_SYSTEM_ENABLED` Identifica le gerarchie di attributi e ha un valore di `0x0000002`.<br />-   `MD_SYSTEM_INTERNAL` Identifica gli attributi senza gerarchie e ha il valore **0x0000004**.<br /><br /> Una gerarchia dell'attributo padre/figlio è sia `MD_USER_DEFINED` sia `MD_SYSTEM_ENABLED`.|  
|`HIERARCHY_DISPLAY_FOLDER`|`DBTYPE_WSTR`||Il percorso da utilizzare durante la visualizzazione della gerarchia nell'interfaccia utente. I nomi delle cartelle saranno separati da un punto e virgola (;). Le cartelle nidificate sono indicate da una barra rovesciata (\\).|  
|`INSTANCE_SELECTION`|`DBTYPE_UI2`||Hint per l'applicazione client relativo alla modalità di visualizzazione della gerarchia. Tra i valori validi sono inclusi i seguenti:<br /><br /> -   `MD_INSTANCE_SELECTION_NONE`<br />-   `MD_INSTANCE_SELECTION_DROPDOWN`<br />-   `MD_INSTANCE_SELECTION_LIST`<br />-   `MD_INSTANCE_SELECTION_FILTEREDLIST`<br />-   `MD_INSTANCE_SELECTION_MANDATORYFILTER`|  
|`GROUPING_BEHAVIOR`|`DBTYPE_I2`||Enumerazione tramite cui viene specificato il comportamento di raggruppamento previsto dei client per questa gerarchia. Di seguito sono indicati i valori possibili:<br /><br /> -   **EncourageGrouping** (1)<br />-   **DiscourageGrouping** (2)|  
|`STRUCTURE_TYPE`|`DBTYPE_WSTR`||Indica il tipo di gerarchia. Tra i valori validi sono inclusi i seguenti:<br /><br /> -   `Natural`<br />-   `Unnatural`<br />-   `Unknown`|  
  
 Il set di righe viene ordinato in base a `CATALOG_NAME`, `SCHEMA_NAME`, `CUBE_NAME`, `DIMENSION_UNIQUE_NAME`, `HIERARCHY_NAME`.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il set di righe `MDSCHEMA_HIERARCHIES` può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`HIERARCHY_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`HIERARCHY_UNIQUE_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`HIERARCHY_ORIGIN`|`DBTYPE_UI2`|(Facoltativo) Una restrizione predefinita è attiva su MD_USER_DEFINED e MD_SYSTEM_ENABLED.|  
|`CUBE_SOURCE`|`DBTYPE_UI2`|(Facoltativo) Bitmap con uno dei seguenti valori validi:<br /><br /> -1 CUBO<br />-QUOTA 2<br /><br /> La restrizione predefinita è impostata sul valore 1.|  
|`HIERARCHY_VISIBILITY`|`DBTYPE_UI2`|(Facoltativo) Bitmap con uno dei seguenti valori validi:<br /><br /> -Visible 1<br />-2 non visibile<br /><br /> La restrizione predefinita è impostata sul valore 1.|  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello schema OLE DB per OLAP](ole-db-for-olap-schema-rowsets.md)  
  
  