---
title: Pacchetto di librerie per machine learning in SQL Server predefinite | Documenti Microsoft
ms.custom: ''
ms.date: 02/19/2018
ms.reviewer: ''
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- R
ms.author: heidist
author: HeidiSteen
manager: cgronlun
ms.workload: On Demand
ms.openlocfilehash: 97dc375dcee9dab2eb38c568b410e8ea2084842f
ms.sourcegitcommit: 059fc64ba858ea2adaad2db39f306a8bff9649c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/04/2018
---
# <a name="default-package-libraries-for-machine-learning-on-sql-server"></a>Librerie di pacchetto predefinite per machine learning in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Questo articolo descrive le librerie predefinite per R e Python installati con SQL Server. In questo articolo fornisce i percorsi predefiniti per queste librerie e viene spiegato come è possibile determinare quali pacchetti e la versione di R o Python vengono installati in ogni raccolta di istanza.

## <a name="using-the-default-instance-library"></a>Utilizzo della libreria di istanza predefinito

Quando si installa l'apprendimento con SQL Server, una libreria singolo pacchetto viene creata a livello di istanza per ogni lingua da installare. SQL Server non è possibile accedere ai pacchetti installati in altre librerie.

Se ci si connette al server da un client remoto, qualsiasi codice R o Python che si desidera eseguire nel contesto di calcolo del server può utilizzare solo i pacchetti installati nella libreria di istanza.

Per proteggere gli asset di server, la libreria di istanza predefinita viene installata in una cartella protetta che è registrata con SQL Server e può essere modificata solo da un amministratore del computer. Se non si è il proprietario del computer, potrebbe essere necessario ottenere l'autorizzazione dell'amministratore per installare i pacchetti a questa raccolta. 

Anche se si è proprietari del computer, considerare l'utilità di qualsiasi pacchetto R o Python specifico in un ambiente server prima di aggiungere il pacchetto per la libreria di istanza. Considerare ad esempio le dimensioni dei file di pacchetto e la necessità di più versioni, nonché indica se il pacchetto richiede la rete o internet l'accesso.

### <a name="sql-server"></a>SQL Server

|Version | Nome istanza|Percorso predefinito|
|------|------|------|
| SQL Server 2016 |istanza predefinita|`C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library`|
| SQL Server 2016 |istanza denominata |`C:\Program Files\Microsoft SQL Server\MSSQL13.<instance_name>\R_SERVICES\library`|
| SQL Server, 2017 con R|istanza predefinita |`C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library` |
| SQL Server, 2017 con R|istanza denominata|`C:\Program Files\Microsoft SQL Server\MSSQL14.MyNamedInstance\R_SERVICES\library` |
| SQL Server, 2017 con Python |istanza predefinita |`C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\library` |
| SQL Server, 2017 con Python|istanza denominata|`C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\PYTHON_SERVICES\library` |

### <a name="r-server-standalone-or-machine-learning-server-standalone"></a>R Server (standalone) o Machine Learning Server (Standalone)

Questa tabella elenca i percorsi predefiniti dei file binari quando il server autonomo viene installato tramite il programma di installazione di SQL Server. 

|Version| Installazione|Percorso predefinito|
|------|------|------|
| SQL Server 2016|R Server (Standalone)| |`C:\Program Files\Microsoft SQL Server\130\R_SERVER`|
|SQL Server 2017|Machine Learning Server, con R |`C:\Program Files\Microsoft SQL Server\130\R_SERVER`|
|SQL Server 2017|Machine Learning Server, con Python |`C:\Program Files\Microsoft SQL Server\130\PYTHON_SERVER`|

Se si installa Microsoft R Server o server di Machine Learning tramite il programma di installazione di Windows separato, i percorsi predefiniti sono diversi: in genere, un codice come `C:\Program Files\Microsoft\R Server\R_SERVER`. Per altre informazioni, vedere:
 
+ [Installazione di Machine Learning Server per Windows](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install)
+ [Installare R Server 9.1 per Windows](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows)

## <a name="what-is-included-in-a-default-installation"></a>Cosa è incluso in un'installazione predefinita

In questa sezione fornisce un riepilogo delle funzionalità R o Python che vengono installati per impostazione predefinita.

### <a name="default-r-installation-for-sql-server"></a>Installazione di R predefinito per SQL Server

