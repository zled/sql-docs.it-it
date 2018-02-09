---
title: URL assoluto e relativo | Documenti Microsoft
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
helpviewer_keywords:
- relative URLs [ADO]
- absolute URLs [ADO]
- URLs [ADO]
ms.assetid: 6a34a7ef-50cc-4c3d-82f7-106b9a8f3caf
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 3564236b7b6bee2ae21f1b78a4275fb615aa2e4e
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="absolute-and-relative-urls"></a>URL assoluto e relativo
Un URL specifica il percorso di una destinazione memorizzata in un computer locale o in rete. La destinazione può essere un file, directory, una pagina HTML, immagine, programma e così via*.*  
  
 Un *URL assoluto* contiene tutte le informazioni necessarie per individuare una risorsa.  
  
 Oggetto *URL relativo* individua una risorsa utilizzando un URL assoluto come punto di partenza. In effetti, il "completamento URL" della destinazione è specificato dalla concatenazione gli URL assoluti e relativi.  
  
 Un *URL assoluto* Usa il seguente formato: *scheme://server/path/resource*  
  
 Un URL relativo in genere è costituito solo il *percorso*e, facoltativamente, il *risorse*, ma non *schema* o *server*. Nelle tabelle seguenti definiscono le singole parti del formato di URL completo.  
  
 *scheme*  
 Specifica il modo in *risorse* viene eseguito.  
  
 *server*  
 Specifica il nome del computer in cui il *risorse* si trova.  
  
 *path*  
 Specifica la sequenza di directory che conduce alla destinazione. Se *risorse* viene omesso, la destinazione è l'ultima directory in *percorso*.  
  
 *resource*  
 Se incluso, *risorse* è la destinazione e in genere è il nome di un file. Potrebbe essere un *file semplice,* contenente un singolo flusso binario di byte, o un *documento strutturato,* contenente uno o più flussi e archivi flussi binari di byte.  
  
## <a name="url-scheme-registration"></a>Registrazione dello schema URL  
 Se un provider supporta gli URL, il provider registrerà uno o più schemi URL. Registrazione significa che tutti gli URL utilizzando lo schema richiamerà automaticamente il provider registrato. Ad esempio, il *http* schema è registrato per il [il Provider Microsoft OLE DB per Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Si presume di tutte le URL abbiano con precedute "http" rappresentano cartelle o file da utilizzare con Provider di pubblicazione sul Web. Per informazioni sugli schemi di registrati dal provider, vedere la documentazione del provider.  
  
## <a name="defining-context-with-a-url"></a>Definizione del contesto con un URL  
 Una funzione di una connessione aperta, rappresentata da un [connessione](../../../ado/reference/ado-api/connection-object-ado.md) dell'oggetto, per limitare le operazioni successive all'origine dati è rappresentato da tale connessione. Ovvero, la connessione definisce il contesto per le operazioni successive.  
  
 Con ADO 2.7 o versioni successive, un URL assoluto inoltre possibile definire un contesto. Ad esempio, quando un [Record](../../../ado/reference/ado-api/record-object-ado.md) oggetto viene aperto con un URL assoluto, un **connessione** oggetto viene creato in modo implicito per rappresentare la risorsa specificata dall'URL.  
  
 Può essere specificato un URL assoluto che definisce un contesto di *ActiveConnection* parametro del **Record** oggetto [aprire](../../../ado/reference/ado-api/open-method-ado-record.md) (metodo). Un URL assoluto può anche essere specificato come valore della "URL**=**" parola chiave nel **connessione** oggetto [aprire](../../../ado/reference/ado-api/open-method-ado-connection.md) metodo  *ConnectionString* parametro e [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto [aprire](../../../ado/reference/ado-api/open-method-ado-recordset.md) metodo *ActiveConnection* parametro.  
  
 Contesto può essere definito anche aprendo un **Record** o **Recordset** oggetto che rappresenta una directory, perché questi oggetti dispongono già di un implicitamente o esplicitamente dichiarati **connessione**  oggetto che specifica di contesto.  
  
## <a name="scoped-operations"></a>Operazioni con ambito  
 Il contesto definisce anche l'ambito, vale a dire, la directory e nelle relative sottodirectory che possono partecipare nelle operazioni successive. Il **Record** oggetto ha diversi metodi con ambiti che operano su una directory e tutte le relative sottodirectory. Questi metodi includono [CopyRecord](../../../ado/reference/ado-api/copyrecord-method-ado.md), [MoveRecord](../../../ado/reference/ado-api/moverecord-method-ado.md), e [DeleteRecord](../../../ado/reference/ado-api/deleterecord-method-ado.md).  
  
## <a name="relative-urls-as-command-text"></a>URL relativi come testo del comando  
 È possibile specificare un comando da eseguire sull'origine dati, digitare una stringa nel *CommandText* parametro del **connessione** dell'oggetto [Execute](../../../ado/reference/ado-api/execute-method-ado-connection.md) (metodo) e il  *Origine* parametro il **Recordset** dell'oggetto [aprire](../../../ado/reference/ado-api/open-method-ado-recordset.md) metodo.  
  
 Può essere specificato un URL relativo di *CommandText* o *origine* parametro. URL relativo non rappresentano effettivamente un comando, ad esempio un comando SQL; specifica semplicemente i parametri. Il contesto della connessione attiva deve essere un URL assoluto e *opzione* parametro deve essere impostato su **adCmdTableDirect**.  
  
 Ad esempio, l'esempio di codice seguente viene illustrato come aprire un **Recordset** nel file Readme25. txt della directory Winnt/system32:  
  
```  
recordset.Open "system32/Readme25.txt", "URL=http://YourServer/Winnt/",,,adCmdTableDirect  
```  
  
 L'URL assoluto nella stringa di connessione specifica il server (`YourServer`) e il percorso (`Winnt`). Definisce inoltre il contesto.  
  
 L'URL relativo nel testo del comando utilizza l'URL assoluto come punto di partenza e specifica il resto del percorso (`system32`) e l'apertura del file (`Readme25.txt`).  
  
 Il campo Opzioni (`adCmdTableDirect`) indica che il tipo di comando è un URL relativo.  
  
 Ad esempio, il seguente codice verrà aperto un **Recordset** sul contenuto del `Winnt` directory:  
  
```  
recordset.Open "", "URL=http://YourServer/Winnt/",,,adCmdTableDirect  
```  
  
## <a name="ole-db-provider-supplied-url-schemes"></a>Schemi di URL fornito dal Provider OLE DB  
 La parte iniziale di un URL completo è il *schema* utilizzato per accedere alla risorsa identificata dal resto dell'URL. Esempi sono HTTP (Hypertext Transfer Protocol) e FTP (File Transfer Protocol).  
  
 ADO supporta i provider OLE DB che riconoscono i propri schemi URL. Ad esempio, il [il Provider Microsoft OLE DB per Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)*,* che accede ai file di Windows 2000 "pubblicati", riconosce lo schema HTTP esistente.  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto di connessione (ADO.NET)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Oggetto di record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)   
 [Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
