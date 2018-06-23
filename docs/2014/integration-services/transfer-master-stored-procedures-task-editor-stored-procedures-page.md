---
title: Le Stored procedure Editor attività Trasferisci Master (pagina Stored procedure) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.transferstoredprocedurestask.storedprocedures.f1
helpviewer_keywords:
- Transfer Stored Procedures Task Editor
ms.assetid: 5fcf171e-cc0b-4c24-8eb5-3a4b4775e64a
caps.latest.revision: 18
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 2ee8337cfdf090e77c9161600a44d8d6d58d04f1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36169934"
---
# <a name="transfer-master-stored-procedures-task-editor-stored-procedures-page"></a>Editor attività Trasferisci stored procedure master (pagina Stored procedure)
  Usare la pagina **Stored procedure** della finestra di dialogo **Editor attività Trasferisci stored procedure master** per specificare le proprietà per la copia di una o più stored procedure definite dall'utente dal database **master** di un'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] a un database **master** di un'altra istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Per altre informazioni su questa attività, vedere [Attività Trasferisci stored procedure master](control-flow/transfer-master-stored-procedures-task.md).  
  
> [!NOTE]  
>  L'attività consente solo il trasferimento di stored procedure appartenenti a **dbo** da un database **master** del server di origine a un database **master** del server di destinazione. Per poter creare stored procedure nel server di destinazione, gli utenti devono disporre dell'autorizzazione CREATE PROCEDURE nel database **master** del server di destinazione o essere membri del ruolo predefinito del server **sysadmin** nel server di destinazione.  
  
## <a name="options"></a>Opzioni  
 **SourceConnection**  
 Selezionare una gestione connessione SMO nell'elenco o fare clic su **\<Nuova connessione...>** per creare una nuova connessione al server di origine.  
  
 **DestinationConnection**  
 Selezionare una gestione connessione SMO nell'elenco o fare clic su **Nuova connessione...>\<** per creare una nuova connessione al server di destinazione.  
  
 **IfObjectExists**  
 Selezionare la modalità con cui l'attività deve gestire le stored procedure definite dall'utente che hanno lo stesso nome di stored procedure già esistenti nel database **master** del server di destinazione.  
  
 Per questa proprietà sono disponibili le opzioni elencate nella tabella seguente:  
  
|valore|Description|  
|-----------|-----------------|  
|**FailTask**|L'attività viene interrotta se nel database **master** del server di destinazione esistono già stored procedure con lo stesso nome.|  
|**Overwrite**|L'attività sovrascrive le stored procedure con lo stesso nome presenti nel database **master** del server di destinazione.|  
|**Skip**|L'attività ignora le stored procedure con lo stesso nome presenti nel database **master** del server di destinazione.|  
  
 **TransferAllStoredProcedures**  
 Selezionare un valore per indicare se nel server di destinazione debbano essere copiate tutte le stored procedure definite dall'utente nel database **master** del server di origine.  
  
|valore|Description|  
|-----------|-----------------|  
|**True**|Copia tutte le stored procedure definite dall'utente nel database **master** .|  
|**False**|Copia solo le stored procedure specificate.|  
  
 **StoredProceduresList**  
 Selezionare le stored procedure definite dall'utente nel database **master** del server di origine da copiare nel database **master** del server di destinazione. Questa opzione è disponibile solo quando la proprietà **TransferAllStoredProcedures** è impostata su **False**.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti per i messaggi e agli errori di Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Attività di Integration Services](control-flow/integration-services-tasks.md)   
 [Le Stored procedure Editor attività Trasferisci Master &#40;pagina Generale&#41;](general-page-of-integration-services-designers-options.md)   
 [Pagina espressioni](expressions/expressions-page.md)   
 [Gestione connessione SMO](connection-manager/smo-connection-manager.md)  
  
  