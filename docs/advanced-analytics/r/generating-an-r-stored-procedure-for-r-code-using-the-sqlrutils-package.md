---
title: Generazione di una stored procedure R per il codice R tramite il pacchetto sqlrutils | Microsoft Docs
ms.custom: 
ms.date: 02/28/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: R
ms.assetid: d8739f16-ac26-4f69-870c-51c77cf286d3
caps.latest.revision: "8"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 805d533d140512754ecd6393654c67fa70f93340
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/01/2017
---
# <a name="generating-an-r-stored-procedure-for-r-code-using-the-sqlrutils-package"></a>Generazione di una stored procedure R per il codice R tramite il pacchetto sqlrutils
Il pacchetto **sqlrutils** fornisce un meccanismo che consente agli utenti di R di inserire gli script R in una stored procedure T-SQL, registrare la stored procedure con un database ed eseguirla da un ambiente di sviluppo R. 

Effettuando la conversione del codice R per consentirne l'esecuzione all'interno di una singola stored procedure, è possibile ottimizzare l'uso di SQL Server R Services. Per questo è necessario che uno script R sia incorporato come parametro in [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). Il pacchetto **sqlrutils** consente di creare questo script R incorporato e di impostare i parametri correlati in modo appropriato.

Il pacchetto **sqlrutils** esegue queste attività:

- Salva lo script T-SQL generato come stringa all'interno di una struttura di dati R.
- Facoltativamente, genera un file con estensione sql per lo script T-SQL, che è possibile modificare o eseguire per creare una stored procedure.
- Registra la stored procedure creata con l'istanza di SQL Server dall'ambiente di sviluppo R.

È anche possibile eseguire la stored procedure da un ambiente R, passando i parametri corretti ed elaborando i risultati. In alternativa, è possibile usare la stored procedure da SQL Server per supportare scenari comuni di integrazione di database, ad esempio i processi di estrazione, trasformazione e caricamento (ETL, Extract, Transform, Load), il training di modelli e l'assegnazione di punteggi a grandi volumi di dati.

  > [!NOTE]
  > Se si intende eseguire la stored procedure da un ambiente R chiamando la funzione *executeStoredProcedure* , è necessario usare un provider ODBC 3.8, ad esempio ODBC Driver 13 for SQL Server.  
  
## <a name="functions-provided-in-sqlrutils"></a>Funzioni disponibili in sqlrutils

L'elenco seguente offre una panoramica delle funzioni che è possibile chiamare dal pacchetto **sqlrutils** per sviluppare una stored procedure per l'uso in SQL Server R Services. Per informazioni dettagliate sui parametri per ogni metodo o funzione, vedere la Guida di R per il pacchetto:

```R
help(package="sqlrutils") 
```

**Definire i parametri e gli input della stored procedure**

- `InputData`. Definisce l'origine dei dati di SQL Server che verranno usati nel frame di dati R. Specificare il nome del frame di dati in cui archiviare i dati di input e una query per ottenere i dati o un valore predefinito. Sono supportate solo query SELECT.

- `InputParameter`. Definisce un singolo parametro di input che verrà incorporato nello script T-SQL. È necessario specificare il nome del parametro e il tipo di dati R corrispondente.

- `OutputData`. Genera un oggetto dati intermedio che è necessario se la funzione R restituisce un elenco contenente un frame di dati. 
   L'oggetto *OutputData* viene usato per archiviare il nome di un singolo frame di dati ottenuto dall'elenco. 

- `OutputParameter`. Genera un oggetto dati intermedio che è necessario se la funzione R restituisce un elenco. L'oggetto *OutputParameter* archivia il nome e il tipo di dati di un singolo membro dell'elenco, presupponendo che tale membro **non** sia un frame di dati. 


**Generare e registrare la stored procedure**


- `StoredProcedure` è il costruttore principale usato per creare la stored procedure.  Questo costruttore genera un oggetto *stored procedure di SQL Server* e, facoltativamente, crea un file di testo contenente una query che può essere usata per generare la stored procedure tramite un comando T-SQL. Facoltativamente, la funzione *StoredProcedure* può anche registrare la stored procedure con il database e l'istanza specificati.

   + Usare l'argomento `func` per specificare una funzione R valida. Tutte le variabili usate dalla funzione devono essere definite all'interno della funzione o specificate come parametri di input. Questi parametri possono includere al massimo un frame di dati.
   + La funzione R deve restituire un frame di dati, un elenco denominato o un valore NULL. Se la funzione restituisce un elenco, questo può contenere al massimo un frame di dati.
   + Usare l'argomento `spName` per specificare il nome della stored procedure che si vuole creare.
   + È possibile passare parametri di output e input facoltativi usando gli oggetti creati da queste funzioni helper: `setInputData`, `setInputParameter`e `setOutputParameter`.
   +  Facoltativamente, usare `filePath` per specificare il percorso e il nome di un file con estensione sql da creare. È possibile eseguire questo file nell'istanza di SQL Server per generare la stored procedure mediante T-SQL.
   + Per definire il server e il database in cui verrà salvata la stored procedure, usare gli argomenti `dbName` e  `connectionString`.
   + Per ottenere l'elenco degli oggetti *InputData* e *InputParameter* usati per creare un oggetto *StoredProcedure* specifico, chiamare `getInputParameters`. 
   + Per registrare la stored procedure con il database specificato, usare `registerStoredProcedure`.

   All'oggetto stored procedure non sono in genere associati dati o valori, a meno che non sia stato specificato un valore predefinito. I dati non vengono recuperati finché non viene eseguita la stored procedure. 


**Specificare gli input ed eseguire la stored procedure**

- Usare `setInputDataQuery` per assegnare una query a un oggetto *InputParameter* . Se ad esempio è stato creato un oggetto stored procedure in R, è possibile usare `setInputDataQuery` per passare argomenti alla funzione *StoredProcedure* in modo da eseguire la stored procedure con gli input desiderati.

- Usare `setInputValue` per assegnare valori specifici a un parametro archiviato come oggetto *InputParameter* . Passare quindi l'oggetto parametro e il valore assegnato relativo alla funzione *StoredProcedure* per eseguire la stored procedure con i valori impostati.

- Usare `executeStoredProcedure` per eseguire una stored procedure definita come oggetto *StoredProcedure* . Chiamare questa funzione solo quando si esegue una stored procedure dal codice R. Non usarla quando si esegue la stored procedure da SQL Server mediante T-SQL.

  > [!NOTE]
  > La funzione *executeStoredProcedure* richiede un provider ODBC 3.8, ad esempio ODBC Driver 13 for SQL Server.  
  
  



## <a name="see-also"></a>Vedere anche
[Come creare una stored procedure con sqlrutils](../../advanced-analytics/r-services/how-to-create-a-stored-procedure-using-sqlrutils.md)

