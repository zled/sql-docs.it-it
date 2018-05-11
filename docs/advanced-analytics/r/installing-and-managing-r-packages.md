---
title: Predefinito R e Python librerie del pacchetto in SQL Server R e SQL Server Machine Learning | Documenti Microsoft
description: Pacchetti R e Python installati da SQL Server per R, R Server Machine Learning servizi (In-Database) e Machine Learning Server (Standalone)
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/08/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 48fb451e35f58cf606c47cd64cf5f9093069c274
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="default-r-and-python-packages-in-sql-server"></a>Valore predefinito R e Python pacchetti in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Questo articolo vengono illustrate le librerie di pacchetto, la posizione e le versioni dei pacchetti R e Python installati con SQL Server. 

## <a name="using-the-default-instance-library"></a>Utilizzo della libreria di istanza predefinito

Quando si installa l'apprendimento con SQL Server, una libreria singolo pacchetto viene creata a livello di istanza per ogni lingua da installare. 

Tutti i script o codice che viene eseguito nel database in SQL Server deve caricare le funzioni dalla libreria di istanza. SQL Server non è possibile accedere ai pacchetti installati in altre librerie. Questo vale per i client remoti. Quando ci si connette al server da un client remoto, qualsiasi codice Python o R che si desidera eseguire nel contesto di calcolo server può utilizzare solo i pacchetti installati nella raccolta di istanza.

Per proteggere gli asset di server, la libreria di istanza predefinita viene installata in una cartella protetta che è registrata con SQL Server e può essere modificata solo da un amministratore del computer. Se non si è il proprietario del computer, potrebbe essere necessario ottenere l'autorizzazione dell'amministratore per installare i pacchetti a questa raccolta. 

Anche se si è proprietari del computer, considerare l'utilità di qualsiasi pacchetto R o Python specifico in un ambiente server prima di aggiungere il pacchetto per la libreria di istanza. Considerare ad esempio le dimensioni dei file di pacchetto e la necessità di più versioni, nonché indica se il pacchetto richiede la rete o internet l'accesso.

### <a name="in-database-engine-instance-file-paths"></a>Percorsi dei file di istanza di motore di Database

Nella tabella seguente viene illustrato il percorso del file di R e Python per versione e il database combinazioni di istanza di motore. 

|Versione | Nome istanza|Percorso predefinito|
|--------|--------------|------------|
| SQL Server 2016 |istanza predefinita| C:\Program Files\Microsoft SQL Server\MSSQL13. MSSQLSERVER\R_SERVICES\library|
| SQL Server 2016 |istanza denominata | C:\Program Files\Microsoft SQL Server\MSSQL13. \R_SERVICES\library < instance_name >|
| SQL Server, 2017 con R|istanza predefinita | C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\R_SERVICES\library |
| SQL Server, 2017 con R|istanza denominata| C:\Program Files\Microsoft SQL Server\MSSQL14. MyNamedInstance\R_SERVICES\library |
| SQL Server, 2017 con Python |istanza predefinita | C:\Program Files\Microsoft SQL Server\MSSQL14. MSSQLSERVER\PYTHON_SERVICES\library |
| SQL Server, 2017 con Python|istanza denominata| C:\Program Files\Microsoft SQL Server\MSSQL14. \PYTHON_SERVICES\library < instance_name > |

### <a name="standalone-server-file-paths"></a>Percorsi di file server autonomo 

Nella tabella seguente sono elencati i percorsi predefiniti dei file binari quando è installato SQL Server 2016 R Server (Standalone) o server di SQL Server 2017 Machine Learning Server (Standalone). 

|Versione| Installazione|Percorso predefinito|
|------|------|------|
| SQL Server 2016|R Server (Standalone)| C:\Program Files\Microsoft SQL Server\130\R_SERVER|
|SQL Server 2017|Machine Learning Server, con R |C:\Program Files\Microsoft SQL Server\140\R_SERVER|
|SQL Server 2017|Machine Learning Server, con Python |C:\Program Files\Microsoft SQL Server\140\PYTHON_SERVER|

> [!NOTE]
> Se altre cartelle con nomi simili sottocartella e file, probabilmente è possibile eseguire un'installazione autonoma di Microsoft R Server o [server di Machine Learning](https://docs.microsoft.com/machine-learning-server/). Questi prodotti server hanno percorsi (vale a dire, c:\Programmi\Microsoft Files\Microsoft\R Server\R_SERVER o c:\Programmi\Microsoft Files\Microsoft\ML SERVER\R_SERVER) e i programmi di installazione diversi. Per altre informazioni, vedere [installare Machine Learning per Windows ReportServer](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) oppure [installare R Server 9.1 per Windows](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows).

## <a name="what-is-included-in-a-default-installation"></a>Cosa è incluso in un'installazione predefinita

In questa sezione riepiloga le funzionalità di R e Python inclusa in un'installazione predefinita.

### <a name="r-components"></a>Componenti di R

