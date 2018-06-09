---
title: Predefinito R e Python librerie del pacchetto in SQL Server R e SQL Server Machine Learning | Documenti Microsoft
description: Pacchetti R e Python installati da SQL Server per R, R Server Machine Learning servizi (In-Database) e Machine Learning Server (Standalone)
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/29/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 9362d6e9dc98f80beabc301f43e755b205b40a10
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34707289"
---
# <a name="default-r-and-python-packages-in-sql-server"></a>Valore predefinito R e Python pacchetti in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Questo articolo elenca i pacchetti R e Python installati con SQL Server e dove trovare la libreria di pacchetto.  

## <a name="r-package-list-for-sql-server"></a>Elenco dei pacchetti R per SQL Server

Pacchetti R installati con [R Services di SQL Server 2016](../install/sql-r-services-windows-install.md) e [servizi di SQL Server 2017 Machine Learning](../install/sql-machine-learning-services-windows-install.md) quando si seleziona la funzionalità di R durante l'installazione. 

Pacchetti         | 2016 | 2017 | Description |
|----------------|--------------|--------------|-------------|
| [RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler)  | 8.0.3 | 9.2 | Utilizzato per i contesti di calcolo remoto, l'esecuzione parallela delle funzioni rx per l'importazione dei dati e trasformazione, modellazione, visualizzazione e analisi di flusso. |
| [sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils) | 8.0.3 | 9.2 |Utilizzato per l'inclusione di script R nelle stored procedure. |
| [MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package)| n.a. | 9.2 | Aggiunge gli algoritmi di machine learning in R. | 
| [olapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) | n.a.  | 9.2 | Utilizzato per la scrittura di istruzioni MDX in R. |

MicrosoftML e olapR sono disponibili per impostazione predefinita in servizi di SQL Server 2017 Machine Learning. In un'istanza di SQL Server 2016 R Services, è possibile aggiungere questi pacchetti tramite un [aggiornamento del componente](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md). Un aggiornamento del componente ottiene anche le versioni più recenti dei pacchetti (ad esempio, le versioni più recenti di RevoScaleR includono funzioni per la gestione dei pacchetti in SQL Server).

## <a name="python-package-list-for-sql-server"></a>Elenco dei pacchetti Python per SQL Server

I pacchetti Python sono disponibili solo in SQL Server 2017 quando si installa [servizi di SQL Server 2017 Machine Learning](../install/sql-machine-learning-services-windows-install.md) e selezionare la funzionalità di Python.

| Pacchetti         | 2017    |  Description |
| -----------------|-------------|------------|
| [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) | 9.2 | Utilizzato per i contesti di calcolo remoto, l'esecuzione parallela delle funzioni rx per l'importazione dei dati e trasformazione, modellazione, visualizzazione e analisi di flusso. |
| [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) | 9.2 | Aggiunge gli algoritmi di machine learning in Python. |

## <a name="open-source-r-in-your-installation"></a>Open source R nell'installazione di

Supporto di R open source di include sono, in modo che è possibile chiamare le funzioni di base R e installare pacchetti open source e di terze parti aggiuntivi. Supporto del linguaggio R include funzionalità di base quali **base**, **stats**, **utils**e altri utenti. Un'installazione di base di R include inoltre numerosi set di dati di esempio e gli strumenti standard di R, ad esempio **RGui** (un semplice editor interattivo) e **RTerm** (un prompt dei comandi R). 

La distribuzione di R open source incluso nell'installazione di [aprire R Microsoft (MRO)](https://mran.microsoft.com/open). MRO aggiunge valore di base R includendo pacchetti open source aggiuntivi, ad esempio il [libreria del Kernel matematico di Intel](https://en.wikipedia.org/wiki/Math_Kernel_Library).

Nella tabella seguente sono riepilogate le versioni di R forniti da MRO utilizzando il programma di installazione di SQL Server.

|Versione             | Versione di R       |
|--------------------|-----------------|
| [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md) | 3.2.2   | 
| [SQL Server 2017 macchina Learning Services](../install/sql-machine-learning-services-windows-install.md) | 3.3.3 |

È necessario sovrascrivere mai manualmente la versione di R installato dal programma di installazione di SQL Server con le versioni più recenti sul web. Pacchetti R Microsoft si basano sul versioni specifiche di R. modificare l'installazione potrebbe destabilizzare il.

## <a name="open-source-python-in-your-installation"></a>Open source Python nell'installazione di

SQL Server 2017 aggiunge i componenti di Python. Quando si seleziona l'opzione di linguaggio Python, installazione della distribuzione Anaconda 4.2. Oltre alle librerie di codice Python, nell'installazione standard include dati di esempio, unit test e script di esempio. 

SQL Server 2017 Machine Learning è la prima versione di R sia Python supportano.

|Versione             | Versione anaconda| Pacchetti Microsoft    |
|--------------------|-----------------|-----------------------|
| SQL Server 2017 Machine Learning Services  | 4.2 su 3.5 Python | revoscalepy, microsoftml |

È necessario sovrascrivere mai manualmente la versione di Python installato dal programma di installazione di SQL Server con le versioni più recenti sul web. Pacchetti Python di Microsoft si basano su versioni specifiche di Anaconda. Modificare l'installazione potrebbe destabilizzare il.

