---
title: "Proprietà ConnectionString (ADO) | Documenti Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Connection15::ConnectionString
helpviewer_keywords:
- ConnectionString property [ADO]
ms.assetid: 3be75b75-4d36-4479-ab64-9a456869252a
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 34db69d25ff835de4f8c81d252c99017ae4acbb5
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="connectionstring-property-ado"></a>Proprietà ConnectionString (ADO)
Indica le informazioni utilizzate per stabilire una connessione a un'origine dati.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Restituisce o imposta un **stringa** valore.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il **ConnectionString** proprietà per specificare un'origine dati passando una stringa di connessione dettagliata contenente una serie di *argomento* *= valore* istruzioni separate da punto e virgola.  
  
 ADO supporta cinque argomenti per il **ConnectionString** proprietà; qualsiasi altro passaggio di argomenti direttamente al provider senza alcuna elaborazione da parte di ADO. ADO supporta gli argomenti è i seguenti.  
  
|Argomento|Description|  
|--------------|-----------------|  
|*Provider =*|Specifica il nome di un provider da utilizzare per la connessione.|  
|*Nome file =*|Specifica il nome di un file specifico del provider (ad esempio, un oggetto origine dati persistenti) contenente informazioni di connessione predefinite.|  
|*Provider remoto =*|Specifica il nome di un provider da utilizzare quando si apre una connessione sul lato client. (Solo servizio dati remota).|  
|*Server remoto =*|Specifica il nome del percorso del server da utilizzare quando si apre una connessione sul lato client. (Solo servizio dati remota).|  
|*URL =*|Specifica la stringa di connessione come un URL assoluto che identifica una risorsa, ad esempio un file o directory.|  
  
 Dopo aver impostato la **ConnectionString** proprietà e aprire il [connessione](../../../ado/reference/ado-api/connection-object-ado.md) dell'oggetto, il provider può modificare il contenuto della proprietà, ad esempio, eseguendo il mapping di nomi degli argomenti definiti da ADO per loro equivalenti per il provider specifico.  
  
 Il **ConnectionString** proprietà eredita automaticamente il valore utilizzato per il *ConnectionString* argomento del [aprire](../../../ado/reference/ado-api/open-method-ado-connection.md) metodo, pertanto è possibile eseguire l'override di corrente** ConnectionString** proprietà durante il **aprire** chiamata al metodo.  
  
 Poiché il *nome File* argomento lo induce ADO caricare il provider associato, è possibile passare a entrambi il *Provider* e *nome File* argomenti.  
  
 Il **ConnectionString** proprietà è di lettura/scrittura quando la connessione è chiusa e di sola lettura quando è aperto.  
  
 I duplicati di un argomento in di **ConnectionString** proprietà vengono ignorate. Viene utilizzata l'ultima istanza di un argomento.  
  
> [!NOTE]
>  **Utilizzo del servizio dati remoti** quando utilizzato sul lato client **connessione** oggetto, il **ConnectionString** proprietà può includere solo la *Provider remoto*e *Server remoto* parametri.  
  
 La tabella seguente elenca il provider ADO predefinito per ogni sistema operativo Windows:  
  
|Provider ADO predefinito|Sistema operativo Windows|  
|--------------------------|------------------------------|  
|MSDASQL<br /><br /> (Per migliorare la leggibilità del codice sorgente, specificare in modo esplicito il nome del provider nella stringa di connessione.)|Windows 2000 (32 bit)<br /><br /> Windows XP (32 bit)<br /><br /> Windows Server 2003 (32 bit)<br /><br /> Windows Vista (32 bit)<br /><br /> Windows Vista Service Pack 1 o versioni successive (32 bit e 64 bit)<br /><br /> Versioni di Windows, Windows Vista (32 bit e 64 bit)|  
|Nessuna impostazione predefinita.<br /><br /> Quando un'applicazione ADO viene eseguito nei seguenti sistemi operativi e non specifica il provider in modo esplicito, ADO restituisce l'errore seguente: "ADODB. Connessione: il provider non è specificato e nessun provider predefinito designato "|Windows 2000 (64 bit)<br /><br /> Windows XP (64 bit)<br /><br /> Windows Server 2003 (64 bit)<br /><br /> Windows Vista (64 bit)|  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto di connessione (ADO.NET)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio ConnectionString, ConnectionTimeout e la proprietà State (VB)](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vb.md)   
 [Esempio ConnectionString, ConnectionTimeout e la proprietà State (VC + +)](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vc.md)   
 [Appendice a: provider](../../../ado/guide/appendixes/appendix-a-providers.md)

