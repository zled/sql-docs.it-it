---
title: Execute (metodo) (connessione ADO) | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::Execute
- Connection15::raw_Execute
helpviewer_keywords:
- Execute method [ADO]
ms.assetid: 03c69320-96b2-4d85-8d49-a13b13e31578
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 27f99015571bd7abdad402dc0f779c04fd546a79
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="execute-method-ado-connection"></a>Execute (metodo) (connessione ADO)
Esegue query specificata, istruzione SQL, stored procedure o il testo del provider.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Set recordset = connection.Execute (CommandText, RecordsAffected, Options)  
Set recordset = connection.Execute (CommandText, RecordsAffected, Options)  
```  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un [Recordset ADO (Object)](../../../ado/reference/ado-api/recordset-object-ado.md) riferimento all'oggetto.  
  
#### <a name="parameters"></a>Parametri  
 *commandText*  
 Oggetto **stringa** valore contenente l'istruzione SQL, stored procedure, un URL o il testo del provider per l'esecuzione. **Facoltativamente**, nomi di tabella possono essere utilizzati ma solo se il provider è compatibile con SQL. Per ad esempio se un nome di tabella "Customers" viene usato, ADO automaticamente anteporre la sintassi SQL Select standard per creare e passare a "SELECT * FROM Customers" come un [!INCLUDE[tsql](../../../includes/tsql_md.md)] istruzione per il provider.  
  
 *RecordsAffected*  
 Facoltativa. Oggetto **lungo** variabile in cui il provider restituisce il numero di record interessati dall'operazione.  
  
 *Opzioni*  
 Facoltativa. Oggetto **lungo** valore che indica la modalità con cui il provider deve valutare l'argomento CommandText. Può essere una maschera di bit di uno o più [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) o [ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md) valori.  
  
 **Nota** utilizzare la **ExecuteOptionEnum** valore **adExecuteStream** per migliorare le prestazioni riducendo al minimo l'elaborazione interna e per le applicazioni che si esegue il porting da Visual Basic 6.0.  
  
 Non utilizzare **adExecuteStream** con il **Execute** metodo di un **connessione** oggetto.  
  
 Non utilizzare i valori CommandTypeEnum di adCmdFile o adCmdTableDirect con Execute. Questi valori possono essere utilizzati solo come opzioni con il [Open (metodo) (Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md) e [metodo Requery](../../../ado/reference/ado-api/requery-method.md) metodi di un **Recordset**.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzando il **Execute** metodo su un [connessione ADO (Object)](../../../ado/reference/ado-api/connection-object-ado.md) viene eseguito l'oggetto di qualsiasi query passata al metodo nell'argomento CommandText sulla connessione specificata. Se l'argomento CommandText specifica una query che restituiscono righe, i risultati generati dall'esecuzione vengono archiviati in un nuovo **Recordset** oggetto. Se il comando non può restituire risultati (ad esempio, una query di aggiornamento di SQL) restituisce il provider **nulla** fino a quando l'opzione **adExecuteStream** è specificata; in caso contrario eseguire restituisce un chiuso **Recordset**.  
  
 L'oggetto restituito **Recordset** oggetto è sempre un cursore forward-only in sola lettura. Se è necessario un **Recordset** con altre funzionalità, creare innanzitutto un **Recordset** con le impostazioni di proprietà desiderato, quindi specificare il **Recordset** oggetto [ Open (metodo) (Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md) per eseguire la query e restituire il tipo di cursore desiderato.  
  
 Il contenuto del *CommandText* argomento sono specifico del provider e può essere la sintassi SQL standard o qualsiasi formato di comando speciale che supporta il provider.  
  
 Verrà generato un evento ExecuteComplete quando conclusione dell'operazione.  
  
> [!NOTE]
>  Gli URL che utilizzano lo schema http richiamerà automaticamente il [il Provider Microsoft OLE DB per Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Per ulteriori informazioni, vedere [URL assoluti e relativi](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)
