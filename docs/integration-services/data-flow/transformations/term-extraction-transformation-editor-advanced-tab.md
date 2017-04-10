---
title: "Editor trasformazione Estrazione termini (Scheda Avanzate) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.termextraction.advanced.f1"
helpviewer_keywords: 
  - "Editor trasformazione Estrazione termini"
ms.assetid: 87118281-6e3c-499e-bac4-fa4c24bb12c6
caps.latest.revision: 29
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 29
---
# Editor trasformazione Estrazione termini (Scheda Avanzate)
  Usare la scheda**Avanzate** della finestra di dialogo **Editor trasformazione Estrazione termini** per specificare le proprietà per l'estrazione, ad esempio la frequenza, la lunghezza e le eventuali parole o frasi da estrarre.  
  
 Per ulteriori informazioni sulla trasformazione Estrazione termini, vedere [Term Extraction Transformation](../../../integration-services/data-flow/transformations/term-extraction-transformation.md).  
  
## Opzioni  
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
 Usare la finestra di dialogo [Configura output errori](../Topic/Configure%20Error%20Output.md) per specificare la gestione degli errori per le righe che causano errori.  
  
## Vedere anche  
 [Guida di riferimento ai messaggi e agli errori di Integration Services](../../../integration-services/integration-services-error-and-message-reference.md)   
 [Editor trasformazione Estrazione termini &#40;scheda Estrazione termini&#41;](../../../integration-services/data-flow/transformations/term-extraction-transformation-editor-term-extraction-tab.md)   
 [Editor trasformazione Estrazione termini &#40;scheda Esclusione&#41;](../../../integration-services/data-flow/transformations/term-extraction-transformation-editor-exclusion-tab.md)   
 [Trasformazione Ricerca termini](../../../integration-services/data-flow/transformations/term-lookup-transformation.md)  
  
  