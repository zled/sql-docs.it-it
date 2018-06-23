---
title: File di origine Editor flat (pagina colonne) | Documenti Microsoft
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
- sql12.dts.designer.flatfilesourceadapter.columns.f1
helpviewer_keywords:
- Flat File Source Editor
ms.assetid: b5af5f65-c087-44fd-b5ae-d0441245fef2
caps.latest.revision: 28
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 3be667dc6fe7dcaefdc183a831f762a566a56c99
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36067841"
---
# <a name="flat-file-source-editor-columns-page"></a>Editor origine file flat (pagina Colonne)
  Usare il nodo **Colonne** della finestra di dialogo **Editor origine file flat** per eseguire il mapping tra una colonna di output e ogni colonna esterna (di origine).  
  
> [!NOTE]  
>  Il `FileNameColumnName` proprietà dell'origine File Flat e il `FastParse` proprietà delle colonne di output non sono disponibili nel **Editor origine File Flat**, ma può essere impostata tramite il **Editor avanzato** . Per ulteriori informazioni su queste proprietà, vedere la sezione relativa all'origine file flat in [Flat File Custom Properties](data-flow/flat-file-custom-properties.md).  
  
 Per ulteriori informazioni sull'origine file flat, vedere [Flat File Source](data-flow/flat-file-source.md).  
  
## <a name="options"></a>Opzioni  
 **Colonne esterne disponibili**  
 Consente di visualizzare l'elenco delle colonne esterne disponibili nell'origine dei dati. Non è possibile utilizzare questa tabella per l'aggiunta o l'eliminazione di colonne.  
  
 **Colonna esterna**  
 Consente di visualizzare le colonne esterne (origine) nell'ordine in cui verranno lette dall'attività. È possibile modificare l'ordine deselezionando innanzitutto le colonne della tabella selezionate e quindi selezionando dall'elenco le colonne esterne in un ordine diverso.  
  
 **Colonna di output**  
 Consente di specificare un nome univoco per ogni colonna di output. Per impostazione predefinita viene suggerito il nome della colonna esterna (di origine) selezionata. È comunque possibile scegliere qualsiasi nome descrittivo univoco. Il nome specificato verrà visualizzato in Progettazione [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti per i messaggi e agli errori di Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Editor origine File flat &#40;pagina Gestione connessione&#41;](../../2014/integration-services/flat-file-source-editor-connection-manager-page.md)   
 [Editor origine File flat &#40;pagina di Output di errore&#41;](../../2014/integration-services/flat-file-source-editor-error-output-page.md)   
 [Gestione connessione file flat](connection-manager/file-connection-manager.md)  
  
  