---
title: "Editor trasformazione Colonna derivata | Microsoft Docs"
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
  - "sql13.dts.designer.derivedcolumntransformation.f1"
helpviewer_keywords: 
  - "Editor trasformazione Colonna derivata"
ms.assetid: ff73923e-d245-43d8-bf24-af3bdc942e51
caps.latest.revision: 33
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 33
---
# Editor trasformazione Colonna derivata
  Usare la finestra di dialogo **Editor trasformazione Colonna derivata** per creare espressioni che popolino le colonne nuove o di sostituzione.  
  
 Per altre informazioni sulla trasformazione Colonna derivata, vedere [Trasformazione Colonna derivata](../../../integration-services/data-flow/transformations/derived-column-transformation.md).  
  
## Opzioni  
 **Variabili e Colonne**  
 Consente di compilare un'espressione che utilizza una variabile o una colonna di input tramite un'operazione di trascinamento della variabile o della colonna dall'elenco di variabili e colonne disponibili in una riga di tabella esistente nel riquadro sottostante o in una nuova riga alla fine dell'elenco.  
  
 **Funzioni e Operatori**  
 Compilare un'espressione che utilizza una funzione o un operatore per valutare i dati di input e indirizzare i dati di output trascinando le funzioni e gli operatori dall'elenco al riquadro sottostante.  
  
 **Nome colonna derivata**  
 Consente di assegnare un nome alla colonna derivata. L'impostazione predefinita è rappresentata da un elenco numerato di colonne derivate. È tuttavia possibile scegliere qualsiasi nome descrittivo e univoco.  
  
 **Colonna derivata**  
 Consente di selezionare una colonna derivata dall'elenco. Scegliere se aggiungere la colonna derivata come nuova colonna di output o sostituire i dati in una colonna esistente.  
  
 **Espressione**  
 Consente di digitare un'espressione o compilarne una mediante il trascinamento dal precedente elenco di colonne, variabili, funzioni e operatori disponibili.  
  
 È possibile specificare il valore di questa proprietà tramite un'espressione di proprietà.  
  
 **Argomenti correlati**: [Espressioni di Integration Services &#40;SSIS&#41;](../../../integration-services/expressions/integration-services-ssis-expressions.md), [Operatori &#40;espressione SSIS&#41;](../../../integration-services/expressions/operators-ssis-expression.md) e [Funzioni &#40;espressione SSIS&#41;](../../../integration-services/expressions/functions-ssis-expression.md)  
  
 **Tipo di dati**  
 Se si aggiungono dati a una nuova colonna, nella finestra di dialogo **Editor trasformazione Colonna derivata** viene valutata automaticamente l'espressione e viene impostato automaticamente il tipo di dati appropriato. Il valore di questa colonna è di sola lettura. Per altre informazioni, vedere [Tipi di dati di Integration Services](../../../integration-services/data-flow/integration-services-data-types.md).  
  
 **Lunghezza**  
 Se si aggiungono dati a una nuova colonna, nella finestra di dialogo **Editor trasformazione colonna derivata** viene valutata automaticamente l'espressione e impostata la lunghezza della colonna per i dati stringa. Il valore di questa colonna è di sola lettura.  
  
 **Precisione**  
 Se si aggiungono dati a una nuova colonna, nella finestra di dialogo **Editor trasformazione Colonna derivata** viene impostata automaticamente la precisione per i dati numerici in base al tipo di dati. Il valore di questa colonna è di sola lettura.  
  
 **Scala**  
 Se si aggiungono dati a una nuova colonna, nella finestra di dialogo **Editor trasformazione Colonna derivata** viene impostata automaticamente la scala per i dati numerici in base al tipo di dati. Il valore di questa colonna è di sola lettura.  
  
 **Tabella codici**  
 Se si aggiungono dati a una nuova colonna, nella finestra di dialogo **Editor trasformazione Colonna derivata** viene impostata automaticamente la tabella codici per il tipo di dati DT_STR. È possibile aggiornare **Tabella codici**.  
  
 **Configura output errori**  
 Consente di indicare come gestire gli errori tramite la finestra di dialogo [Configura output errori](../Topic/Configure%20Error%20Output.md).  
  
## Vedere anche  
 [Guida di riferimento ai messaggi e agli errori di Integration Services](../../../integration-services/integration-services-error-and-message-reference.md)   
 [Derivazione di valori di colonna tramite la trasformazione Colonna derivata](../../../integration-services/data-flow/transformations/derive-column-values-by-using-the-derived-column-transformation.md)  
  
  