## <a name="component-upgrades"></a>Aggiornamenti dei componenti

Dopo l'installazione iniziale, i pacchetti R e Python vengono aggiornati tramite service pack e gli aggiornamenti cumulativi, ma sono possibili dal solo aggiornamenti di versione completo *associazione* ai criteri di supporto del ciclo di vita moderna. Associazione viene modificato il modello di manutenzione. Per impostazione predefinita, dopo l'installazione iniziale, i pacchetti R vengono aggiornati tramite service pack e gli aggiornamenti cumulativi. Altri pacchetti e aggiornamenti di versione completo di componenti di base R sono possibili solo tramite gli aggiornamenti di prodotto (da SQL Server 2016 da SQL Server 2017) o mediante l'associazione R supportano al Server di Microsoft Machine Learning. Per altre informazioni, vedere [aggiornamento R e Python componenti di SQL Server](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

## <a name="package-library-location"></a>Percorso di libreria del pacchetto

Quando si installa l'apprendimento con SQL Server, una libreria singolo pacchetto viene creata a livello di istanza per ogni lingua da installare. In Windows, la libreria di istanza è una cartella protetta registrata con SQL Server.

Tutti i script o codice che viene eseguito nel database in SQL Server deve caricare le funzioni dalla libreria di istanza. SQL Server non è possibile accedere ai pacchetti installati in altre librerie. Questo vale per i client remoti. Quando ci si connette al server da un client remoto, qualsiasi codice Python o R che si desidera eseguire nel contesto di calcolo server può utilizzare solo i pacchetti installati nella raccolta di istanza.

Per proteggere gli asset di server, la libreria di istanza predefinita può essere modificata solo da un amministratore del computer. Se non si è il proprietario del computer, potrebbe essere necessario ottenere l'autorizzazione dell'amministratore per installare i pacchetti a questa raccolta. 

#### <a name="file-path-for-in-database-engine-instances"></a>Percorso del file per le istanze del motore In-Database

Nella tabella seguente viene illustrato il percorso del file di R e Python per versione e il database combinazioni di istanza di motore. MSSQL13 indica SQL Server 2016 ed è solo per R. MSSQL14 indica 2017 di SQL Server e sono presenti cartelle R e Python. 

I percorsi di file includono anche i nomi delle istanze. SQL Server viene installato [le istanze del motore di database](../../database-engine/configure-windows/database-engine-instances-sql-server.md) come istanza predefinita (MSSQLSERVER) o come istanza denominata definita dall'utente. Se SQL Server viene installato come istanza denominata, verrà visualizzato tale nome aggiunto come indicato di seguito: `MSSQL13.<instance_name>`.

|Versione e della lingua  | Percorso predefinito|
|----------------------|------------|
| SQL Server 2016 |C:\Program Files\Microsoft SQL Server\MSSQL13. MSSQLSERVER\R_SERVICES\library|
| SQL Server, 2017 con R|C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\R_SERVICES\library |
| SQL Server, 2017 con Python |C:\Program Files\Microsoft SQL Server\MSSQL14. Pacchetti MSSQLSERVER\PYTHON_SERVICES\Lib\site |


#### <a name="file-path-for-standalone-server-installations"></a>Percorso del file per le installazioni di server autonomi

Nella tabella seguente sono elencati i percorsi predefiniti dei file binari quando è installato SQL Server 2016 R Server (Standalone) o server di SQL Server 2017 Machine Learning Server (Standalone). 

|Versione| Installazione|Percorso predefinito|
|-------|-------------|------------|
| SQL Server 2016|R Server (Standalone)| C:\Program Files\Microsoft SQL Server\130\R_SERVER|
|SQL Server 2017|Machine Learning Server, con R |C:\Program Files\Microsoft SQL Server\140\R_SERVER|
|SQL Server 2017|Machine Learning Server, con Python |C:\Program Files\Microsoft SQL Server\140\PYTHON_SERVER|

> [!NOTE]
> Se altre cartelle con nomi simili sottocartella e file, probabilmente è possibile eseguire un'installazione autonoma di Microsoft R Server o [server di Machine Learning](https://docs.microsoft.com/machine-learning-server/). Questi prodotti server hanno percorsi (vale a dire, c:\Programmi\Microsoft Files\Microsoft\R Server\R_SERVER o c:\Programmi\Microsoft Files\Microsoft\ML SERVER\R_SERVER) e i programmi di installazione diversi. Per altre informazioni, vedere [installare Machine Learning per Windows ReportServer](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) oppure [installare R Server 9.1 per Windows](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows).

## <a name="next-steps"></a>Passaggi successivi

+ [Ottenere informazioni sui pacchetti](determine-which-packages-are-installed-on-sql-server.md)
+ [Installare nuovi pacchetti R](install-additional-r-packages-on-sql-server.md)
+ [Installare nuovi pacchetti Python](../python/install-additional-python-packages-on-sql-server.md)
+ [Abilitare la gestione remota dei pacchetti R](r-package-how-to-enable-or-disable.md)
+ [Funzioni RevoScaleR per la gestione dei pacchetti R](use-revoscaler-to-manage-r-packages.md)
+ [Sincronizzazione dei pacchetti R](package-install-uninstall-and-sync.md)
+ [miniCRAN per il repository locale di pacchetti R](create-a-local-package-repository-using-minicran.md)