Open source R è la distribuzione di Microsoft [Microsoft R Open (MRO)](https://mran.microsoft.com/open). Pacchetti di base R includono funzionalità di base, ad esempio **stats** e **utils**. È possibile eseguire `installed.packages(priority = "base")` per restituire un elenco dei pacchetti. Un'installazione di base di R include inoltre numerosi set di dati di esempio e gli strumenti standard di R, ad esempio RGui (un semplice editor interattivo) e RTerm (un prompt dei comandi R).

Includono i pacchetti R proprietaria [RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler) per contesti di calcolo remoto, streaming, esecuzione parallela di funzioni rx per l'importazione dei dati e la trasformazione, modellazione, visualizzazione e analisi. [MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package) aggiunge apprendimento di modellazione in R. Includono altri pacchetti Microsoft [olapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) per la scrittura di istruzioni MDX in R e [sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils) per l'inclusione di script R nelle stored procedure.


|Versione             | Versione di R       | Pacchetti Microsoft    |
|--------------------|-----------------|-----------------------|
| SQL Server 2016 R Services | 3.2.2   | RevoScaleR, sqlrutil  |
| SQL Server 2017 Machine Learning Services| 3.3.3 | RevoScaleR, MicrosoftML, olapR, sqlrutil|

È possibile aggiornare i pacchetti di componenti di R, aggiungere i nuovi pacchetti R e modelli di pre-installati mediante l'associazione ai criteri di supporto del ciclo di vita moderna. Associazione viene modificato il modello di manutenzione. Per impostazione predefinita, dopo l'installazione iniziale, i pacchetti R vengono aggiornati tramite service pack e gli aggiornamenti cumulativi. Altri pacchetti e aggiornamenti di versione completo di componenti di base R sono possibili solo tramite gli aggiornamenti di prodotto (da SQL Server 2016 da SQL Server 2017) o mediante l'associazione R supportano al Server di Microsoft Machine Learning. Per altre informazioni, vedere [aggiornamento R e Python componenti di SQL Server](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

### <a name="python-components"></a>Componenti di Python

SQL Server 2017 aggiunge i componenti di Python. Quando si seleziona l'opzione di linguaggio Python, una distribuzione Anaconda è installata. Oltre alle librerie di codice Python, nell'installazione standard include dati di esempio, unit test e script di esempio. 

I pacchetti Microsoft includono [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) come l'equivalente di Python di RevoScaleR, con lo streaming, esecuzione delle funzioni rx per l'importazione dei dati e trasformazione, modellazione, visualizzazione e analisi parallela. Un altro pacchetto di Python [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) per il training e trasformazioni, analisi di punteggio, text e image ed estrazione di funzioni per la derivazione di valori da dati esistenti.

SQL Server 2017 Machine Learning è la prima versione di R sia Python supportano.

|Versione             | Versione anaconda| Pacchetti Microsoft    |
|--------------------|-----------------|-----------------------|
| SQL Server 2017 Machine Learning Services  | 4.2 su 3.5 Python | revoscalepy, microsoftml |

Dopo l'installazione iniziale, pacchetti Python vengono aggiornati tramite service pack e gli aggiornamenti cumulativi, ma gli aggiornamenti di versione completo sono possibili solo mediante l'associazione supporto Python ai Server di Microsoft Machine Learning. Per altre informazioni, vedere [aggiornamento R e Python componenti di SQL Server](use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

## <a name="administrative-permissions-for-package-installation"></a>Autorizzazioni amministrative per l'installazione del pacchetto

La libreria di pacchetti utilizzata da un'istanza nel database si trova fisicamente nella cartella file di programma dell'istanza di SQL Server. La scrittura in questa posizione richiede le autorizzazioni di amministratore. Tuttavia, SQL Server 2017 offre alcune metodologie aggiuntive per l'installazione del pacchetto che offre a utenti non amministratori la possibilità di aggiungere pacchetti.

+ In SQL Server 2016, l'accesso amministrativo è obbligatorio per una nuova installazione del pacchetto.
+ In SQL Server 2017, è possibile continuare a installare i pacchetti come amministratore per R e Python, e si tratta probabilmente il metodo più semplice. 

    L'istruzione DDL, creare libreria esterna consente all'amministratore di database installare i pacchetti senza utilizzare gli strumenti di R. 

    Se si utilizza la funzionalità di gestione pacchetti per il Server di Machine Learning, è possibile utilizzare RevoScaleR per installare i pacchetti R a livello di database. L'amministratore del database è necessario abilitare la funzionalità e quindi concedere agli utenti la possibilità di installare i propri pacchetti in un singolo database. Per ulteriori informazioni, vedere [abilitare la gestione dei pacchetti tramite DDL](r-package-how-to-enable-or-disable.md).

### <a name="user-libraries-are-not-supported"></a>Librerie utente non sono supportate.

Gli utenti spesso non è possibile installare un pacchetto in un percorso protetto si avvalgono di installazione di un pacchetto in una raccolta di utenti. Tuttavia, non si tratta possibile nell'ambiente di SQL Server. Accesso al file system è in genere limitata nel server, o anche se si dispone di diritti di amministratore e l'accesso in una cartella di documento utente nel server, il runtime dello script esterno che viene eseguita in SQL Server non può accedere tutti i pacchetti installati all'esterno dell'istanza predefinita libreria. Sono tuttavia possibili soluzioni alternative. Per suggerimenti su come risolvere i problemi relativi alle librerie utente, vedere [soluzioni alternative per le librerie utente R](packages-installed-in-user-libraries.md).

## <a name="next-steps"></a>Passaggi successivi

+ [Ottenere informazioni sul pacchetto](determine-which-packages-are-installed-on-sql-server.md)
+ [Installare i nuovi pacchetti R](install-additional-r-packages-on-sql-server.md)
+ [Installare i nuovi pacchetti di Python](../python/install-additional-python-packages-on-sql-server.md)
+ [Abilitare la gestione remota di pacchetti R](r-package-how-to-enable-or-disable.md)
+ [Funzioni RevoScaleR per la gestione dei pacchetti R](use-revoscaler-to-manage-r-packages.md)
+ [Sincronizzazione del pacchetto R](package-install-uninstall-and-sync.md)
+ [miniCRAN per locale del repository di pacchetti R](create-a-local-package-repository-using-minicran.md)
