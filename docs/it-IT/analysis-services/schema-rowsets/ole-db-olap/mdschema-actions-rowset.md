---
title: Set di righe MDSCHEMA_ACTIONS | Documenti Microsoft
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
- MDSCHEMA_ACTIONS
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- MDSCHEMA_ACTIONS rowset
ms.assetid: f73081f8-ac51-4286-b46e-2b34e792c3e0
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 19423a6d4b8ffe345309032559e733f629358594
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="mdschemaactions-rowset"></a>Set di righe MDSCHEMA_ACTIONS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Descrive le azioni che possono essere disponibili per l'applicazione client.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il **MDSCHEMA_ACTIONS** set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Lunghezza|Description|  
|-----------------|--------------------|------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**||Nome del database.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**||Non supportato. Contiene sempre **VT_NULL**.|  
|**CUBE_NAME**|**DBTYPE_WSTR**||Nome del cubo a cui appartiene questa azione.|  
|**NOME_AZIONE**|**DBTYPE_WSTR**||Nome di questa azione.|  
|**ACTION_TYPE**|**DBTYPE_I4**||Bitmap utilizzata per specificare il metodo di attivazione dell'azione. Nel file Msmd.h sono definite le seguenti costanti del valore bit per questa bitmap:<br /><br /> **MDACTION_TYPE_URL** (**0x01**)<br /><br /> **MDACTION_TYPE_HTML** (**0x02**)<br /><br /> **MDACTION_TYPE_STATEMENT** (**0x04**)<br /><br /> **MDACTION_TYPE_DATASET** (**0x08**)<br /><br /> **MDACTION_TYPE_ROWSET** (**0x10**)<br /><br /> **MDACTION_TYPE_COMMANDLINE** (**0x20**)<br /><br /> **MDACTION_TYPE_PROPRIETARY** (**0x40**)<br /><br /> **MDACTION_TYPE_REPORT** (**0x80**)<br /><br /> **MDACTION_TYPE_DRILLTHROUGH** (**0x100**)|  
|**COORDINATE**|**DBTYPE_WSTR**||Espressione MDX che specifica un oggetto o una coordinata nello spazio multidimensionale in cui viene eseguita l'azione. Il valore di questa colonna di restrizione viene fornito dall'applicazione client.<br /><br /> Il **CORDINATE** deve essere risolto in un oggetto specificato **COORDINATE_TYPE**.|  
|**COORDINATE_TYPE**|**DBTYPE_I4**||Bitmap che specifica il modo in **coordinare** colonna di restrizione viene interpretato. Nel file Msmd.h sono definite le seguenti costanti del valore bit per questa bitmap:<br /><br /> **MDACTION_COORDINATE_CUBE** (**1**)<br /><br /> **MDACTION_COORDINATE_DIMENSION** (**2**): fa riferimento a gerarchie delle dimensioni.<br /><br /> **MDACTION_COORDINATE_LEVEL** (**3**)<br /><br /> **MDACTION_COORDINATE_MEMBER** (**4**)<br /><br /> **MDACTION_COORDINATE_SET** (**5**)<br /><br /> **MDACTION_COORDINATE_CELL** (**6**)|  
|**ACTION_CAPTION**|**DBTYPE_WSTR**||Nome dell'azione se non viene specificata alcuna didascalia né alcuna traduzione in DDL.<br /><br /> Se è sono specificate una didascalia o una traduzione, e **CaptionIsMDX** è false, una delle seguenti stringhe:<br /><br /> -La traduzione per la lingua appropriata.<br /><br /> -La didascalia specificata se è stata trovata alcuna traduzione per la lingua specificata.<br /><br /> -Il nome dell'azione se è stata trovata alcuna traduzione e la didascalia non è stato specificato nell'istruzione DDL.<br /><br /> Se è sono specificate una didascalia o una traduzione, e **CaptionIsMDX** è true, stringa risultante dall'individuazione della traduzione appropriata per la lingua specificata o della traduzione specificata nella didascalia DDL e calcolare il formula per creare la stringa.<br /><br /> Se l'azione è stata specificata nello script MDX, non vi sono traduzioni e la didascalia viene sempre considerata come un'espressione MDX.|  
|**DESCRIPTION**|**DBTYPE_WSTR**||Descrizione semplice dell'azione.|  
|**CONTENT**|**DBTYPE_WSTR**||Espressione o contenuto dell'azione da eseguire.|  
|**APPLICAZIONE**|**DBTYPE_WSTR**||Nome dell'applicazione da utilizzare per eseguire l'azione.|  
|**CHIAMATA**|**DBTYPE_I4**||Informazioni sulla modalità con cui richiamare l'azione:<br /><br /> **MDACTION_INVOCATION_INTERACTIVE** (**1**) indica un'azione regolare utilizzata durante le normali operazioni. È il valore predefinito per questa colonna.<br /><br /> **MDACTION_INVOCATION_ON_OPEN** (**2**) indica che l'azione deve essere eseguita quando si apre il cubo.<br /><br /> **MDACTION_INVOCATION_BATCH** (**4**) indica che l'azione viene eseguita come parte di un'operazione batch o [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] attività.<br /><br /> <br /><br /> Si noti che questi valori di enumerazione sono definiti nel file msmd.|  
  
 Il set di righe viene ordinato in base **CATALOG_NAME**, **SCHEMA_NAME**, **CUBE_NAME**, **nome_azione**.  
  
