---
title: Cmdlet Invoke-ASCmd | Documenti Microsoft
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 2896b74a-3911-4b3f-89ab-bb375bdb34d8
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 366263980ae7ad9d5a792e6525888080a38ebbf6
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="invoke-ascmd-cmdlet"></a>Cmdlet Invoke-ASCmd

[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  Consente a un amministratore del database di eseguire uno script XMLA, query MDX (Multidimensional Expressions), istruzioni DMX (Data Mining Extensions) o script TMSL (Tabular Model Scripting Language).  
  
 TMSL è supportato solo per la modalità server tabulare in un'istanza di SQL Server 2016 Analysis Services.  
  
 Questo è il cmdlet da usare per creare database o altri oggetti con un file di input di script.  
  
## <a name="syntax"></a>Sintassi  
 `Invoke-ASCmd –Query <string> [-Server <string>] [-Database <string>] [-Credential <PSCredential>] [-ConnectionTimeout <int>] [-QueryTimeout <int>] [-Variable <string[]>] [-TraceFile <string>] [-TraceFileFormat <TraceFileFormatOption>] [-TraceFileDelimiter <string>] [-TraceTimeout <int>] [-TraceLevel <TraceLevelOption>] [<CommonParameters>]`  
  
 `Invoke-ASCmd –InputFile <string> [-Server <string>] [-Database <string>] [-Credential <PSCredential>] [-ConnectionTimeout <int>] [-QueryTimeout <int>] [-Variable <string[]>] [-TraceFile <string>] [-TraceFileFormat <TraceFileFormatOption>] [-TraceFileDelimiter <string>] [-TraceTimeout <int>] [-TraceLevel <TraceLevelOption>] [<CommonParameters>]`  
  
## <a name="description"></a>Description  
 Il cmdlet Invoke-ASCmd può eseguire query o script contenuti nei file di input.  
  
 Per XMLA sono supportati i comandi seguenti: Alter, Backup, Batch, BeginTransaction, Cancel, ClearCache, CommitTransaction, Create, Delete, DesignAggregations, Drop, Insert, Lock, MergePartitions, NotifyTableChange, Process, Restore, RollbackTransaction, Statement (usato per eseguire query MDX e istruzioni DMX), Subscribe, Synchronize, Unlock, Update, UpdateCells.  
  
 Per TMSL: Alter, Create, Delete, MergePartitions, Process, Update.  
  
 Questo cmdlet supporta il parametro -Credential, che può essere utilizzato se è stata configurata l'istanza di Analysis Services per l'accesso HTTP. Il parametro -Credential accetta un oggetto PSCredential che fornisce un'identità utente di Windows. In IIS verrà quindi rappresentato questo utente durante la connessione ad Analysis Services. Per eseguire lo script, è necessario che l'identità disponga delle autorizzazioni di amministratore di sistema nell'istanza di Analysis Services.  
  
## <a name="parameters"></a>Parametri  
  
### <a name="-query-string"></a>-Query \<stringa >  
 Specifica la query, l'istruzione o lo script effettivo direttamente nella riga di comando anziché in un file. È possibile specificare anche una query come input della pipeline. Quando si usa **Invoke-AsCmd** , è necessario specificare un valore per il parametro **–InputFile** o **–Query**.  
  
|||  
|-|-|  
|Obbligatorio?|true|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|True (ByValue)|  
|Accettare caratteri jolly?|false|  
  
### <a name="-inputfile-string"></a>-InputFile \<stringa >  
 Identifica il file contenente lo script XMLA, la query MDX, l'istruzione DMX o lo script TMSL (in JSON). Quando si usa **Invoke-AsCmd** , è necessario specificare un valore per il parametro **–InputFile** o **–Query**.  
  
|||  
|-|-|  
|Obbligatorio?|true|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-server-string"></a>-Server \<stringa >  
 Specifica l'istanza di Analysis Services a cui il cmdlet deve connettersi per l'esecuzione. Se non viene fornito alcun nome del server, la connessione verrà effettuata a localhost. Per le istanze predefinite è sufficiente specificare il nome del server, mentre per quelle denominate, utilizzare il formato nomeserver\nomeistanza. Per le connessioni HTTP, utilizzare il formato http[s]://server[:porta]/virtualdirectory/msmdpump.dll.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito|localhost|  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-database-string"></a>-Database \<stringa >  
 Specifica il database su cui deve essere eseguita una query MDX o un'istruzione DMX. Il parametro del database viene ignorato se tramite il cmdlet viene eseguito uno script XMLA, poiché il nome del database viene incorporato nello script stesso.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-credential-pscredential"></a>-Credential \<PSCredential >  
 Specifica un oggetto PSCredential che fornisce un nome utente e una password di Windows. Specificare questo parametro solo se l'istanza di Analysis Services viene configurata per l'accesso HTTP, utilizzando l'autenticazione di base. Per le connessioni native in cui viene utilizzata la sicurezza integrata, questo parametro viene ignorato.  
  
 Se questo parametro è presente, le credenziali fornite vengono accodate alla stringa di connessione. In IIS verrà quindi rappresentata questa identità utente durante la connessione ad Analysis Services. Se non vengono specificate credenziali, verrà utilizzato l'account di Windows predefinito dell'utente che esegue lo strumento.  
  
 Per usare questo parametro, creare innanzitutto un oggetto PSCredential usando Get-Credential per specificare il nome utente e la password, ad esempio, `$Cred=Get-Credential “adventure-works\admin”`. Successivamente è possibile inoltrare tramite pipe questo oggetto al parametro -Credential `(-Credential:$Cred`.  
  
   Per altre informazioni sull'accesso HTTP, vedere [Configurare l'accesso HTTP ad Analysis Services in Internet Information Services &#40;IIS&#41; 8.0](../../analysis-services/instances/configure-http-access-to-analysis-services-on-iis-8-0.md).  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|True (ByValue)|  
|Accettare caratteri jolly?|false|  
  
### <a name="-connectiontimeout-int"></a>-ConnectionTimeout \<int >  
 Specifica il numero di secondi prima del timeout della connessione all'istanza di Analysis Services. Il valore di timeout deve essere un intero compreso tra 0 e 65534. Se si specifica 0, non si verifica alcun timeout dei tentativi di connessione.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito|30|  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-querytimeout-int"></a>-QueryTimeout \<int >  
 Specifica il numero di secondi prima del timeout delle query. Se non si specifica nessun valore di timeout, alle query non viene associato alcun timeout. Il timeout deve essere un intero compreso tra 1 e 65535.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito|30|  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-variable-string"></a>-Variabile \<string [] >  
 Specifica ulteriori variabili di scripting. Ogni variabile è una coppia nome-valore. Se nel valore sono contenuti spazi o caratteri di controllo incorporati, è necessario racchiuderlo tra virgolette doppie Utilizzare una matrice di PowerShell per specificare più variabili e i relativi valori.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-tracefile-string"></a>-TraceFile \<stringa >  
 Identifica il file a cui vengono inviati gli eventi di traccia di Analysis Services durante l'esecuzione dello script XMLA, della query MDX o dell'istruzione DMX. Se il file è già esistente, viene automaticamente sovrascritto, a meno che non si tratti di un file di traccia creato con le impostazioni dei parametri -TraceLevel:Duration e –TraceLevel:DurationResult. I nomi di file che contengono spazi devono essere racchiusi tra virgolette (" "). Se il nome file non è valido, viene generato un messaggio di errore.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-tracefileformat-string"></a>-TraceFileFormat \<stringa >  
 Specifica il formato file per il parametro –TraceFile, se quest'ultimo è specificato. Le opzioni disponibili sono testo o csv. Il valore predefinito è "csv".  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito|csv|  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-tracefiledelimiter-string"></a>-TraceFileDelimiter \<stringa >  
 Specifica il carattere da utilizzare come delimitatore del file di traccia se viene specificato csv come formato di questo file. Il carattere predefinito è | (barra verticale).  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito||  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-tracetimeout-int"></a>-TraceTimeout \<int >  
 Specifica il numero di secondi di attesa del motore di Analysis Services prima di terminare la traccia, nel caso in cui si specifichi il parametro –TraceFile. La traccia viene considerata conclusa se non viene registrato alcun messaggio durante il periodo di tempo specificato. Il valore di timeout di traccia predefinito è di 5 secondi.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito|5|  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="-tracelevel-traceleveloption"></a>-TraceLevel \<TraceLevelOption >  
 Specifica quali dati vengono raccolti e registrati nel file di traccia. I valori possibili sono High, Medium, Low, Duration, DurationResult.  
  
|||  
|-|-|  
|Obbligatorio?|false|  
|Posizione?|denominata|  
|Valore predefinito|Alto|  
|Accettare input da pipeline?|false|  
|Accettare caratteri jolly?|false|  
  
### <a name="commonparameters"></a>\<Parametricomuni >  
 In questo cmdlet vengono supportati i parametri comuni: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer e -OutVariable. Per altre informazioni, vedere [About_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825).  
  
## <a name="inputs-and-outputs"></a>Input e output  
 Il tipo di input è il tipo degli oggetti che è possibile inoltrare tramite pipe al cmdlet. Il tipo restituito è il tipo degli oggetti restituiti dal cmdlet.  
  
|||  
|-|-|  
|Input|PSObject|  
|Output|String|  
  
## <a name="example-1-xmla-input-file"></a>Esempio 1 (file di input XMLA)  
  
```  
Invoke-ASCmd –InputFile:"C:\MyFolder\DiscoverConnections.xmla"  
```  
  
 Questo comando esegue uno script XMLA tramite cui viene restituito l'elenco di connessioni attive nel server. Nel file DiscoverConnections.xmla è contenuto lo script XMLA seguente:  
  
```  
<Discover xmlns="urn:schemas-microsoft-com:xml-analysis">  
<RequestType>DISCOVER_CONNECTIONS</RequestType>  
<Restrictions />  
   <Properties>  
      <PropertyList>  
         <Content>Data</Content>  
      </PropertyList>  
   </Properties>  
</Discover>  
```  
  
## <a name="example-2-tmsl-input-file"></a>Esempio 2 (file di input TMSL)  
 Questo esempio è identico al primo, ma lo script è TMSL (JSON) e richiede un'istanza tabulare di SQL Server 2016. Uno script TMSL può essere generato in SQL Server Management Studio.  
  
 Se si hanno più istanze e l'istanza tabulare è un'istanza denominata, ricordare di impostare il nome del server:  
  
```  
Invoke-ASCmd –InputFile "C:\folder-name\T1200-NewDB.json" -Server "server-name\instance-name"  
```  
  
## <a name="example-3-query"></a>Esempio 3 (Query)  
  
```  
Invoke-ASCmd -Database:"Adventure Works DW" -Query:"<Discover xmlns='urn:schemas-microsoft-com:xml analysis'><RequestType>DISCOVER_DATASOURCES</RequestType><Restrictions></Restrictions><Properties></Properties></Discover>"  
```  
  
 Tramite la query Discover XMLA vengono restituite le origini dati disponibili per Analysis Server e le informazioni richieste per connettersi a esse. I risultati sono in XML. Per una migliore leggibilità, è possibile inviare pipe dell'output a un file XML (ad esempio, accodare `| Out-file C:\Results\XMLAQueryOutput.xml` al comando) e visualizzare i risultati in un browser o in un'altra applicazione che supporta l'XML strutturato.  
  
  
  

