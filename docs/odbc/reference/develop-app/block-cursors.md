---
title: Bloccare i cursori | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- cursors [ODBC], block
- block cursors [ODBC]
- result sets [ODBC], block cursors
ms.assetid: 1a92b5d8-7c6e-4ce5-8c99-600a387026aa
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 21bbfa223e2eb58df8fc89b69f7f9df3c08983e8
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32912156"
---
# <a name="block-cursors"></a>Cursori a blocchi
Molte applicazioni impiegano una quantità significativa di tempo per trasferire i dati attraverso la rete. Parte di questo tempo è trascorso effettivamente riportare i dati attraverso la rete e una parte viene impiegata per la rete sovraccarico, ad esempio la chiamata eseguita dal driver per richiedere una riga di dati. Il tempo di quest'ultimo può essere ridotto se l'applicazione utilizza in modo efficiente *blocco* o *fat* *i cursori,* che può restituire più di una riga alla volta.  
  
 Sempre un'applicazione ha la possibilità di usare un cursore a blocchi. Sulle origini dati da cui può essere recuperata solo una riga alla volta, è necessario simulare cursori a blocchi nel driver. Questa operazione può essere eseguita mediante l'esecuzione di più operazioni di recupero a riga singola. Sebbene sia improbabile fornire un miglioramento delle prestazioni, viene aperto opportunità per le applicazioni. Di DBMS implementano cursori a blocchi in modo nativo e i driver associati a tali DBMS espongono, tali applicazioni verranno quindi riscontrare un aumento delle prestazioni.  
  
 Le righe restituite in un'unica operazione di recupero con un cursore a blocchi vengono chiamate i *set di righe*. È importante non confondere il set di righe con il set di risultati. Il set di risultati viene mantenuto nell'origine dati, mentre il set di righe viene mantenuto nel buffer dell'applicazione. Mentre il set di risultati è fisso, non è il set di righe, modifica la posizione e il contenuto ogni volta che viene recuperato un nuovo set di righe. Un cursore a riga singola, ad esempio i punti di cursore forward-only SQL tradizionale a una riga corrente, come un cursore a blocchi punta al set di righe, può essere considerato come *righe correnti*.  
  
 Per eseguire operazioni che operano su una singola riga, quando sono state recuperate più righe, l'applicazione prima di tutto necessario indicare quale riga è la riga corrente. La riga corrente viene richiesto dalle chiamate a **SQLGetData** e posizionato aggiornamento e istruzioni delete. Quando un cursore a blocchi innanzitutto viene restituito un set di righe, la riga corrente è la prima riga del set di righe. Per modificare la riga corrente, l'applicazione chiama **SQLSetPos** o **SQLBulkOperations** (per l'aggiornamento dal segnalibro). Nella figura seguente mostra la relazione tra il set di risultati, set di righe, la riga corrente, il cursore di set di righe e cursore a blocchi. Per ulteriori informazioni, vedere [cursori a blocchi usando](../../../odbc/reference/develop-app/using-block-cursors.md), più avanti in questa sezione e [istruzioni di eliminazione e aggiornamento posizionato](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md) e [aggiornamento dei dati con SQLSetPos](../../../odbc/reference/develop-app/updating-data-with-sqlsetpos.md).  
  
 ![Recupero del successivo, precedente, primo e ultimo set di righe](../../../odbc/reference/develop-app/media/pr20_2.gif "pr20_2")  
  
 Se un cursore è un cursore a blocchi è indipendente se è scorrevole. Ad esempio, la maggior parte del lavoro in un'applicazione di report viene impiegato per il recupero e la stampa delle righe. Per questo motivo, tale verranno eseguiti più rapidamente con forward-only, cursore a blocchi. Usa un cursore forward-only per evitare il costo di un cursore scorrevole e un cursore a blocchi per ridurre il traffico di rete.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Associazione di colonne per l'utilizzo con cursori rettangolari](../../../odbc/reference/develop-app/binding-columns-for-use-with-block-cursors.md)  
  
-   [Utilizzo di cursori rettangolari](../../../odbc/reference/develop-app/using-block-cursors.md)  
  
-   [Matrice di stato riga](../../../odbc/reference/develop-app/row-status-array.md)
