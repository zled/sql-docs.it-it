---
title: Il Provider di servizi remoti Microsoft OLE DB (ADO Service Provider) | Documenti Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- OLE DB remoting provider [ADO]
- providers [ADO], OLE DB remoting provider
- remoting provider [ADO]
ms.assetid: a4360ed4-b70f-4734-9041-4025d033346b
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4f132bb8124afecea1b1f7fb519ecf64d1cfe88a
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="microsoft-ole-db-remoting-provider-overview"></a>Cenni preliminari sul Provider di servizi remoti Microsoft OLE DB
Il Provider remoto Microsoft OLE DB consente a un utente locale in un computer client richiamare i provider di dati in un computer remoto. Specificare i parametri di provider di dati per il computer remoto come se fosse un utente locale sul computer remoto. Quindi specificare i parametri utilizzati dal Provider di servizi remoti di accedere al computer remoto. È quindi possibile accedere al computer remoto, come se trattasse di un utente locale.

> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).

## <a name="provider-keyword"></a>Parola chiave del provider
 Per richiamare il Provider OLE DB remota, specificare la parola chiave e il valore seguente nella stringa di connessione. Si noti lo spazio vuoto il nome del provider.

```
"Provider=MS Remote"
```

## <a name="additional-keywords"></a>Parole chiave aggiuntive
 Quando viene richiamato questo provider di servizi, le parole chiave aggiuntive seguenti sono rilevanti.

|Parola chiave|Description|
|-------------|-----------------|
|**Data Source**|Specifica il nome dell'origine dati remota. Viene passato per il Provider OLE DB remota per l'elaborazione.<br /><br /> Questa parola chiave è equivalente al [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) dell'oggetto [Connetti](../../../ado/reference/rds-api/connect-property-rds.md) proprietà.|

## <a name="dynamic-properties"></a>Proprietà dinamiche
 Quando viene richiamato questo provider di servizi, le proprietà dinamiche seguenti vengono aggiunti per il [connessione](../../../ado/reference/ado-api/connection-object-ado.md)dell'oggetto [proprietà](../../../ado/reference/ado-api/properties-collection-ado.md) insieme.

|Nome della proprietà dinamica|Description|
|---------------------------|-----------------|
|**DFMode**|Indica la modalità DataFactory. Stringa che specifica la versione desiderata del [DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) oggetto sul server. Impostare questa proprietà prima di aprire una connessione per una particolare versione di richiedere la **DataFactory**. Se la versione richiesta non è disponibile, verrà effettuato un tentativo di utilizzare la versione precedente. Se non è una versione precedente, si verificherà un errore. Se **DFMode** è inferiore rispetto a quella disponibile, si verificherà un errore. Questa proprietà è di sola lettura dopo che viene stabilita una connessione.<br /><br /> Può essere uno dei seguenti valori di stringa valida:<br /><br /> -"25", versione 2.5 (impostazione predefinita)<br />-"21", versione 2.1<br />-"20", versione 2.0<br />-"15", versione 1.5|
|**Proprietà dei comandi**|Indica i valori che verranno aggiunti alla stringa di proprietà del comando (set di righe) inviati al server dal provider MS Remote. Il valore predefinito di questa stringa è vt_empty.|
|**DFMode corrente**|Indica il numero di versione effettiva di **DataFactory** sul server. Questa proprietà per verificare se la versione richiesta nel **DFMode** proprietà è stata rispettata.<br /><br /> Può essere uno dei valori interi lunghi validi seguenti:<br /><br /> -25-versione 2.5 (impostazione predefinita)<br />-21-versione 2.1<br />-20-versione 2.0<br />-15-versione 1.5<br /><br /> Aggiunta di "DFMode = 20;" alla stringa di connessione quando si utilizza il **MSRemote** provider può migliorare le prestazioni del server durante l'aggiornamento dati. Con questa impostazione, il **RDSServer** oggetto sul server utilizza una modalità meno risorse. Tuttavia, le funzionalità seguenti non sono disponibili in questa configurazione:<br /><br /> -Utilizzo di query con parametri.<br />-Recupero di informazioni di parametro o una colonna prima di chiamare il **Execute** metodo.<br />-Impostazione **Transact Updates** a **True**.<br />-Ottenere lo stato di riga.<br />-La chiamata di **Resync** metodo.<br />-Aggiornamento (in modo esplicito o automatico) tramite il **Update Resync** proprietà.<br />-Impostazione **comando** o **Recordset** proprietà.<br />-Utilizzo **adCmdTableDirect**.|
|**gestore**|Indica il nome di un programma di personalizzazione lato server (o gestore) che estende la funzionalità del [RDSServer](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)ed eventuali parametri utilizzati dal gestore*,* tutti separati da virgole ( ","). Oggetto **stringa** valore.|
|**Timeout Internet**|Indica il numero massimo di millisecondi di attesa per una richiesta di trasmessi da e verso il server. (Il valore predefinito è 5 minuti).|
|**Provider remoto**|Indica il nome del provider di dati da utilizzare nel server remoto.|
|**Server remoto**|Indica il protocollo di comunicazione e nome del server utilizzabile da questa connessione. Questa proprietà è equivalente al [RDS. DataContro](../../../ado/reference/rds-api/datacontrol-object-rds.md) oggetto [Server](../../../ado/reference/rds-api/server-property-rds.md) proprietà.|
|**Transact aggiornamenti**|Se impostato su **True**, questo valore indica che quando [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) viene eseguita nel server, verrà eseguita all'interno di una transazione. Il valore predefinito per questa proprietà dinamica booleana è **False**.|

 È inoltre possibile impostare le proprietà dinamiche scrivibile specificando i relativi nomi come parole chiave nella stringa di connessione. Ad esempio, impostare il **Timeout Internet** proprietà dinamiche a cinque secondi, specificando:

