---
title: Utilizzi dei dati del catalogo | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- catalog data [ODBC]
- functions [ODBC], catalog functions
- catalog functions [ODBC], using catalog data
ms.assetid: d5915d0c-eec3-4382-850e-bd863763c99a
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 61a112f126eb83d40e350c5cc275f28438f15383
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="uses-of-catalog-data"></a>Utilizzi dei dati del catalogo
Le applicazioni utilizzano dati del catalogo in diversi modi. Ecco alcuni usi comuni:  
  
-   **Creazione di istruzioni SQL in fase di esecuzione.** Applicazioni verticali, ad esempio un'applicazione di immissione dell'ordine, contengono le istruzioni SQL hard-coded. Le tabelle e colonne utilizzate dall'applicazione vengono corretti anticipatamente, sono istruzioni che accedono a tali tabelle. Ad esempio, un'applicazione di immissione ordini contiene in genere un singolo, con parametri **inserire** istruzione per l'aggiunta di nuovi ordini per il sistema.  
  
     Spesso, le applicazioni generiche, ad esempio un foglio di calcolo che utilizza ODBC per recuperare i dati, creare istruzioni SQL in fase di esecuzione in base all'input dell'utente. Tale applicazione potrebbe richiedere all'utente di digitare i nomi delle tabelle e colonne da utilizzare. Tuttavia, sarebbe più facile per l'utente se l'applicazione visualizzata elenchi di tabelle e colonne da cui l'utente può effettuare selezioni. Per compilare questi elenchi, l'applicazione chiama il **SQLTables** e **SQLColumns** funzioni di catalogo.  
  
-   **Creazione di istruzioni SQL durante lo sviluppo.** In genere, gli ambienti di sviluppo di applicazioni consentono ai programmatori di creare query di database durante lo sviluppo di un programma. Le query sono quindi hardcoded nell'applicazione da compilare.  
  
     Inoltre è possibile utilizzare tali ambienti **SQLTables** e **SQLColumns** per creare elenchi da cui il programmatore può effettuare selezioni. Questi ambienti possono essere utilizzate anche **SQLPrimaryKeys** e **SQLForeignKeys** per determinare automaticamente e mostrare le relazioni tra le tabelle selezionate e utilizzare **SQLStatistics** per determinare ed evidenziare i campi indicizzati per consentire al programmatore di creare query efficienti.  
  
-   **La creazione di cursori.** Impossibile utilizzare un'applicazione, un driver o un middleware che fornisce un motore del cursore scorrevole **SQLSpecialColumns** per determinare quale colonna o quali colonne identificano una riga. Impossibile compilare il programma un *keyset* contenente i valori di queste colonne per ogni riga che è stata recuperata. Quando si scorre l'applicazione torna alla riga, utilizzerebbe quindi questi valori per recuperare i dati più recenti per la riga. Per ulteriori informazioni sui cursori scorrevoli e keyset, vedere [cursori scorrevoli](../../../odbc/reference/develop-app/scrollable-cursors.md).

