---
title: Comando oggetto (ADO) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: Command
helpviewer_keywords: Command object [ADO]
ms.assetid: a02c22fb-542d-465e-a629-30fd59dcbebf
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 2f4aab59ac3a5296d4dcd75927b632f7a6915d46
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="command-object-ado"></a>Oggetto Command (ADO)
Definisce un comando specifico che si desidera eseguire in un'origine dati.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare un **comando** oggetto query in un database e restituire i record in un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto, per eseguire un'operazione bulk o per modificare la struttura di un database. La funzionalità del provider, a seconda alcune **comando** raccolte, i metodi o proprietà possono generare un errore quando vi viene fatto riferimento.  
  
 Con le raccolte, i metodi e proprietà di un **comando** dell'oggetto, è possibile eseguire le operazioni seguenti:  
  
-   Definire il testo del comando (ad esempio, un'istruzione SQL) eseguibile con il [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) proprietà. In alternativa, per il comando o una query strutture diverso semplice stringhe (ad esempio, query modello XML) definiscono il comando con il [CommandStream](../../../ado/reference/ado-api/commandstream-property-ado.md) proprietà.  
  
-   Facoltativamente, indicare il sottolinguaggio del comando usato nel **CommandText** o **CommandStream** con il [sottolinguaggio](../../../ado/reference/ado-api/dialect-property.md) proprietà.  
  
-   Definire le query con parametri o gli argomenti di stored procedure con [parametro](../../../ado/reference/ado-api/parameter-object.md) oggetti e [parametri](../../../ado/reference/ado-api/parameters-collection-ado.md) insieme.  
  
-   Indicare se i nomi di parametro devono essere passati al provider con il [NamedParameters](../../../ado/reference/ado-api/namedparameters-property-ado.md) proprietà.  
  
-   Eseguire un comando e restituire un **Recordset** oggetto se appropriato, tramite il [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md) metodo.  
  
-   Specificare il tipo di comando con il [CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md) proprietà prima dell'esecuzione per ottimizzare le prestazioni.  
  
-   Controllare se il provider Salva una versione preparata (compilata o) del comando prima dell'esecuzione con il [Prepared](../../../ado/reference/ado-api/prepared-property-ado.md) proprietà.  
  
-   Impostare il numero di secondi di attesa per un comando da eseguire con un provider di [CommandTimeout](../../../ado/reference/ado-api/commandtimeout-property-ado.md) proprietà.  
  
-   Associare una connessione aperta con un **comando** oggetto impostando il relativo [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) proprietà.  
  
-   Impostare il [nome](../../../ado/reference/ado-api/name-property-ado.md) proprietà per identificare il **comando** oggetto come un metodo sull'oggetto associato [connessione](../../../ado/reference/ado-api/connection-object-ado.md) oggetto.  
  
-   Passare un **comando** dell'oggetto per il [origine](../../../ado/reference/ado-api/source-property-ado-recordset.md) proprietà di un **Recordset** per ottenere i dati.  
  
-   Accedere agli attributi specifici del provider con il [proprietà](../../../ado/reference/ado-api/properties-collection-ado.md) insieme.  
  
> [!NOTE]
>  Per eseguire una query senza utilizzare un **comando** dell'oggetto, passare una stringa di query per il [Execute](../../../ado/reference/ado-api/execute-method-ado-connection.md) metodo di un **connessione** oggetto o il [aprire](../../../ado/reference/ado-api/open-method-ado-recordset.md)metodo di un **Recordset** oggetto. Tuttavia, un **comando** oggetto sono obbligatorie quando si desidera mantenere il testo del comando ed eseguirla nuovamente o utilizzare i parametri di query.  
  
 Per creare un **comando** oggetto in modo indipendente da un oggetto definito in precedenza **connessione** dell'oggetto, impostare il relativo **ActiveConnection** proprietà in una stringa di connessione valida. ADO verrà comunque creato un **connessione** oggetto, ma non assegnare tale oggetto a una variabile oggetto. Tuttavia, se si desidera associare più **comando** gli oggetti con la stessa connessione, creare e aprire in modo esplicito un **connessione** oggetto; questa assegna il **connessione** oggetto a una variabile oggetto. Assicurarsi che il **connessione** oggetto è stato aperto correttamente prima di assegnarlo al **ActiveConnection** proprietà del **comando** dell'oggetto, perché l'assegnazione di un chiuso **connessione** oggetto provoca un errore. Se non si imposta la **ActiveConnection** proprietà del **comando** dell'oggetto a questa variabile di oggetto, crea un nuovo oggetto ADO **connessione** per ciascun  **Comando** dell'oggetto, anche se si utilizza la stessa stringa di connessione.  
  
 Per eseguire un **comando**, chiamarlo relativo [nome](../../../ado/reference/ado-api/name-property-ado.md) proprietà sull'oggetto associato **connessione** oggetto. Il **comando** deve avere il **ActiveConnection** proprietà impostata sul **connessione** oggetto. Se il **comando** dispone di parametri, passare valori come argomenti al metodo.  
  
 Se due o più **comando** gli oggetti vengono eseguiti nella stessa connessione e **comando** oggetto è una stored procedure con parametri di output, si verifica un errore. Per eseguire ogni **comando** dell'oggetto, utilizzare connessioni separate o disconnettere tutti gli altri **comando** oggetti dalla connessione.  
  
 Il **parametri** insieme è il membro predefinito del **comando** oggetto. Di conseguenza, le due istruzioni di codice seguenti sono equivalenti.  
  
```  
objCmd.Parameters.Item(0)  
objCmd(0)  
```  
  
-   Il **comando** oggetto non è sicuro per lo scripting.  
  
 In questa sezione contiene l'argomento seguente.  
  
-   [Oggetto proprietà, metodi ed eventi di comando](../../../ado/reference/ado-api/command-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto di connessione (ADO.NET)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Raccolta di parametri (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)   
 [Raccolta delle proprietà (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [Appendice A: Provider](../../../ado/guide/appendixes/appendix-a-providers.md)
