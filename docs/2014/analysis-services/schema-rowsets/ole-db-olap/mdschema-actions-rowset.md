---
title: Set di righe MDSCHEMA_ACTIONS | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MDSCHEMA_ACTIONS
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_ACTIONS rowset
ms.assetid: f73081f8-ac51-4286-b46e-2b34e792c3e0
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 317ddc9a284df779a44866c0c037310b29f76d02
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48140727"
---
# <a name="mdschemaactions-rowset"></a>Set di righe MDSCHEMA_ACTIONS
  Descrive le azioni che possono essere disponibili per l'applicazione client.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il `MDSCHEMA_ACTIONS` set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Length|Description|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||Nome del database.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||Non supportato. Contiene sempre `VT_NULL`.|  
|`CUBE_NAME`|`DBTYPE_WSTR`||Nome del cubo a cui appartiene questa azione.|  
|`ACTION_NAME`|`DBTYPE_WSTR`||Nome di questa azione.|  
|`ACTION_TYPE`|`DBTYPE_I4`||Bitmap utilizzata per specificare il metodo di attivazione dell'azione. Nel file Msmd.h sono definite le seguenti costanti del valore bit per questa bitmap:<br /><br /> -   `MDACTION_TYPE_URL` (`0x01`)<br />-   `MDACTION_TYPE_HTML` (`0x02`)<br />-   `MDACTION_TYPE_STATEMENT` (`0x04`)<br />-   `MDACTION_TYPE_DATASET` (`0x08`)<br />-   `MDACTION_TYPE_ROWSET` (`0x10`)<br />-   `MDACTION_TYPE_COMMANDLINE` (`0x20`)<br />-   `MDACTION_TYPE_PROPRIETARY` (`0x40`)<br />-   `MDACTION_TYPE_REPORT` (`0x80`)<br />-   `MDACTION_TYPE_DRILLTHROUGH` (`0x100`)|  
|`COORDINATE`|`DBTYPE_WSTR`||Espressione MDX che specifica un oggetto o una coordinata nello spazio multidimensionale in cui viene eseguita l'azione. Il valore di questa colonna di restrizione viene fornito dall'applicazione client.<br /><br /> `CORDINATE` deve essere risolto in un oggetto specificato in `COORDINATE_TYPE`.|  
|`COORDINATE_TYPE`|`DBTYPE_I4`||Bitmap che specifica come viene interpretata la colonna di restrizione `COORDINATE`. Nel file Msmd.h sono definite le seguenti costanti del valore bit per questa bitmap:<br /><br /> -   `MDACTION_COORDINATE_CUBE` (`1`)<br />-   `MDACTION_COORDINATE_DIMENSION` (`2`)<br />     fa riferimento alle gerarchie delle dimensioni.<br />-   `MDACTION_COORDINATE_LEVEL` (`3`)<br />-   `MDACTION_COORDINATE_MEMBER` (`4`)<br />-   `MDACTION_COORDINATE_SET` (`5`)<br />-   `MDACTION_COORDINATE_CELL` (`6`)|  
|`ACTION_CAPTION`|`DBTYPE_WSTR`||Nome dell'azione se non viene specificata alcuna didascalia né alcuna traduzione in DDL.<br /><br /> Se viene specificata una didascalia o una traduzione e `CaptionIsMDX` è false, una delle seguenti stringhe:<br /><br /> -La traduzione per la lingua appropriata.<br />-La didascalia specificata se è stata trovata alcuna traduzione per la lingua specificata.<br />-Il nome dell'azione se è stata trovata alcuna traduzione e la didascalia non è stato specificato nell'istruzione DDL.<br /><br /> Se viene specificata una didascalia o una traduzione e `CaptionIsMDX` è true, stringa risultante dall'individuazione della traduzione appropriata per la lingua specificata o della traduzione specificata nella didascalia DDL e dal calcolo della formula per creare la stringa.<br /><br /> Se l'azione è stata specificata nello script MDX, non vi sono traduzioni e la didascalia viene sempre considerata come un'espressione MDX.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Descrizione semplice dell'azione.|  
|`CONTENT`|`DBTYPE_WSTR`||Espressione o contenuto dell'azione da eseguire.|  
|`APPLICATION`|`DBTYPE_WSTR`||Nome dell'applicazione da utilizzare per eseguire l'azione.|  
|`INVOCATION`|`DBTYPE_I4`||Informazioni sulla modalità con cui richiamare l'azione:<br /><br /> -   `MDACTION_INVOCATION_INTERACTIVE` (`1`) indica un'azione regolare utilizzata durante il normale funzionamento. È il valore predefinito per questa colonna.<br />-   `MDACTION_INVOCATION_ON_OPEN` (`2`) indica che l'azione deve essere eseguita quando si apre la prima volta il cubo.<br />-   `MDACTION_INVOCATION_BATCH` (`4`) indica che l'azione viene eseguita come parte di un'operazione batch o [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] attività.<br /><br /> Questi valori di enumerazione sono definiti nel file Msmd.h.|  
  
 Il set di righe viene ordinato in base a `CATALOG_NAME`, `SCHEMA_NAME`, `CUBE_NAME` e `ACTION_NAME`.  
  