Per impostazione predefinita l'oggetto R **base** pacchetti installati. Pacchetti di base includono le funzionalità di base fornite da pacchetti come `stats` e `utils`.

Un'installazione di base di R include inoltre numerosi set di dati di esempio e gli strumenti standard di R, ad esempio RGui (un semplice editor interattivo) e RTerm (un prompt dei comandi R).

L'installazione di R in SQL Server 2016 o SQL Server 2017 include inoltre il **RevoScaleR** pacchetto e pacchetti avanzati correlati e i provider che supporta i contesti di calcolo remoto, streaming, l'esecuzione parallela di funzione rx, e molte altre funzionalità.

Per aggiornare il pacchetto RevoScaleR, di utilizzare l'associazione per l'aggiornamento solo di machine learning componenti, patch o aggiornare l'istanza in una versione più recente di SQL Server.

+ Per una panoramica delle funzionalità di R avanzata, vedere [su Machine Learning Server](https://docs.microsoft.com/machine-learning-server/what-is-microsoft-r-server)

+ Per scaricare le librerie RevoScaleR in un computer client, installare [Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client)

### <a name="default-python-installation-for-sql-server"></a>Installazione di Python predefinita per SQL Server

Se si seleziona di machine learning funzionalità e l'opzione di linguaggio Python, una distribuzione Anaconda è installata. La versione esatta varia a seconda della versione di SQL Server è stato installato e se è stato aggiornato l'istanza del programma di installazione del Server di Machine Learning tramite.

|Versione| Versione anaconda| Altre modifiche|
|------|------|------|
| SQL Server 2017 RTM| 3.5.2| Nuovo: revoscalepy|
| aggiornare tramite Machine Learning Server 9.2.1 2017 settembre| Anaconda 4.2| aggiornamenti a revoscalepy |
| SQL Server 2017 CU3| Anaconda 4.2| aggiornamenti a revoscalepy |

Oltre alle librerie di codice Python, nell'installazione standard include dati di esempio, unit test e script di esempio.

## <a name="restrictions-and-known-issues"></a>Limitazioni e problemi noti

Qualsiasi soluzione in esecuzione in SQL Server può utilizzare **solo** pacchetti installati nella libreria predefinita associata all'istanza.

Se si utilizza l'associazione per l'aggiornamento dei componenti R in un'istanza, è possibile modificare il percorso alla libreria di istanza. Assicurarsi di verificare il percorso della libreria attualmente utilizzato da SQL Server.

## <a name="administrative-permissions-required-for-package-installation"></a>Autorizzazioni amministrative necessarie per l'installazione del pacchetto

Le autorizzazioni necessarie per l'installazione del pacchetto sono stati modificati tra SQL Server 2016 e SQL Server 2017.

+ In SQL Server 2016, è necessario per l'installazione di nuovi pacchetti R accesso amministrativo.

+ In SQL Server 2017, è possibile continuare a installare i pacchetti come amministratore per R e Python, e si tratta probabilmente il metodo più semplice.

    L'istruzione DDL, creare libreria esterna consente all'amministratore di database installare i pacchetti senza utilizzare gli strumenti di R. 

    Se si utilizza la funzionalità di gestione pacchetti per il Server di Machine Learning, è possibile utilizzare RevoScaleR per installare i pacchetti R a livello di database. L'amministratore del database è necessario abilitare la funzionalità e quindi concedere agli utenti la possibilità di installare i propri pacchetti in un singolo database. Per ulteriori informazioni, vedere [abilitare la gestione dei pacchetti tramite DDL](r-package-how-to-enable-or-disable.md).

### <a name="user-libraries-are-not-supported"></a>Librerie utente non sono supportate.

Gli utenti spesso non è possibile installare un pacchetto in un percorso protetto si avvalgono di installazione di un pacchetto in una raccolta di utenti. Tuttavia, non si tratta possibile nell'ambiente di SQL Server. Anche accesso al file system è spesso limitato sul server.

Anche se si dispone dei diritti di amministrazione e accesso in una cartella di documento utente sul server, il runtime dello script esterno che viene eseguita in SQL Server non è possibile accedere a tutti i pacchetti installati all'esterno della libreria di istanza predefinito.

Per suggerimenti su come risolvere i problemi relativi alle librerie utente, vedere [pacchetto installato nelle librerie utente](packages-installed-in-user-libraries.md).