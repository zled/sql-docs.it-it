---
title: "finestra Variabili locali | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.locals"
helpviewer_keywords: 
  - "Variabili locali - finestra [Transact-SQL]"
ms.assetid: 59bea640-7823-4b4d-832c-f384d83cca2f
caps.latest.revision: 16
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# finestra Variabili locali
  Nella finestra **Variabili locali** vengono visualizzate informazioni sulle espressioni locali nell'ambito corrente del debugger [!INCLUDE[tsql](../../includes/tsql-md.md)] . L'ambito è impostato sul frame dello stack di chiamate corrente selezionato nella finestra **Stack di chiamate** . Per visualizzare espressioni locali, è necessario utilizzare la modalità di debug.  
  
## Elenco attività  
 **Per accedere alla finestra Variabili locali**  
  
-   Scegliere **Finestre** dal menu **Debug**, quindi fare clic su **Variabili locali**.  
  
 **Per modificare il valore di un'espressione**  
  
-   Fare clic con il pulsante destro del mouse sull'espressione, quindi scegliere **Modifica valore**.  
  
## Colonne  
 **Nome**  
 Nome dell'espressione locale. Nel debugger [!INCLUDE[tsql](../../includes/tsql-md.md)] vengono elencati parametri, variabili e funzioni di sistema i cui nomi iniziano per @@.  
  
 **Valore**  
 Consente di visualizzare il valore è assegnato attualmente all'espressione locale. Questa colonna è vuota quando non è stato assegnato alcun valore all'espressione.  
  
 Se la lunghezza di un'espressione è maggiore della larghezza della colonna **Valore** , il valore completo verrà visualizzato in una descrizione comandi quando si sposta il puntatore sulla cella **Valore** per l'espressione.  
  
 Un'icona di lente di ingrandimento in una cella **Valore** indica che è disponibile il visualizzatore del debugger [!INCLUDE[tsql](../../includes/tsql-md.md)] . Nell'elenco è possibile specificare **Visualizzatore testo**, **Visualizzatore XML**o **Visualizzatore HTML**. Per avviare un visualizzatore del debugger, fare clic sull'icona di lente di ingrandimento. Tramite il debugger [!INCLUDE[tsql](../../includes/tsql-md.md)] viene visualizzata una finestra di dialogo contenente dati in un formato appropriato per il tipo di dati.  
  
 **Tipo**  
 Consente di visualizzare il tipo di dati dell'espressione.  
  
## Vedere anche  
 [Debugger Transact-SQL](../../relational-databases/scripting/transact-sql-debugger.md)   
 [Informazioni del debugger Transact-SQL](../../relational-databases/scripting/transact-sql-debugger-information.md)   
 [finestra Espressioni di controllo](../../relational-databases/scripting/watch-window.md)   
 [Finestra Stack di chiamate](../../relational-databases/scripting/call-stack-window.md)   
 [Finestra di dialogo Controllo immediato](../../relational-databases/scripting/quickwatch-dialog-box.md)   
 [Espressioni &#40; Transact-SQL &#41;](../../t-sql/language-elements/expressions-transact-sql.md)  
  
  