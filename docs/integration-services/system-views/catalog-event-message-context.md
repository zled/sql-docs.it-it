---
title: Catalog.event_message_context | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 273a54f8-b107-4f36-9461-2b475644760d
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: b7aeb07c52f7ed00aa5a6a29cdd054258cb62d65
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="catalogeventmessagecontext"></a>catalog.event_message_context
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Visualizza le informazioni sulle condizioni associate ai messaggi di evento di esecuzione, per le esecuzioni nel server [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|Context_id|bigint|ID univoco per il contesto dell'errore.|  
|Event_message_id|bigint|ID univoco per il messaggio a cui è correlato il contesto.|  
|Context_depth|int|Con l'aumentare della profondità, il contesto è più lontano dall'errore. Quando si verifica un errore, la profondità del contesto parte da 1. Il valore 0 indica lo stato del pacchetto prima dell'avvio dell'esecuzione.|  
|Package_path|Nvarchar(max)|Percorso del pacchetto per l'origine del contesto.|  
|Context_type|smallint|Tipo dell'oggetto che rappresenta l'origine del contesto. Vedere il **osservazioni** sezione per un elenco di tipi di contesto.|  
|Context_source_name|Nvarchar(4000)|Nome dell'oggetto che rappresenta l'origine del contesto.|  
|Context_source_id|nvarchar(38)|ID univoco dell'oggetto che rappresenta l'origine del contesto.|  
|Property_name|Nvarchar(4000)|Nome della proprietà associata all'origine del contesto.|  
|Property_value|Sql_variant|Valore della proprietà associata all'origine del contesto.|  
  
## <a name="remarks"></a>Osservazioni  
 Nella tabella seguente sono elencati i tipi di contesto.  
  
||||  
|-|-|-|  
|Valore tipo di contesto|Nome tipo|Description|  
|10|Attività|Stato di un'attività nel momento in cui si è verificato un errore.|  
|20|Pipeline|Errore è stato generato da un componente della pipeline: componente di trasformazione, origine o destinazione.|  
|30|Sequenza|Stato di una sequenza.|  
|40|Ciclo For|Stato di un ciclo For|  
|50|Ciclo Foreach|Stato di un ciclo Foreach|  
|60|Pacchetto|Stato del pacchetto nel momento in cui si è verificato un errore.|  
|70|Variabile|Valore di variabile|  
|80|Gestione connessione|Proprietà di una gestione connessione.|  
  
## <a name="permissions"></a>Permissions  
 Per questa vista è necessaria una delle autorizzazioni seguenti:  
  
-   Autorizzazione READ per l'operazione  
  
-   L'appartenenza al **ssis_admin** ruolo del database.  
  
-   L'appartenenza al **sysadmin** ruolo del server.  
  
  
