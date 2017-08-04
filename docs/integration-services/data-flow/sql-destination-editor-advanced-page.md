---
title: Editor destinazione SQL Server (pagina avanzate) | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.sqlserverdestadapter.advanced.f1
helpviewer_keywords:
- SQL Server Destination Editor
ms.assetid: 9b46bcf8-ddaf-4d7d-90a6-80bc19517e9b
caps.latest.revision: 28
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e279b5bc6ff340323647d1a93daeb006ec4c3cbf
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="sql-destination-editor-advanced-page"></a>Editor destinazione SQL Server (pagina Avanzate)
  Usare la pagina **Avanzate** della finestra di dialogo **Editor destinazione SQL** per specificare le opzioni di inserimento bulk avanzate.  
  
 Per ulteriori informazioni sulla destinazione SQL Server, vedere [SQL Server Destination](../../integration-services/data-flow/sql-server-destination.md).  
  
## <a name="options"></a>Opzioni  
 **Mantieni valori Identity**  
 Consente di specificare se l'attività deve inserire valori nelle colonne Identity. Il valore predefinito di questa proprietà è **False**.  
  
 **Mantieni valori Null**  
 Consente di specificare se l'attività deve mantenere i valori Null. Il valore predefinito di questa proprietà è **False**.  
  
 **Blocco a livello di tabella**  
 Consente di specificare se la tabella viene bloccata durante il caricamento dei dati. Il valore predefinito di questa proprietà è **True**.  
  
 **Vincoli CHECK**  
 Consente di specificare se l'attività deve verificare i vincoli. Il valore predefinito di questa proprietà è **True**.  
  
 **Attive trigger**  
 Consente di specificare se l'inserimento bulk deve attivare i trigger nelle tabelle. Il valore predefinito di questa proprietà è **False**.  
  
 **Prima riga**  
 Consente di specificare la prima riga da inserire. Il valore predefinito della proprietà è **-1**, a indicare che non è stato assegnato alcun valore.  
  
> [!NOTE]  
>  Deselezionare la casella in **Editor destinazione SQL** per indicare che non si vuole assegnare alcun valore alla proprietà. Usare -1 nella finestra **Proprietà** , in **Editor avanzato**e nel modello a oggetti.  
  
 **Ultima riga**  
 Consente di specificare l'ultima riga da inserire. Il valore predefinito della proprietà è **-1**, a indicare che non è stato assegnato alcun valore.  
  
> [!NOTE]  
>  Deselezionare la casella in **Editor destinazione SQL** per indicare che non si vuole assegnare alcun valore alla proprietà. Usare -1 nella finestra **Proprietà** , in **Editor avanzato**e nel modello a oggetti.  
  
 **Numero massimo di errori**  
 Consente di specificare il numero massimo di errori che possono verificarsi prima dell'arresto dell'inserimento bulk. Il valore predefinito della proprietà è **-1**, a indicare che non è stato assegnato alcun valore.  
  
> [!NOTE]  
>  Deselezionare la casella in **Editor destinazione SQL** per indicare che non si vuole assegnare alcun valore alla proprietà. Usare -1 nella finestra **Proprietà** , in **Editor avanzato**e nel modello a oggetti.  
  
 **Timeout**  
 Consente di specificare il numero di secondi di attesa prima che l'inserimento bulk venga arrestato a causa di un timeout.  
  
 **Colonne di ordinamento**  
 Consente di digitare i nomi delle colonne di ordinamento. È possibile ordinare ogni colonna in ordine crescente o decrescente. Se si utilizzando più colonne di ordinamento, delimitare l'elenco con virgole.  
  
## <a name="see-also"></a>Vedere anche  
 [Errori di Integration Services e riferimento ai messaggi](../../integration-services/integration-services-error-and-message-reference.md)   
 [Editor destinazione SQL Server &#40; Pagina Gestione connessione &#41;](../../integration-services/data-flow/sql-destination-editor-connection-manager-page.md)   
 [Editor destinazione SQL Server &#40; Pagina mapping &#41;](../../integration-services/data-flow/sql-destination-editor-mappings-page.md)   
 [Caricamento bulk dei dati tramite la destinazione di SQL Server](../../integration-services/data-flow/bulk-load-data-by-using-the-sql-server-destination.md)  
  
  
