---
title: Catalog. operation_messages (Database SSISDB) | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- catalog.operation_messages view [Integration Services]
- operation_messages view [Integration Services]
ms.assetid: 0b3cbe38-ce24-47ca-83ef-6538a5299d1a
caps.latest.revision: 27
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 235e9896cbf075bdc26e3df120b23091b8e82d6d
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="catalogoperationmessages-ssisdb-database"></a>catalog.operation_messages (database SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Vengono visualizzati i messaggi registrati durante le operazioni nel catalogo di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|operation_message_id|**bigint**|Identificatore (ID) univoco del messaggio.|  
|operation_id|**bigint**|ID univoco dell'operazione.|  
|message_time|**DateTimeOffset(7)**|Ora di creazione del messaggio.|  
|message_type|**smallint**|Tipo di messaggio visualizzato.|  
|message_source_type|**smallint**|L'ID del tipo di origine del messaggio.|  
|message|**nvarchar(max)**|Testo del messaggio.|  
|extended_info_id|**bigint**|L'ID di informazioni aggiuntive correlate al messaggio dell'operazione, vedere il [extended_operation_info](../../integration-services/system-views/catalog-extended-operation-info-ssisdb-database.md) visualizzazione.|  
  
## <a name="remarks"></a>Osservazioni  
 In questa vista viene visualizzata una riga per ogni messaggio registrato durante un'operazione nel catalogo. Il messaggio può essere generato dal server, dal processo di esecuzione del pacchetto o dal motore di esecuzione.  
  
 In questa vista vengono visualizzati i tipi di messaggio seguenti:  
  
|**message_type** valore|Description|  
|-----------------------------|-----------------|  
|-1|Unknown|  
|120|Errore|  
|110|Avviso|  
|70|Informazioni|  
|10|Pre-convalida|  
|20|Post-convalida|  
|30|Pre-execute|  
|40|Post-execute|  
|60|Progress|  
|50|StatusChange|  
|100|QueryCancel|  
|130|TaskFailed|  
|90|Diagnostic|  
|200|Custom|  
|140|DiagnosticEx<br /><br /> Ogni volta che un'attività Esegui pacchetto esegue un pacchetto figlio, l'evento viene registrato. Il messaggio di evento include i valori dei parametri passati ai pacchetti figlio.<br /><br /> Il valore della colonna di messaggio per DiagnosticEx è Testo XML.|  
|400|NonDiagnostic|  
|80|VariableValueChanged|  
  
 In questa vista vengono visualizzati i tipi di origine del messaggio seguenti.  
  
|**message_source_type**|Description|  
|-------------------------------|-----------------|  
|10|API della voce, ad esempio stored procedure CLR e T-SQL|  
|20|Processo esterno utilizzato per eseguire il pacchetto (ISServerExec.exe)|  
|30|Oggetti a livello di pacchetto|  
|40|Attività Flusso di controllo|  
|50|Contenitori del flusso di controllo|  
|60|Attività Flusso di dati|  
  
## <a name="permissions"></a>Permissions  
 Per questa vista è necessaria una delle autorizzazioni seguenti:  
  
-   Autorizzazione READ per l'operazione  
  
-   L'appartenenza al **ssis_admin** ruolo del database  
  
-   L'appartenenza al **sysadmin** ruolo del server  
  
> [!NOTE]  
>  Quando si dispone delle autorizzazioni per eseguire un'operazione nel server, si dispone anche delle autorizzazioni per visualizzare le informazioni sull'operazione. È applicata la sicurezza a livello di riga, pertanto vengono visualizzate solo le righe per le quali si dispone delle autorizzazioni per la visualizzazione.  
  
  
