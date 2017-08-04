---
title: Editor trasformazione Ricerca fuzzy (scheda Avanzate) | Documenti Microsoft
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
- sql13.dts.designer.fuzzylookuptransformation.advanced.f1
helpviewer_keywords:
- Fuzzy Lookup Transformation Editor
ms.assetid: 0a2919be-2ea7-4c06-82b8-0ffad5f0dd83
caps.latest.revision: 27
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 6036e6f61ef2bb3d0f974642fd6c595e2199f73b
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="fuzzy-lookup-transformation-editor-advanced-tab"></a>Editor trasformazione Ricerca fuzzy (scheda Avanzate)
  Usare la scheda **Avanzate** della finestra di dialogo **Editor trasformazione Ricerca fuzzy** per impostare i parametri relativi alla ricerca fuzzy.  
  
 Per ulteriori informazioni sulla trasformazione Ricerca fuzzy, vedere [Fuzzy Lookup Transformation](../../../integration-services/data-flow/transformations/fuzzy-lookup-transformation.md).  
  
## <a name="options"></a>Opzioni  
 **Numero massimo di corrispondenze da restituire per ricerca**  
 Consente di specificare il numero massimo di corrispondenze restituite dalla trasformazione per ogni riga di input. L'impostazione predefinita è **1**.  
  
 **Soglia di somiglianza**  
 Consente di impostare la soglia di somiglianza a livello di componente mediante il dispositivo di scorrimento. Più il valore è vicino a 1, maggiore deve essere la somiglianza tra il valore di ricerca e il valore di origine per essere considerata una corrispondenza. L'aumento della soglia può migliorare la velocità di confronto, poiché verrà considerato un numero minore di record candidati.  
  
 **Delimitatori token**  
 Consente di specificare i delimitatori utilizzati dalla trasformazione per suddividere in token i valori delle colonne.  
  
## <a name="see-also"></a>Vedere anche  
 [Errori di Integration Services e riferimento ai messaggi](../../../integration-services/integration-services-error-and-message-reference.md)   
 [Editor trasformazione Ricerca fuzzy &#40; Scheda tabella di riferimento &#41;](../../../integration-services/data-flow/transformations/fuzzy-lookup-transformation-editor-reference-table-tab.md)   
 [Editor trasformazione Ricerca fuzzy &#40; Scheda Colonne &#41;](../../../integration-services/data-flow/transformations/fuzzy-lookup-transformation-editor-columns-tab.md)  
  
  
