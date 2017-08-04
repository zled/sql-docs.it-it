---
title: Editor trasformazione Esportazione colonna (pagina colonne) | Documenti Microsoft
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
- sql13.dts.designer.fileextractortransformation.columns.f1
helpviewer_keywords:
- Export Column Transformation Editor
ms.assetid: b659a5c2-5509-4b5b-9c82-136c971d5c7f
caps.latest.revision: 28
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e3538e9379c48faaa700f56aa1ecf0ceafc68e2a
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="export-column-transformation-editor-columns-page"></a>Editor trasformazione Esportazione colonna (pagina Colonne)
  Utilizzare la pagina **Colonne** della finestra di dialogo **Editor trasformazione Esportazione colonna** per specificare le colonne nel flusso di dati da estrarre in file. È possibile indicare se la trasformazione Esporta colonna deve accodare i dati a un file oppure sovrascrivere un file esistente.  
  
 Per ulteriori informazioni sulla trasformazione Esportazione colonna, vedere [Export Column Transformation](../../../integration-services/data-flow/transformations/export-column-transformation.md).  
  
## <a name="options"></a>Opzioni  
 **Colonna estrazione**  
 Consente di eseguire una selezione dall'elenco di colonne di input contenenti dati di tipo text o image. In tutte le righe devono essere presenti definizioni per **Colonna estrazione** e **Colonna percorso file**.  
  
 **Colonna percorso file**  
 Consente di eseguire una selezione dall'elenco di colonne di input contenenti nomi e percorsi di file. In tutte le righe devono essere presenti definizioni per **Colonna estrazione** e **Colonna percorso file**.  
  
 **Consenti accodamento**  
 Consente di indicare se la trasformazione accoderà i dati ai file esistenti. Il valore predefinito è **false**.  
  
 **Forza troncamento**  
 Consente di indicare se la trasformazione eliminerà il contenuto di file esistenti prima di scrivere i dati. Il valore predefinito è **false**.  
  
 **Scrivi indicatore ordine byte**  
 Consente di specificare se scrivere un indicatore ordine byte (BOM) nel file. L'indicatore dell'ordine dei byte viene scritto solo se i dati hanno il tipo di dati **DT_NTEXT** o DT_WSTR e non sono accodati a un file di dati esistente.  
  
## <a name="see-also"></a>Vedere anche  
 [Errori di Integration Services e riferimento ai messaggi](../../../integration-services/integration-services-error-and-message-reference.md)   
 [Editor di trasformazione Esportazione colonna &#40; Pagina Output degli errori &#41;](../../../integration-services/data-flow/transformations/export-column-transformation-editor-error-output-page.md)  
  
  