> [!NOTE]  
>  Le azioni di tipo `MDACTION_TYPE_PROPRIETARY` devono fornire un valore per la colonna `APPLICATION`.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il set di righe `MDSCHEMA_ACTIONS` può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Facoltativo|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|Facoltativo|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Obbligatorio|  
|`ACTION_NAME`|`DBTYPE_WSTR`|Facoltativo|  
|`ACTION_TYPE`|`DBTYPE_I4`|Facoltativo|  
|`COORDINATE`|`DBTYPE_WSTR`|Obbligatorio|  
|`COORDINATE_TYPE`|`DBTYPE_I4`|Obbligatorio|  
|`INVOCATION`|`DBTYPE_I4`|(Facoltativo) L'impostazione predefinita della colonna di restrizione `INVOCATION` è il valore di `MDACTION_INVOCATION_INTERACTIVE`. Per recuperare tutte le azioni, utilizzare il valore `MDACTION_INVOCATION_ALL` nella colonna di restrizione `INVOCATION`.|  
|`CUBE_SOURCE`|`DBTYPE_UI2`|(Facoltativo) Bitmap con uno dei seguenti valori validi:<br /><br /> -1 CUBO<br />-DIMENSIONE DI 2<br /><br /> La restrizione predefinita è impostata sul valore 1.|  
  
> [!IMPORTANT]  
>  Il valore predefinito della colonna di restrizione `INVOCATION` è `MDACTION_INVOCATION_INTERACTIVE`. Qualsiasi set di righe dello schema che non specifichi in modo esplicito un valore per questa colonna contiene solo righe con questo valore. Se si desidera che il set di righe contenga l'intero set di azioni, utilizzare la costante `MDACTION_INVOCATION_ALL` nella colonna di restrizione `INVOCATION`.  
  
 Nelle applicazioni client è possibile definire più `ACTION_TYPE` tramite l'operatore OR.  
  
## <a name="remarks"></a>Note  
 Nella tabella seguente vengono elencate le combinazioni di `COORDINATE` e `COORDINATE_TYPE` valide.  
  
|Tipo di oggetto COORDINATE|COORDINATE_TYPE|  
|----------------------------|----------------------|  
|`Cube`|`MDACTION_COORDINATE_CUBE`|  
|`Dimension`|`MDACTION_COORDINATE_DIMENSION`<br /><br /> `MDACTION_COORDINATE_LEVEL`<br /><br /> `MDACTION_COORDINATE_MEMBER`<br /><br /> `MDACTION_COORDINATE_SET`<br /><br /> `MDACTION_COORDINATE_CELL`|  
|`Hierarchy`|`MDACTION_COORDINATE_DIMENSION`|  
|`Level`|`MDACTION_COORDINATE_LEVEL`|  
|`Member`|`MDACTION_COORDINATE_MEMBER`|  
|`Set`|`MDACTION_COORDINATE_SET`|  
|`cell`|`MDACTION_COORDINATE_CELL`|  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello schema OLE DB per OLAP](ole-db-for-olap-schema-rowsets.md)  
  
  