```
Dim cn as New ADODB.Connection
cn.Open "Provider=MS Remote;Internet Timeout=5000"
```

 Per impostare o recuperare una proprietà dinamica specificandone il nome dell'indice per il **proprietà** proprietà. Nell'esempio seguente viene illustrato come ottenere e visualizzare il valore corrente del **Timeout Internet** proprietà dinamiche e quindi impostare un nuovo valore:

```
Debug.Print cn.Properties("Internet Timeout")
cn.Properties("Internet Timeout") = 5000
```

## <a name="remarks"></a>Osservazioni
 In ADO.NET 2.0, il Provider OLE DB remota può specificare solo nel *ActiveConnection* parametro del [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto **aprire** metodo. A partire da ADO 2.1, il provider può anche essere specificato nel *ConnectionString* parametro del [connessione](../../../ado/reference/ado-api/connection-object-ado.md) oggetto **aprire** metodo.

 L'equivalente di **RDS. DataControl** oggetto [SQL](../../../ado/reference/rds-api/sql-property.md) proprietà non è disponibile. Il [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto **aprire** metodo *origine* viene invece utilizzato l'argomento.

 **Nota** specificando ".... Provider remoto = MS Remote;... "verrà creato uno scenario a quattro livelli. Scenario oltre a tre livelli non è stati testati e non sono necessari.

## <a name="example"></a>Esempio
 In questo esempio viene eseguita una query sul **autori** sommario il **Pubs** database in un server denominato *server*. I nomi di origine dati remota e server remoti vengono forniti nel [aprire](../../../ado/reference/ado-api/open-method-ado-connection.md) metodo il[connessione](../../../ado/reference/ado-api/connection-object-ado.md) oggetto e la query SQL viene specificata nel[aprire](../../../ado/reference/ado-api/open-method-ado-recordset.md) metodo il [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto. Oggetto **Recordset** oggetto viene restituito, modificato e utilizzato per aggiornare l'origine dati.

```
Dim rs as New ADODB.Recordset
Dim cn as New ADODB.Connection
cn.Open  "Provider=MS Remote;Data Source=pubs;" & _
         "Remote Server=http://YourServer"
rs.Open "SELECT * FROM authors", cn
...                'Edit the recordset
rs.UpdateBatch     'Equivalent of RDS SubmitChanges
...
```

## <a name="see-also"></a>Vedere anche
 [Panoramica del Provider OLE DB per la comunicazione remota](http://msdn.microsoft.com/en-us/4083b72f-68c4-4252-b366-abb70db5ca2b)
