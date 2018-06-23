---
title: Editor trasformazione Ricerca fuzzy (scheda Avanzate) | Documenti Microsoft
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
- sql12.dts.designer.fuzzylookuptransformation.advanced.f1
helpviewer_keywords:
- Fuzzy Lookup Transformation Editor
ms.assetid: 0a2919be-2ea7-4c06-82b8-0ffad5f0dd83
caps.latest.revision: 26
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 65c7acaab54bbbaa18126e9c1d2ac032e96557da
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36077833"
---
# <a name="fuzzy-lookup-transformation-editor-advanced-tab"></a>Editor trasformazione Ricerca fuzzy (scheda Avanzate)
  Usare la scheda **Avanzate** della finestra di dialogo **Editor trasformazione Ricerca fuzzy** per impostare i parametri relativi alla ricerca fuzzy.  
  
 Per ulteriori informazioni sulla trasformazione Ricerca fuzzy, vedere [Fuzzy Lookup Transformation](data-flow/transformations/lookup-transformation.md).  
  
## <a name="options"></a>Opzioni  
 **Numero massimo di corrispondenze da restituire per ricerca**  
 Consente di specificare il numero massimo di corrispondenze restituite dalla trasformazione per ogni riga di input. L'impostazione predefinita è **1**.  
  
 **Soglia di somiglianza**  
 Consente di impostare la soglia di somiglianza a livello di componente mediante il dispositivo di scorrimento. Più il valore è vicino a 1, maggiore deve essere la somiglianza tra il valore di ricerca e il valore di origine per essere considerata una corrispondenza. L'aumento della soglia può migliorare la velocità di confronto, poiché verrà considerato un numero minore di record candidati.  
  
 **Delimitatori token**  
 Consente di specificare i delimitatori utilizzati dalla trasformazione per suddividere in token i valori delle colonne.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti per i messaggi e agli errori di Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Editor trasformazione Ricerca fuzzy &#40;scheda tabella di riferimento&#41;](../../2014/integration-services/fuzzy-lookup-transformation-editor-reference-table-tab.md)   
 [Editor trasformazione Ricerca fuzzy &#40;scheda colonne&#41;](../../2014/integration-services/fuzzy-lookup-transformation-editor-columns-tab.md)  
  
  