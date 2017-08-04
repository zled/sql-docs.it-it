---
title: Editor di trasformazione estrazione termini (scheda Avanzate) | Documenti Microsoft
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
- sql13.dts.designer.termextraction.advanced.f1
helpviewer_keywords:
- Term Extraction Transformation Editor
ms.assetid: 87118281-6e3c-499e-bac4-fa4c24bb12c6
caps.latest.revision: 29
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 605085b59357a98011c801f8aa4675e89c3cd8a9
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="term-extraction-transformation-editor-advanced-tab"></a>Editor trasformazione Estrazione termini (Scheda Avanzate)
  Usare la scheda **Avanzate** della finestra di dialogo **Editor trasformazione Estrazione termini** per specificare le proprietà per l'estrazione, ad esempio la frequenza, la lunghezza e le eventuali parole o frasi da estrarre.  
  
 Per ulteriori informazioni sulla trasformazione Estrazione termini, vedere [Term Extraction Transformation](../../../integration-services/data-flow/transformations/term-extraction-transformation.md).  
  
## <a name="options"></a>Opzioni  
 **Sostantivo**  
 Consente di specificare che la trasformazione estrarrà solo singoli sostantivi.  
  
 **Sintagma nominale**  
 Consente di specificare che la trasformazione estrarrà solo sintagmi nominali.  
  
 **Sostantivo e sintagma nominale**  
 Consente di specificare che la trasformazione estrarrà sia sostantivi che sintagmi nominali.  
  
 **Frequenza**  
 Consente di specificare che il punteggio è rappresentato dalla frequenza del termine.  
  
 **TFIDF**  
 Consente di specificare che il punteggio è rappresentato dal valore TFIDF del termine. Il punteggio TFIDF è il prodotto della frequenza dei termini e della frequenza inversa dei documenti, definito come: TFIDF di un termine T = (frequenza di T) * log( (numero di righe nell'input) / (numero di righe contenenti T) )  
  
 **Soglia di frequenza**  
 Consente di specificare il numero di volte in cui una parola o una frase deve ricorrere prima che venga estratta. Il valore predefinito è 2.  
  
 **Lunghezza massima termine**  
 Consente di specificare la lunghezza massima in parole di una frase. Questa opzione ha effetto soltanto sui sintagmi nominali. Il valore predefinito è 12.  
  
 **Estrazione con distinzione maiuscole/minuscole**  
 Consente di specificare se eseguire l'estrazione rilevando la distinzione tra maiuscole e minuscole. Il valore predefinito è **False**.  
  
 **Configura output errori**  
 Usare la finestra di dialogo [Configura output errori](http://msdn.microsoft.com/library/5f8da390-fab5-44f8-b268-d8fa313ce4b9) per specificare la gestione degli errori per le righe che causano errori.  
  
## <a name="see-also"></a>Vedere anche  
 [Errori di Integration Services e riferimento ai messaggi](../../../integration-services/integration-services-error-and-message-reference.md)   
 [Editor trasformazione estrazione termini &#40; Al termine scheda estrazione &#41;](../../../integration-services/data-flow/transformations/term-extraction-transformation-editor-term-extraction-tab.md)   
 [Editor trasformazione estrazione termini &#40; Scheda esclusione &#41;](../../../integration-services/data-flow/transformations/term-extraction-transformation-editor-exclusion-tab.md)   
 [Trasformazione Ricerca termini](../../../integration-services/data-flow/transformations/term-lookup-transformation.md)  
  
  
