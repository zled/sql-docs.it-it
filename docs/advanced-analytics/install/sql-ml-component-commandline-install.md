---
title: Installazione dei componenti di SQL Server machine learning della riga di comando | Documenti Microsoft
ms.custom: 
ms.date: 03/15/2018
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
caps.latest.revision: 
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.workload: Inactive
ms.openlocfilehash: c51d8299837f0eda02a07afe1ea4d34d3ecd5e31
ms.sourcegitcommit: 8e897b44a98943dce0f7129b1c7c0e695949cc3b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/21/2018
---
# <a name="install-sql-server-machine-learning-components-from-the-command-line"></a>Installare i componenti di SQL Server machine learning dalla riga di comando
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In questo articolo vengono fornite istruzioni per intalling SQL Server di apprendimento automatico dei componenti dalla riga di comando:

+ [Istanza di database](#indb)
+ [Aggiungere a un'istanza di motore di database esistente](#add-existing)
+ [Installazione invisibile all'utente](#silent)
+ [Server autonomo](#shared-feature)

È possibile specificare l'interazione automatica, base o completa con l'interfaccia utente di installazione. Questo articolo integra [installazione di SQL Server dal Prompt dei comandi](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md), i parametri univoci per i componenti della formazione macchina R e Python di copertura.

## <a name="pre-install-checklist"></a>Elenco di controllo pre-installazione

+ Eseguire i comandi da un prompt dei comandi con privilegi elevati. 

+ Un'istanza del motore di database è obbligatorio per le installazioni nel database. È possibile installare solo le funzionalità di Python o R, sebbene sia possibile [aggiungerli in modo incrementale a un'istanza esistente](#add-existing). Se si desidera semplicemente R e Python senza il motore di database, installare il [server autonomo](#shared-feature).

+ Non installare in un cluster di failover. Il meccanismo di sicurezza utilizzato per isolare i processi R e Python non è compatibile con un ambiente cluster di failover di Windows Server.

+ Non installare un controller di dominio. La parte di Machine Learning Services del programma di installazione avrà esito negativo.

+ Evitare l'installazione autonoma e le istanze nel database nello stesso computer. Un server autonomo competono per le stesse risorse, indebolendo le prestazioni di entrambe le installazioni.


## <a name="command-line-arguments"></a>Argomenti della riga di comando

L'argomento di funzionalità è obbligatorio, poiché sono termini contratti di licenza. 

In caso di installazione dal prompt dei comandi, in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è supportata la modalità non interattiva completa tramite il parametro /Q o la modalità non interattiva semplice tramite il parametro /QS. L'opzione /QS indica semplicemente lo stato di avanzamento, non accetta alcun input e non consente di visualizzare eventuali messaggi di errore. Il parametro /QS è supportato solo quando viene specificato /Action=install.

| Argomenti | Description |
|-----------|-------------|
| / FEATURES = AdvancedAnalytics | Installa la versione in-database: SQL Server 2017 Machine Learning Services (In-Database) o SQL Server 2016 R Services (In-Database).  |
| /FEATURES = SQL_INST_MR | Si applica a SQL Server 2017. Abbinato a AdvancedAnalytics. Installa la funzionalità (In-Database) R, tra cui Microsoft R Open e i pacchetti R proprietari. La funzionalità di SQL Server 2016 R Services è R-only, pertanto non esiste alcun parametro di quella versione.|
| /FEATURES = SQL_INST_MPY | Si applica a SQL Server 2017. Abbinato a AdvancedAnalytics. Installa la funzionalità di Python (In-Database), compresi Anaconda e i pacchetti Python proprietari. |
| /FEATURES = SQL_SHARED_MR | Viene installata la funzionalità di R per la versione autonoma: SQL Server 2017 Machine Learning Server (Standalone) o SQL Server 2016 R Server (Standalone). Un server autonomo è una "funzionalità condivise" non è associata a un'istanza del motore di database.|
| /FEATURES = SQL_SHARED_MPY | Si applica a SQL Server 2017. Viene installata la funzionalità di Python per la versione autonoma: SQL Server 2017 Machine Learning Server (Standalone). Un server autonomo è una "funzionalità condivise" non è associata a un'istanza del motore di database.|
| /IACCEPTROPENLICENSETERMS  | Indica che si abbia accettato le condizioni di licenza per l'utilizzo di componenti di R open origine. |
| / IACCEPTPYTHONLICENSETERMS | Indica che si abbia accettato le condizioni di licenza per l'utilizzo dei componenti di Python. |
| /IACCEPTSQLSERVERLICENSETERMS | Indica che si abbia accettato le condizioni di licenza per l'utilizzo di SQL Server.|
| / MRCACHEDIRECTORY | Per l'installazione offline, imposta la cartella contenente i file CAB del componente R. |
| /MPYCACHEDIRECTORY | Per l'installazione offline, imposta la cartella contenente i file CAB del componente Python. |


## <a name="indb"></a> Installazioni di istanze nel database

Analitica nel database è disponibili per le istanze del motore di database, necessari per l'aggiunta di **AdvancedAnalytics** funzionalità per l'installazione. È possibile installare un'istanza del motore di database con avanzate analitica, o [aggiungerlo a un'istanza esistente](#add-existing). 

Per visualizzare le informazioni sullo stato senza l'oggetto interattivo sullo schermo prompt, usare l'argomento /qs.

> [!Important]
> Dopo l'installazione, due ulteriori passaggi di configurazione rimangono. Integrazione non è completa fino a quando non vengono eseguite queste attività. Vedere [attività post-installazione](#post-install) per istruzioni.

### <a name="sql-server-2017-database-engine-advanced-analytics-with-python-and-r"></a>SQL Server 2017: motore di database advanced analitica con Python e R

Per un'installazione simultanea dell'istanza del motore di database, specificare il nome dell'istanza e un account di accesso di amministratore (Windows). Include funzionalità per l'installazione dei componenti di base e i componenti del linguaggio, nonché accettazione di tutte le condizioni di licenza.

```  
Setup.exe /qs /ACTION=Install /FEATURES=SQLEngine,ADVANCEDANALYTICS,SQL_INST_MR,SQL_INST_MPY
/INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="<Windows-username>" 
/IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS /IACCEPTPYTHONLICENSETERMS
```

Questo stesso comando, ma con un account di accesso di SQL Server in un motore di database tramite autenticazione mista.

```
Setup.exe /q /ACTION=Install /FEATURES=SQLEngine,ADVANCEDANALYTICS,SQL_INST_MR,SQL_INST_MPY
/INSTANCENAME=MSSQLSERVER /SECURITYMODE=SQL /SAPWD="%password%" /SQLSYSADMINACCOUNTS="<sql-username>" 
/IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS /IACCEPTPYTHONLICENSETERMS
```

In questo esempio è Python, che mostra che è possibile aggiungere una lingua omettendo una funzionalità.

```  
Setup.exe /qs /ACTION=Install /FEATURES=SQLEngine,ADVANCEDANALYTICS,SQL_INST_MPY 
/INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="<username>" 
/IACCEPTSQLSERVERLICENSETERMS  /IACCEPTPYTHONLICENSETERMS
```

### <a name="sql-server-2016-database-engine-and-advanced-analytics-with-r"></a>SQL Server 2016: motore di database e avanzate analitica con R

Questo comando è identico a SQL Server 2017, ma senza gli elementi di Python, che non sono disponibili nel programma di installazione di SQL Server 2016.

```  
Setup.exe /qs /ACTION=Install /FEATURES=SQLEngine,ADVANCEDANALYTICS,SQL_INST_MR
/INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="<Windows-username>" 
/IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS 
```

## <a name="post-install"></a> Configurazione post-installazione (obbligatorio)

Si applica alle installazioni solo nel database.

Al termine dell'installazione, è un'istanza del motore di database con i pacchetti R e Python, Microsoft R e Python, Microsoft R Open, Anaconda, strumenti, gli esempi e script che fanno parte della distribuzione. 

Per completare l'installazione sono necessarie due operazioni:

1. Riavviare il servizio motore di database.

1. Abilitare gli script esterni prima di poter usare la funzionalità. Seguire le istruzioni in [installare SQL Server 2017 Machine Learning Services (In-Database)](sql-machine-learning-services-windows-install.md) come il passaggio successivo. 

Per SQL Server 2016, in alternativa, usare questo articolo [installare SQL Server 2016 R Services (In-Database)](sql-r-services-windows-install.md).

## <a name="add-existing"></a> Aggiungere analitica avanzate a un'istanza di motore di database esistente

Quando si aggiungono analitica avanzate nel database a un'istanza di motore di database esistente, specificare il nome dell'istanza. Ad esempio, se si è precedentemente installato un motore di database di SQL Server 2017 e Python, è possibile utilizzare questo comando per aggiungere R.

```  
Setup.exe /qs /ACTION=Install /FEATURES=SQL_INST_MR /INSTANCENAME=MSSQLSERVER 
/IACCEPTSQLSERVERLICENSETERMS  /IACCEPTROPENLICENSETERMS
```



## <a name="silent"></a> Installazione invisibile all'utente

Un'installazione invisibile all'utente elimina il controllo per i percorsi di file con estensione cab. Per questo motivo, è necessario specificare il percorso in cui devono essere decompresso file con estensione cab. È possibile la directory temporanea per questo oggetto.
 
```  
Setup.exe /q /ACTION=Install /FEATURES=SQLEngine,ADVANCEDANALYTICS,SQL_INST_MR,SQL_INST_MPY 
/INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="<username>" 
/IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS /IACCEPTPYTHONLICENSETERMS 
/MRCACHEDIRECTORY=%temp% /MPYCACHEDIRECTORY=%temp%
```

## <a name="shared-feature"></a> Installazioni di server autonomi

Un server autonomo è una "funzionalità condivise" non è associata a un'istanza del motore di database. Gli esempi seguenti mostrano la sintassi valida per entrambe le versioni.

SQL Server 2017 supporta Python e R in un server autonomo:

```
Setup.exe /q /ACTION=Install /FEATURES=SQL_SHARED_MR,SQL_SHARED_MPY  
/IACCEPTROPENLICENSETERMS /IACCEPTPYTHONLICENSETERMS /IACCEPTSQLSERVERLICENSETERMS
```

SQL Server 2016 è solo per R:

```
Setup.exe /q /ACTION=Install /FEATURES=SQL_SHARED_MR 
/IACCEPTROPENLICENSETERMS /IACCEPTSQLSERVERLICENSETERMS
```

Al termine dell'installazione, si dispone di un server, pacchetti Microsoft, le distribuzioni di open source di R e Python, strumenti, esempi e script che fanno parte della distribuzione. 

Per aprire una finestra della console di R, passare a \Programmi\Microsoft SQL Server\140 (o 130) \R_SERVER\bin\x64 e fare doppio clic su **RGui.exe**. Non si ha familiarità con R? Questa esercitazione: [comandi R di base e le funzioni RevoScaleR: 25 sono esempi comuni](https://docs.microsoft.com/en-us/machine-learning-server/r/tutorial-r-to-revoscaler).

Per aprire un comando di Python, andare a \Programmi\Microsoft SQL Server\140\PYTHON_SERVER\bin\x64 e fare doppio clic su **python.exe**.

## <a name="get-help"></a>Supporto

Assistenza sull'installazione o aggiornamento? Per le risposte alle domande più comuni e sui problemi noti, vedere l'articolo seguente:

* [Aggiornamento e l'installazione domande frequenti - servizi di Machine Learning](../r/upgrade-and-installation-faq-sql-server-r-services.md)

Per controllare lo stato di installazione dell'istanza e risolvere i problemi più comuni, provare a questi report personalizzati.

* [Report personalizzati per SQL Server R Services](../r/monitor-r-services-using-custom-reports-in-management-studio.md)

## <a name="next-steps"></a>Passaggi successivi

Gli sviluppatori R possono iniziare a usare alcuni semplici esempi e apprendere le nozioni di base del funzionamento di R con SQL Server. Per il passaggio successivo, vedere i collegamenti seguenti:

+ [Esercitazione: Esecuzione di R in T-SQL](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)
+ [Esercitazione: In-database analitica per gli sviluppatori R](../tutorials/sqldev-in-database-r-for-sql-developers.md)

Gli sviluppatori di Python possono imparare a usare Python con SQL Server seguendo queste esercitazioni:

+ [Esercitazione: Esecuzione di Python in T-SQL](../tutorials/run-python-using-t-sql.md)
+ [Esercitazione: In-database analitica per sviluppatori Python](../tutorials/sqldev-in-database-python-for-sql-developers.md)

Per visualizzare gli esempi di machine learning basato su scenari reali, vedere [Machine learning esercitazioni](../tutorials/machine-learning-services-tutorials.md).