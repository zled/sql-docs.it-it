---
title: Editor trasformazione Esportazione colonna (pagina colonne) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fileextractortransformation.columns.f1
helpviewer_keywords:
- Export Column Transformation Editor
ms.assetid: b659a5c2-5509-4b5b-9c82-136c971d5c7f
caps.latest.revision: 28
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b427d8a727f0db31b63d43efbe00378c7ef0f18b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37207451"
---
# <a name="export-column-transformation-editor-columns-page"></a>Editor trasformazione Esportazione colonna (pagina Colonne)
  Utilizzare la pagina **Colonne** della finestra di dialogo **Editor trasformazione Esportazione colonna** per specificare le colonne nel flusso di dati da estrarre in file. È possibile indicare se la trasformazione Esporta colonna deve accodare i dati a un file oppure sovrascrivere un file esistente.  
  
 Per ulteriori informazioni sulla trasformazione Esportazione colonna, vedere [Export Column Transformation](data-flow/transformations/export-column-transformation.md).  
  
## <a name="options"></a>Opzioni  
 **Colonna estrazione**  
 Consente di eseguire una selezione dall'elenco di colonne di input contenenti dati di tipo text o image. In tutte le righe devono essere presenti definizioni per **Colonna estrazione** e **Colonna percorso file**.  
  
 **Colonna percorso file**  
 Consente di eseguire una selezione dall'elenco di colonne di input contenenti nomi e percorsi di file. In tutte le righe devono essere presenti definizioni per **Colonna estrazione** e **Colonna percorso file**.  
  
 **Consenti accodamento**  
 Consente di indicare se la trasformazione accoderà i dati ai file esistenti. Il valore predefinito è `false`.  
  
 **Forza troncamento**  
 Consente di indicare se la trasformazione eliminerà il contenuto di file esistenti prima di scrivere i dati. Il valore predefinito è `false`.  
  
 **Scrivi indicatore ordine byte**  
 Consente di specificare se scrivere un indicatore ordine byte (BOM) nel file. Un carattere BOM viene scritto solo se i dati hanno il `DT_NTEXT` o tipo di dati DT_WSTR e non viene aggiunta a un file di dati esistente.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento ai messaggi e agli errori di Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Editor trasformazione Esportazione colonna &#40;pagina dell'Output degli errori&#41;](../../2014/integration-services/export-column-transformation-editor-error-output-page.md)  
  
  
