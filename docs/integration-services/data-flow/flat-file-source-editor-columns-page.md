---
title: File di origine Editor flat (pagina colonne) | Documenti Microsoft
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
- sql13.dts.designer.flatfilesourceadapter.columns.f1
helpviewer_keywords:
- Flat File Source Editor
ms.assetid: b5af5f65-c087-44fd-b5ae-d0441245fef2
caps.latest.revision: 28
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: a34e304d72b80412f5527dcb75f00b6dcb2fcbb2
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="flat-file-source-editor-columns-page"></a>Editor origine file flat (pagina Colonne)
  Usare il nodo **Colonne** della finestra di dialogo **Editor origine file flat** per eseguire il mapping tra una colonna di output e ogni colonna esterna (di origine).  
  
> [!NOTE]  
>  La proprietà **FileNameColumnName** dell'origine file flat e la proprietà **FastParse** delle relative colonne di output non sono disponibili nell' **Editor origine file flat**, tuttavia possono essere impostate utilizzando l' **Editor avanzato**. Per ulteriori informazioni su queste proprietà, vedere la sezione relativa all'origine file flat in [Flat File Custom Properties](../../integration-services/data-flow/flat-file-custom-properties.md).  
  
 Per ulteriori informazioni sull'origine file flat, vedere [Flat File Source](../../integration-services/data-flow/flat-file-source.md).  
  
## <a name="options"></a>Opzioni  
 **Colonne esterne disponibili**  
 Consente di visualizzare l'elenco delle colonne esterne disponibili nell'origine dei dati. Non è possibile utilizzare questa tabella per l'aggiunta o l'eliminazione di colonne.  
  
 **Colonna esterna**  
 Consente di visualizzare le colonne esterne (origine) nell'ordine in cui verranno lette dall'attività. È possibile modificare l'ordine deselezionando innanzitutto le colonne della tabella selezionate e quindi selezionando dall'elenco le colonne esterne in un ordine diverso.  
  
 **Colonna di output**  
 Consente di specificare un nome univoco per ogni colonna di output. Per impostazione predefinita viene suggerito il nome della colonna esterna (di origine) selezionata. È comunque possibile scegliere qualsiasi nome descrittivo univoco. Il nome specificato verrà visualizzato in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
## <a name="see-also"></a>Vedere anche  
 [Errori di Integration Services e riferimento ai messaggi](../../integration-services/integration-services-error-and-message-reference.md)   
 [Editor origine File flat &#40; Pagina Gestione connessione &#41;](../../integration-services/data-flow/flat-file-source-editor-connection-manager-page.md)   
 [Editor origine File flat &#40; Pagina Output degli errori &#41;](../../integration-services/data-flow/flat-file-source-editor-error-output-page.md)   
 [Gestione connessione File flat](../../integration-services/connection-manager/flat-file-connection-manager.md)  
  
  
