---
title: Eseguire il metodo (comando ADO) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Command15::Execute
- Command15::raw_Execute
helpviewer_keywords:
- Execute method [ADO]
ms.assetid: f84a5ff3-0528-4ad7-9bea-9a15103378dd
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 7f16d3c01fb219bdbe7f52bbc39d3c410b5de918
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="execute-method-ado-command"></a>Eseguire il metodo (comando ADO)
Esegue la query, l'istruzione SQL o stored procedure specificata nel [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) o [CommandStream](../../../ado/reference/ado-api/commandstream-property-ado.md) proprietà del [oggetto comando](../../../ado/reference/ado-api/command-object-ado.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Set recordset = command.Execute( RecordsAffected, Parameters, Options )  
```  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) riferimento all'oggetto, un flusso, o **nulla**.  
  
#### <a name="parameters"></a>Parametri  
 *RecordsAffected*  
 Facoltativa. Oggetto **lungo** variabile in cui il provider restituisce il numero di record interessati dall'operazione. Il *RecordsAffected* parametro si applica solo a query o stored procedure. *RecordsAffected* non restituisce il numero di record restituito da una stored procedure o la restituzione di risultati di query. Per ottenere queste informazioni, utilizzare il [RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md) proprietà. Il **Execute** metodo non restituirà le informazioni corrette quando si utilizza **adAsyncExecute**, semplicemente perché quando viene eseguito un comando in modo asincrono, il numero di record interessati non può ancora essere noto al momento il metodo restituisce.  
  
 *Parametri*  
 Facoltativa. Oggetto **Variant** matrice di valori dei parametri utilizzati in combinazione con la stringa di input o di un flusso specificato in **CommandText** o **CommandStream**. (I parametri di output non restituisce valori corretti quando passati in questo argomento).  
  
 *Opzioni*  
 Facoltativa. A **lungo** valore che indica la modalità con cui il provider deve valutare il [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) o [CommandStream](../../../ado/reference/ado-api/commandstream-property-ado.md) proprietà del [comando](../../../ado/reference/ado-api/command-object-ado.md) oggetto. Può essere eseguito utilizzando un valore di maschera di bit [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) e/o [ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md) valori. Ad esempio, è possibile utilizzare **adCmdText** e **adExecuteStream** in combinazione, se si desidera utilizzare ADO di valutare il valore della **CommandText** proprietà come testo, e indica che il comando deve annullare e viene restituito alcun record che potrebbe essere generato quando viene eseguito il testo del comando.  
  
> [!NOTE]
>  Utilizzare il **ExecuteOptionEnum** valore **adExecuteStream** per migliorare le prestazioni riducendo al minimo l'elaborazione interna. Se **adExecuteStream** è stato specificato, le opzioni **adAsyncFetch** e **adAsynchFetchNonBlocking** vengono ignorati. Non utilizzare il **CommandTypeEnum** valori di **adCmdFile** o **adCmdTableDirect** con **Execute**. Questi valori possono essere utilizzati solo come opzioni con il [aprire](../../../ado/reference/ado-api/open-method-ado-recordset.md) e [Requery](../../../ado/reference/ado-api/requery-method.md) metodi di un **Recordset**.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzando il **Execute** metodo su un **comando** oggetto esegue la query specificata nel **CommandText** proprietà o **CommandStream** proprietà dell'oggetto.  
  
 Risultati vengono restituiti in un **Recordset** (per impostazione predefinita) o come un flusso di informazioni binarie. Per ottenere un flusso binario, specificare **adExecuteStream** in *opzioni*, quindi fornire un flusso impostando **Command.Properties ("flusso di Output")**. Un oggetto ADO **flusso** oggetto può essere specificato per ricevere i risultati o un altro oggetto di flusso, ad esempio l'oggetto risposta di IIS può essere specificato. Se è stato specificato alcun flusso prima di chiamare **Execute** con **adExecuteStream**, si verifica un errore. La posizione del flusso restituito dalla **Execute** è provider specifico.  
  
 Se il comando non può restituire risultati (ad esempio, una query di aggiornamento di SQL) restituisce il provider **nulla** fino a quando l'opzione **adExecuteStream** è specificata; in caso contrario eseguire restituisce un chiuso **Recordset**. Alcune lingue dell'applicazione consentono di ignorare il valore restituito se non **Recordset** desiderato.  
  
 **Eseguire** genera un errore se l'utente specifica un valore per **CommandStream** quando il **CommandType** è **adCmdStoredProc**,  **adCmdTable**, o **adCmdTableDirect**.  
  
 Se la query include parametri, valori di corrente per il **comando** vengono utilizzati i parametri dell'oggetto a meno che non si esegue l'override di questi valori dei parametri passati con il **Execute** chiamare. È possibile eseguire l'override di un subset dei parametri omettendo i nuovi valori per alcuni dei parametri quando si chiama il **Execute** metodo. L'ordine in cui si specificano i parametri è lo stesso ordine in cui li passa il metodo. Ad esempio, se sono presenti parametri quattro (o più) e si desidera passare nuovi valori per solo il primo e il quarto parametro, è necessario passare il `Array(var1,,,var4)` come il *parametri* argomento.  
  
> [!NOTE]
>  I parametri di output non restituirà i valori corretti quando passato il *parametri* argomento.  
  
 Un [ExecuteComplete](../../../ado/reference/ado-api/executecomplete-event-ado.md) verrà generato l'evento quando questa operazione è terminata.  
  
> [!NOTE]
>  Esecuzione di comandi che contiene gli URL, quelli che utilizzano lo schema http richiamerà automaticamente il [il Provider Microsoft OLE DB per Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Per ulteriori informazioni, vedere [URL assoluti e relativi](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Execute, Requery e deselezionare l'esempio di metodi (VB)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vb.md)   
 [Execute, Requery e Clear metodi esempio (VBScript)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vbscript.md)   
 [Execute, Requery e deselezionare l'esempio di metodi (VC + +)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vc.md)   
 [Proprietà CommandStream (ADO)](../../../ado/reference/ado-api/commandstream-property-ado.md)   
 [Proprietà CommandText (ADO)](../../../ado/reference/ado-api/commandtext-property-ado.md)   
 [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md)   
 [Execute (metodo) (connessione ADO)](../../../ado/reference/ado-api/execute-method-ado-connection.md)   
 [Evento ExecuteComplete (ADO)](../../../ado/reference/ado-api/executecomplete-event-ado.md)
