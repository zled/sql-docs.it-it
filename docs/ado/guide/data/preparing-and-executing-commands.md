---
title: Preparazione e l'esecuzione di comandi | Documenti Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Command object [ADO], preparing and executing commands
ms.assetid: 7448d9ee-7f4b-47e3-be54-2df8c9bbac32
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f566d3fb0c639e5f7cb7214d8cf467312ae7f28d
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="preparing-and-executing-commands"></a>Preparazione e l'esecuzione di comandi
I comandi sono disponibili istruzioni di rilasciato a un provider di eseguire alcune operazioni per l'origine dati sottostante. Un'istruzione SQL, è ad esempio, un comando per il Provider di dati SQL Microsoft. In ADO, i comandi in genere vengono rappresentati da **comando** oggetti, anche se i comandi semplici possono anche essere emessi tramite **connessione** o **Recordset** oggetti.  
  
 È possibile utilizzare il **comando** oggetto richiesta alcuna operazione di tipo supportato dal provider, presupponendo che il provider può interpretare correttamente la stringa di comando. È un'operazione comune per i provider di dati di query a un database e restituire i record in un **Recordset** oggetto, che può essere considerato come un contenitore per contenere il risultato e uno strumento per visualizzare il risultato. Come con molti oggetti ADO, alcuni **comando** raccolte di oggetti, metodi o proprietà potrebbe generare errori quando si fa riferimento, a seconda della funzionalità del provider.  
  
 Oltre a utilizzare **comando** oggetti, è possibile utilizzare il **Execute** metodo il **connessione** oggetto o **aprire** sul (metodo) **Recordset** esegue un comando e consentire l'esecuzione dell'oggetto. Tuttavia, è consigliabile utilizzare un **comando** dell'oggetto se è necessario riutilizzare un comando nel codice o se è necessario passare informazioni dettagliate sui parametri con il comando. Questi scenari sono illustrati in dettaglio più avanti in questa sezione.  
  
> [!NOTE]
>  Determinati **comando**s può restituire un risultato impostato come flusso binario o come una singola **Record** piuttosto che come un **Recordset**, se supportato dal provider. Inoltre, alcuni **comando**s non è studiata per restituire qualsiasi set di risultati affatto (ad esempio, una query SQL Update). In questa sezione illustra lo scenario più comune, tuttavia: l'esecuzione di **comando**che restituiscono i risultati come un **Recordset** oggetto. Per ulteriori informazioni sulla restituzione di risultati in **Record**s o **flusso**s, vedere [record e i flussi](../../../ado/guide/data/records-and-streams.md).  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Panoramica dell'oggetto Command](../../../ado/guide/data/command-object-overview.md)  
  
-   [Per creare ed eseguire un comando semplice](../../../ado/guide/data/creating-and-executing-a-simple-command.md)  
  
-   [Parametri dell'oggetto Command](../../../ado/guide/data/command-object-parameters.md)  
  
-   [Chiamare una Stored Procedure con un comando](../../../ado/guide/data/calling-a-stored-procedure-with-a-command.md)  
  
-   [Chiamare una Stored Procedure come metodo in un oggetto di connessione](../../../ado/guide/data/calling-a-stored-procedure-as-a-method-on-a-connection-object.md)  
  
-   [Comandi denominati](../../../ado/guide/data/named-commands.md)  
  
-   [Passaggio di parametri a un comando denominato](../../../ado/guide/data/passing-parameters-to-a-named-command.md)

