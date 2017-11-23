---
title: Livelli di isolamento delle transazioni | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dirty reads [ODBC]
- isolation levels [ODBC]
- nonrepeatable reads [ODBC]
- read uncommitted [ODBC]
- read committed [ODBC]
- serializable reads [ODBC]
- phantoms [ODBC]
- transaction isolation [ODBC]
- repeatable reads [ODBC]
- transactions [ODBC], isolation
ms.assetid: 0d638d55-ffd0-48fb-834b-406f466214d4
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: f0b5499af07c7bbb5309ff87037f7c3825872dab
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="transaction-isolation-levels"></a>Livelli di isolamento delle transazioni
*Livelli di isolamento delle transazioni* sono una misura dell'estensione per la transazione ha esito positivo isolamento. In particolare, i livelli di isolamento delle transazioni vengono definiti dalla presenza o assenza di fenomeni di seguenti:  
  
-   **Letture dirty** A *lettura dirty* si verifica quando una transazione legge i dati che non è ancora stato eseguito il commit. Ad esempio, si supponga che gli aggiornamenti delle transazioni 1 una riga. La transazione 2 legge la riga aggiornata prima l'aggiornamento di commit della transazione 1. Se 1 rollback della transazione di modifica, la transazione 2 hanno leggerà i dati viene considerati mai esistito.  
  
-   **Letture non ripetibili** A *lettura non ripetibile* si verifica quando una transazione legge la stessa riga due volte, ma ottiene dati diversi ogni volta. Ad esempio, si supponga che la transazione 1 letture una riga. La transazione 2 aggiorna o elimina tale riga e viene eseguito il commit di aggiornamento o eliminazione. Se la transazione 1 consente di leggere nuovamente la riga, recupera i valori di riga diversi o individua che la riga è stata eliminata.  
  
-   **Righe fantasma** A *fantasma* è una riga che corrisponde ai criteri di ricerca ma non viene inizialmente visualizzata. Si supponga, ad esempio, la transazione 1 legge un set di righe che soddisfa alcuni criteri di ricerca. La transazione 2 genera una nuova riga (tramite un aggiornamento o un'istruzione insert) che corrisponde ai criteri di ricerca per la transazione 1. Se la transazione 1 reexecutes l'istruzione che legge le righe, ottiene un set diverso di righe.  
  
 I quattro livelli di isolamento (come definito da SQL-92) sono definiti in termini di fenomeni. Nella tabella seguente, "X" contrassegna ogni fenomeno che può verificarsi.  
  
|Livello di isolamento delle transazioni|Letture dirty|Letture non ripetibili|Righe fantasma|  
|---------------------------------|-----------------|-------------------------|--------------|  
|Read Uncommitted|X|X|X|  
|Read Committed|--|X|X|  
|Repeatable Read|--|--|X|  
|Serializable|--|--|--|  
  
 Nella tabella seguente vengono descritti i semplici metodi che DBMS potrebbe implementare livelli di isolamento delle transazioni.  
  
> [!IMPORTANT]  
>  La maggior parte dei DBMS utilizzare combinazioni più complesse rispetto a queste per aumentare la concorrenza. Questi esempi sono forniti solo a scopo illustrativo. In particolare, ODBC prescrivono il DBMS specifico come isolare le transazioni tra loro.  
  
|Isolamento delle transazioni|Implementazione possibili|  
|---------------------------|-----------------------------|  
|Read Uncommitted|Le transazioni non sono isolate una da altra. Se il sistema DBMS supporta altri livelli di isolamento delle transazioni, ignora qualsiasi meccanismo viene utilizzato per implementare tali livelli. In modo che non influiscano negativamente altre transazioni, le transazioni eseguite al livello Read Uncommitted sono in genere di sola lettura.|  
|Read Committed|La transazione attende fino a quando le righe scrittura bloccata da altre transazioni vengono sbloccate; Ciò evita la lettura di tutti i dati "dirty".<br /><br /> Contiene la transazione un blocco di lettura (se legge solo la riga) o di scrittura del blocco (se aggiorna o elimina la riga) per impedire alle altre transazioni di aggiornamento o l'eliminazione di riga corrente. La transazione rilascia i blocchi di lettura quando si sposta dalla riga corrente. Contiene dei blocchi di scrittura finché viene eseguito il commit o rollback.|  
|Repeatable Read|La transazione attende fino a quando le righe scrittura bloccata da altre transazioni vengono sbloccate; Ciò evita la lettura di tutti i dati "dirty".<br /><br /> La transazione mantiene i blocchi di lettura su tutte le righe che restituisce i blocchi di applicazione e scrittura in tutte le righe vengano inserimenti, aggiornamenti o eliminati. Ad esempio, se la transazione include l'istruzione SQL **selezionare \* FROM Orders**, i blocchi di lettura transazione righe che l'applicazione recupera tali. Se la transazione include l'istruzione SQL **eliminare da ordini in cui lo stato = 'Chiuso'**, i blocchi di scrittura delle transazioni righe che li elimina.<br /><br /> Dato che altre transazioni non è possibile aggiornare o eliminare queste righe, la transazione corrente evita qualsiasi letture non ripetibili. La transazione rilascia i blocchi quando viene eseguito il commit o rollback.|  
|Serializable|La transazione attende fino a quando le righe scrittura bloccata da altre transazioni vengono sbloccate; Ciò evita la lettura di tutti i dati "dirty".<br /><br /> La transazione contiene un blocco di lettura (se legge solo righe) o il blocco di scrittura (se è possibile aggiornare o eliminare righe) dell'intervallo di righe interessa. Ad esempio, se la transazione include l'istruzione SQL **selezionare \* FROM Orders**, l'intervallo è l'intera tabella Orders; il transazione lettura blocchi di tabella e non non consentire l'aggiunta di nuove righe da inserire. Se la transazione include l'istruzione SQL **eliminare da ordini in cui lo stato = 'Chiuso'**, l'intervallo è tutte le righe con lo stato di "CLOSED"; i blocchi di scrittura transazione tutte le righe degli ordini di tabella il cui stato è "Chiuso" e non non Consenti tutte le righe da inserire o aggiornare in modo che la riga risulta ha lo stato "Chiuso".<br /><br /> Dato che altre transazioni non è possibile aggiornare o eliminare le righe nell'intervallo, la transazione corrente evita qualsiasi letture non ripetibili. Dato che altre transazioni non è possibile inserire le righe nell'intervallo, la transazione corrente evita qualsiasi righe fantasma. La transazione rilascia il blocco quando viene eseguito il commit o rollback.|  
  
 È importante notare che il livello di isolamento non influisce sulla possibilità di una transazione per visualizzare le proprie modifiche; le transazioni possono sempre visualizzare qualsiasi modifica apportata. Ad esempio, una transazione può essere costituito da due **aggiornamento** istruzioni, il primo dei quali genera la retribuzione di tutti i dipendenti del 10% e il secondo dei quali imposta la retribuzione dei dipendenti su alcune quantità massima di tale quantità. L'esito è positivo come una singola transazione solo perché la seconda **aggiornamento** istruzione è possibile visualizzare i risultati del primo.