> [!NOTE]  
>  Azioni di **MDACTION_TYPE_PROPRIETARY** tipo deve fornire un valore per il **applicazione** colonna.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il **MDSCHEMA_ACTIONS** righe può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Facoltativo|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Facoltativo|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Obbligatorio|  
|**NOME_AZIONE**|**DBTYPE_WSTR**|Facoltativo|  
|**ACTION_TYPE**|**DBTYPE_I4**|Facoltativo|  
|**COORDINATE**|**DBTYPE_WSTR**|Obbligatorio|  
|**COORDINATE_TYPE**|**DBTYPE_I4**|Obbligatorio|  
|**CHIAMATA**|**DBTYPE_I4**|(Facoltativo) Il **chiamata** al valore dell'impostazione predefinita della colonna di restrizione **MDACTION_INVOCATION_INTERACTIVE**. Per recuperare tutte le azioni, utilizzare il **MDACTION_INVOCATION_ALL** valore il **chiamata** colonna di restrizione.|  
|**CUBE_SOURCE**|**DBTYPE_UI2**|(Facoltativo) Restrizione predefinita è un valore pari a 1. Una bitmap con uno dei valori validi seguenti:<br /><br /> 1 CUBO<br /><br /> 2 DIMENSIONE|  
  
> [!IMPORTANT]  
>  Il **chiamata** colonna di restrizione ha un valore predefinito di **MDACTION_INVOCATION_INTERACTIVE**. Qualsiasi set di righe dello schema che non specifichi in modo esplicito un valore per questa colonna contiene solo righe con questo valore. Se si desidera il set di righe per contenere l'intero set di azioni, utilizzare il **MDACTION_INVOCATION_ALL** costante nel **chiamata** colonna di restrizione.  
  
 Le applicazioni client è possono definire più **ACTION_TYPE** utilizzando l'operatore OR.  
  
## <a name="remarks"></a>Osservazioni  
 Nella tabella seguente sono elencati validi **coordinare** e **COORDINATE_TYPE** combinazioni.  
  
|Tipo di oggetto COORDINATE|COORDINATE_TYPE|  
|----------------------------|----------------------|  
|**Cube**|**MDACTION_COORDINATE_CUBE**|  
|**Dimensione**|**MDACTION_COORDINATE_DIMENSION**<br /><br /> **MDACTION_COORDINATE_LEVEL**<br /><br /> **MDACTION_COORDINATE_MEMBER**<br /><br /> **MDACTION_COORDINATE_SET**<br /><br /> **MDACTION_COORDINATE_CELL**|  
|**Gerarchia**|**MDACTION_COORDINATE_DIMENSION**|  
|**Level**|**MDACTION_COORDINATE_LEVEL**|  
|**Membro**|**MDACTION_COORDINATE_MEMBER**|  
|**Set**|**MDACTION_COORDINATE_SET**|  
|**Cella**|**MDACTION_COORDINATE_CELL**|  
  
## <a name="see-also"></a>Vedere anche  
 [OLE DB per OLAP i rowset dello Schema](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
