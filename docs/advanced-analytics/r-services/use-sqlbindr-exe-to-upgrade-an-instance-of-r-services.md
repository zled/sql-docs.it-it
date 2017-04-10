---
title: "Usare sqlBindR.exe per aggiornare un&#39;istanza di R Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server (starting with 2016 CTP3)"
ms.assetid: 4da80998-f929-4fad-a86f-87d09c1a79ef
caps.latest.revision: 15
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 8
---
# Usare sqlBindR.exe per aggiornare un&#39;istanza di R Services
Microsoft R Server per Windows contiene un nuovo strumento, denominato **SqlBindR.exe**, che può essere usato per aggiornare i componenti R per un'istanza. Questo processo è definito **associazione** perché modifica il modello di licenza per un'istanza di SQL Server 2016 in modo da usare la nuova licenza del supporto Microsoft basata sui criteri relativi al ciclo di vita moderni.

In generale, con questo sistema di licenza si ha la sicurezza che i data scientist usino sempre la versione più recente di R. Per altre informazioni sulle condizioni e sui vantaggi della licenza software Microsoft, vedere [Run Microsoft R Server for Windows](https://msdnstage.redmond.corp.microsoft.com/en-us/microsoft-r/rserver-install-windows?branch=r-server-nov16-dev) (Eseguire Microsoft R Server per Windows).

Quando si associa un'istanza, vengono eseguite tre operazioni:
+ I criteri di supporto per l'istanza vengono modificati: quelli di SQL Server 2016 vengono sostituiti dal nuovo contratto di licenza software Microsoft basato su criteri moderni.
+ I componenti R associati all'istanza vengono aggiornati automaticamente con ogni versione, parallelamente alla versione corrente di R Server secondo le nuove condizioni del contratto di licenza software basato su criteri moderni.
+ L'istanza non può più essere aggiornata manualmente, se non per aggiungere nuovi pacchetti. 

Se successivamente si decide di interrompere l'aggiornamento dell'istanza in base a ogni versione, è necessario **disassociare** l'istanza e quindi disinstallare i componenti di Microsoft R Server come descritto in questo articolo: [Run Microsoft R Server for Windows](https://msdn.microsoft.com/microsoft-r/rserver-install-windows) (Eseguire Microsoft R Server per Windows). Al termine del processo, gli aggiornamenti successivi di R Server non avranno più effetto sull'istanza.

> [!NOTE] Il processo di aggiornamento è supportato solo per le istanze di SQL Server 2016 a cui è stata applicata una patch con l'aggiornamento cumulativo 3.0.  
> 
> Se si usa R Services in SQL Server vNext, non è necessario applicare questo aggiornamento. I componenti R vengono sempre aggiornati automaticamente ogni volta che viene eseguita un'attività cardine.

## <a name="how-to-upgrade-an-instance"></a>Come aggiornare un'istanza


1. Eseguire il programma di installazione per Microsoft R Server nel computer in cui è presente l'istanza da aggiornare.
2. Al termine l'installazione, individuare la cartella contenente lo strumento, **SqlBindR.exe**. Il percorso predefinito è: `C:\Program Files\Microsoft\R Server\Setup`
2. Aprire un prompt dei comandi come amministratore.
3. Digitare il comando seguente per visualizzare un elenco delle istanze disponibili: `SqlBindR.exe /list`
4. Eseguire il comando **SqlBindR.exe** con l'argomento */bind* per specificare il nome dell'istanza da aggiornare. 
   Ad esempio, per aggiornare solo l'istanza predefinita, digitare:  `SqlBindR.exe /bind MSSQL14.MSSQLSERVER`

## <a name="how-to-downgrade-an-instance-of-r-services"></a>Come effettuare il downgrade di un'istanza di R Services

Per ripristinare lo stato di un'istanza, è necessario eseguire lo strumento SqlBindR per rimuovere le licenze e quindi ripristinare o reinstallare l'istanza.

1. Eseguire il comando **SqlBindR.exe** con l'argomento */unbind* e specificare l'istanza. 
   Ad esempio, il comando seguente ripristina l'istanza predefinita per garantire la conformità con le licenze e la pianificazione degli aggiornamenti di SQL Server:  `SqlBindR.exe /unbind MSSQL14.MSSQLSERVER`
2. Ripristinare lo stato originale dell'istanza effettuando una delle operazioni seguenti:
    + Ripristinare l'istanza. L'operazione di ripristino applicherà gli aggiornamenti a tutte le funzionalità installate.
    + Disinstallare e reinstallare e quindi applicare tutte le versioni del servizio. L'istanza deve essere riavviata.
3. Dopo che R Server è stato rimosso, anche tutti i pacchetti che sono stati installati con l'istanza vengono rimossi e devono quindi essere reinstallati.

## <a name="requirements"></a>Requisiti
L'aggiornamento è supportato solo per le istanze di SQL Server 2016 che soddisfano i requisiti seguenti:
+ SQL Server 2016 SP1 o versione successiva
+ Aggiornamento cumulativo 3.0 (OD) applicato

L'aggiornamento è attualmente supportato solo tramite lo strumento da riga di comando. In una versione successiva sarà disponibile un'interfaccia interattiva.

## <a name="sqlbindrexe-command-syntax"></a>Sintassi del comando sqlbindr.exe


### <a name="usage"></a>Utilizzo

`sqlbindr [/list] [/bind <SQL_instance_ID>] [/unbind <SQL_instance_ID>]`

### <a name="parameters"></a>Parametri

|Nome|Descrizione|
|------|------|
|*list*| Visualizza un elenco di tutti gli ID delle istanze di database SQL nel computer corrente|
|*bind*| Aggiorna l'istanza di database SQL specificata alla versione più recente di R Server e assicura che all'istanza vengano applicati automaticamente gli aggiornamenti successivi di R Server|
|*unbind*|Disinstalla la versione più recente di R Server dall'istanza di database SQL specificata e impedisce l'applicazione degli aggiornamenti successivi di R Server|

### <a name="errors"></a>Errori

La query restituisce i messaggi di errore seguenti:

|Errore|Soluzione|
|------|------|
|An error occurred while binding the instance (Si è verificato un errore durante l'associazione dell'istanza)| Non è stato possibile associare l'istanza. Contattare il supporto tecnico.|
|The instance is already bound (L'istanza è già associata)| È stato eseguito il comando *bind*, ma l'istanza specificata è già associata. Scegliere un'istanza diversa.|
|The instance is not bound (L'istanza non è associata)| È stato eseguito il comando *unbind*, ma l'istanza specificata non è associata. Scegliere un'istanza diversa.|
|Not a valid SQL instance ID (L'ID dell'istanza SQL non è valido)| È possibile che il nome di istanza digitato non sia corretto. Eseguire nuovamente il comando con l'argomento *list* per visualizzare gli ID di istanza disponibili.|
|No instances found (Non è stata trovata alcuna istanza)| In questo computer non è presente un'istanza di SQL Server R Services.|
|Nell'istanza deve essere installata una versione compatibile di SQL R Services (In-Database).| Per informazioni più dettagliate, vedere https://go.microsoft.com/fwlink/?linkid=835761|
|An error occurred while unbinding the instance (Si è verificato un errore durante l'annullamento dell'associazione dell'istanza)| Non è stato possibile disassociare l'istanza. Contattare il supporto tecnico.|
|An unexpected error has occurred (Si è verificato un errore imprevisto)| Si sono verificati altri errori. Contattare il supporto tecnico.  |
|No SQL instances found (Non è stata trovata alcuna istanza di SQL)| In questo computer non è presente un'istanza di SQL Server. |


## <a name="see-also"></a>Vedere anche

[R Server Release Notes](https://msdn.microsoft.com/microsoft-r/notes/r-server-notes) (Note sulla versione di R Server)
