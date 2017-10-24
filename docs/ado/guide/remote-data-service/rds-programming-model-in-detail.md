---
title: Modello di programmazione di servizi desktop remoto in modo dettagliato | Documenti Microsoft
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
- RDS programming model [ADO], details
ms.assetid: 3e57af8d-519b-4467-a0bd-af468534cefd
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: db8a1222c560b54629baa34da595e0f5c49835b0
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="rds-programming-model-in-detail"></a>Modello di programmazione di servizi desktop remoto in modo dettagliato
Di seguito sono indicati gli elementi chiave del modello di programmazione di servizi desktop remoto:  
  
-   RDS. DataSpace  
  
-   RDSServer  
  
-   RDS. DataControl  
  
-   Evento  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="rdsdataspace"></a>RDS. DataSpace  
 L'applicazione client deve specificare il server e il programma di server da richiamare. In cambio, l'applicazione riceve un riferimento all'applicazione server e può gestire il riferimento come se fosse il programma server stesso.  
  
 Il modello a oggetti RDS integra questa funzionalità di [RDS. DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md) oggetto.  
  
 L'applicazione server è specificata con un ID di programma, o *ProgID*. Il server utilizza il *ProgID* e del Registro di sistema del computer server per individuare le informazioni sul programma effettivo da avviare.  
  
 Servizi Desktop remoto viene fatta distinzione internamente a seconda se l'applicazione server è in un server remoto tramite Internet o una intranet. un server in una rete locale; o non in un server, ma in una libreria di collegamento dinamico (DLL) locale. Questa distinzione determina come le informazioni scambiate tra il client e il server e fa la differenza tangibile nel tipo di riferimento restituito all'applicazione client. Tuttavia, dal punto di vista, questa distinzione hanno alcun significato speciale. Tutto ciò che è importante è che viene restituito un riferimento di un programma utilizzabile.  
  
## <a name="rdsserverdatafactory"></a>RDSServer  
 Servizi Desktop remoto offre un'applicazione server predefinita in grado di eseguire una query SQL sull'origine dati e restituire un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) dell'oggetto o richiedere un **Recordset** dell'oggetto e aggiornare l'origine dati.  
  
 Il modello a oggetti RDS integra questa funzionalità di [RDSServer](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) oggetto.  
  
 Inoltre, questo oggetto dispone di un metodo per la creazione di un oggetto vuoto **Recordset** oggetto che è possibile riempire a livello di codice ([CreateRecordset](../../../ado/reference/rds-api/createrecordset-method-rds.md)) e un altro metodo per convertire un **Recordset ** oggetto in una stringa di testo per creare una pagina Web ([ConvertToString](../../../ado/reference/rds-api/converttostring-method-rds.md)).  
  
 Con ADO, è possibile ignorare alcuni connessione standard e comportamento del comando di **RDSServer** con un **DataFactory** gestore e un file di personalizzazione che contiene una connessione, comando, e i parametri di sicurezza.  
  
 L'applicazione server è a volte definita un *oggetto business*. È possibile scrivere il proprio oggetto business personalizzato che è possibile eseguire l'accesso ai dati complesse, controlli di validità e così via. Anche quando si scrive un oggetto business personalizzato, è possibile creare un'istanza di un **RDSServer** dell'oggetto e utilizzare alcuni dei relativi metodi per eseguire le proprie attività.  
  
## <a name="rdsdatacontrol"></a>RDS. DataControl  
 Consente di combinare le funzionalità di servizi desktop remoto di **RDS. DataSpace** e **RDSServer**e inoltre abilitare i controlli visual utilizzare facilmente la **Recordset** oggetto restituito da una query da un'origine dati. Tenta di servizi desktop remoto, nel caso più comune, eseguire il più possibile accedere a informazioni su un server e visualizzarli in un controllo visivo automaticamente.  
  
 Il modello a oggetti RDS integra questa funzionalità di [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) oggetto.  
  
 Il **RDS. DataControl** presenta due aspetti. Un aspetto relativo all'origine dati. Se si imposta il comando e informazioni di connessione utilizzando il **Connetti** e **SQL** le proprietà del **RDS. DataControl**, verrà utilizzato automaticamente il **RDS. DataSpace** per creare un riferimento all'impostazione predefinita **RDSServer** oggetto. Il **RDSServer** utilizzerà il **Connetti** valore della proprietà per la connessione all'origine dati, utilizzare il **SQL** valore della proprietà da ottenere un ** Recordset** dall'origine dati e restituire il **Recordset** dell'oggetto per il **RDS. DataControl**.  
  
 La seconda caratteristica relativa alla visualizzazione di restituito **Recordset** informazioni in un controllo visivo. È possibile associare un controllo visivo con il **RDS. DataControl** (in un processo denominato associazione) e accedere alle informazioni nell'oggetto associato **Recordset** oggetto, visualizzare i risultati della query in una pagina Web in Microsoft® Internet Explorer. Ogni **RDS. DataControl** oggetto associa uno **Recordset** oggetto che rappresenta i risultati di una singola query, a uno o più controlli visivi (ad esempio, una casella di testo, una casella combinata, un controllo griglia e così via). Possono esistere più **RDS. DataControl** oggetto in ogni pagina. Ogni **RDS. DataControl** oggetto può essere connesso a un'origine dati diversa e contiene i risultati di una query separata.  
  
 Il **RDS. DataControl** oggetto include anche metodi per l'esplorazione, ordinamento e il filtraggio delle righe dell'oggetto associato **Recordset** oggetto. Questi metodi sono simili, ma non identici, i metodi sull'oggetto ADO **Recordset** oggetto.  
  
## <a name="events"></a>Eventi  
 Servizi Desktop remoto supporta due degli eventi interni, che sono indipendenti dal modello di eventi ADO. Il [onReadyStateChange](../../../ado/reference/rds-api/onreadystatechange-event-rds.md) eventi viene chiamato ogni volta che il **RDS. DataControl** [ReadyState](../../../ado/reference/rds-api/readystate-property-rds.md) modifiche delle proprietà, notificando all'utente quando un'operazione asincrona è completata, terminata o si è verificato un errore. Il [onError](../../../ado/reference/rds-api/onerror-event-rds.md) eventi viene chiamato ogni volta che si verifica un errore, anche se l'errore si verifica durante un'operazione asincrona.  
  
> [!NOTE]
>  Microsoft Internet Explorer sono disponibili due eventi aggiuntivi per RDS: **onDataSetChanged**, che indica che il **Recordset** è il recupero di righe, è ancora completamente funzionale e ** onDataSetComplete**, che indica che il **Recordset** ha completato il recupero di righe.  
  
## <a name="see-also"></a>Vedere anche  
 [Modello di programmazione di servizi desktop remoto con gli oggetti](../../../ado/guide/remote-data-service/rds-programming-model-with-objects.md)   
 [Oggetto DataControl (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)   
 [Oggetto DataFactory (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)   
 [Oggetto DataSpace (RDS)](../../../ado/reference/rds-api/dataspace-object-rds.md)   
 [Scenario di servizi desktop remoto](../../../ado/guide/remote-data-service/rds-scenario.md)   
 [Esercitazione di servizi desktop remoto](../../../ado/guide/remote-data-service/rds-tutorial.md)   
 [Utilizzo e sicurezza per RDS](../../../ado/guide/remote-data-service/rds-usage-and-security.md)




