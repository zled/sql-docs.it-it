---
title: Installare i componenti di apprendimento di SQL Server senza accesso a internet | Documenti Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/02/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 3a340acfbbcf19a6015e3b2745b1f6089e12d3fd
ms.sourcegitcommit: cfe5b2af733e7801558b441b4b9427cfe4c26435
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/06/2018
ms.locfileid: "34822194"
---
# <a name="install-sql-server-machine-learning-components-without-internet-access"></a>Installare i componenti senza accesso a internet di apprendimento automatico SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Per impostazione predefinita, i programmi di installazione connettersi ai siti di download Microsoft per ottenere necessarie e i componenti aggiornati per machine learning in SQL Server. Se i vincoli del firewall impediscono l'installazione di raggiungere questi siti, è possibile utilizzare un dispositivo connesso a internet per scaricare i file, trasferire i file in un server offline e quindi eseguire l'installazione.

## <a name="get-the-installation-media"></a>Ottenere il supporto di installazione

[!INCLUDE[GetInstallationMedia](../../includes/getssmedia.md)]

> [!NOTE]  
> Per le installazioni locali è necessario eseguire il programma di installazione come amministratore. Se si installa [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da una condivisione remota, è necessario utilizzare un account di dominio con autorizzazioni di lettura ed esecuzione relative a tale condivisione.  
 
 ###  <a name="bkmk_ga_instalpatch"></a> Requisito di installazione patch 

Microsoft ha rilevato un problema con una versione specifica dei file binari di Microsoft VC++ 2013 Runtime installati come prerequisito da SQL Server. Se l'aggiornamento dei file binari di VC++ Runtime non viene installato, potrebbero verificarsi problemi di stabilità di SQL Server in determinati scenari. Prima di installare SQL Server, seguire le istruzioni in [Note sulla versione di SQL Server](../../sql-server/sql-server-2016-release-notes.md#bkmk_ga_instalpatch) per vedere se il computer richiede una patch per i file binari di VC++ Runtime.  


## <a name="download-cab-files"></a>Scaricare i file con estensione cab

In un server connesso a internet, scaricano i file con estensione CAB necessari per un'installazione offline. Il programma di installazione utilizza i file con estensione CAB per installare le funzionalità aggiuntive.

Versione  |Collegamento di download  |
---------|---------|
**Versione iniziale di SQL Server 2017** |
Microsoft R Open     |[SRO_3.3.3.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851496)|
Microsoft R Server      |[SRS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851507)|
Aprire Microsoft Python     |[SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502) |
Server Microsoft Python    |[SPS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851508) |
**SQL Server 2017 CU1** |
Microsoft R Open     |Nessuna modifica. Utilizzare precedente|
Microsoft R Server      |[SRS_9.2.0.100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851501)|
Aprire Microsoft Python     |Nessuna modifica. Utilizzare precedente |
Server Microsoft Python    |[SPS_9.2.0.100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851500) |
**SQL Server 2017 CU2** |
Microsoft R Open     |Nessuna modifica. Utilizzare precedente|
Microsoft R Server      |Nessuna modifica. Utilizzare precedente|
Aprire Microsoft Python     |Nessuna modifica. Utilizzare precedente|
Server Microsoft Python    |Nessuna modifica. Utilizzare precedente|
**SQL Server 2017 CU3** |
Microsoft R Open     |[SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)|
Microsoft R Server      |[SRS_9.2.0.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863893)|
Aprire Microsoft Python     |Nessuna modifica. Utilizzare precedente|
Server Microsoft Python    |[SPS_9.2.0.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863892)|
**SQL Server 2017 CU4** |
Microsoft R Open     |Nessuna modifica. Utilizzare precedente|
Microsoft R Server      |[SRS_9.2.0.400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866212&clcid=1033)|
Aprire Microsoft Python     |Nessuna modifica. Utilizzare precedente|
Server Microsoft Python    |[SPS_9.2.0.400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866213&clcid=1033)|
**SQL Server 2017 CU5** |
Microsoft R Open     |Nessuna modifica. Utilizzare precedente|
Microsoft R Server      |[SRS_9.2.0.500_1033.cab](https://go.microsoft.com/fwlink/?LinkId=869052&clcid=1033)|
Aprire Microsoft Python     |Nessuna modifica. Utilizzare precedente|
Server Microsoft Python    |[SPS_9.2.0.500_1033.cab](https://go.microsoft.com/fwlink/?LinkId=869053&clcid=1033)|
**SQL Server 2017 CU6** |
Microsoft R Open     |Nessuna modifica. Utilizzare precedente|
Microsoft R Server      |[SRS_9.2.0.600_1033.cab](https://go.microsoft.com/fwlink/?LinkId=871074&clcid=1033)|
Aprire Microsoft Python     |Nessuna modifica. Utilizzare precedente|
Server Microsoft Python    |[SPS_9.2.0.600_1033.cab](https://go.microsoft.com/fwlink/?LinkId=871073&clcid=1033)|
**SQL Server 2017 CU7** |
Microsoft R Open     |Nessuna modifica. Utilizzare precedente|
Microsoft R Server      |Nessuna modifica. Utilizzare precedente|
Aprire Microsoft Python     |Nessuna modifica. Utilizzare precedente|
Server Microsoft Python    |Nessuna modifica. Utilizzare precedente|


### <a name="bkmk_2016Installers"></a>Download di SQL Server 2016

> [!IMPORTANT]
> 
> Quando si installa SQL Server 2016 SP1 CU4 o CU5 SP1 offline, è possibile scaricare SRO_3.2.2.16000_1033.cab. Se hai scaricato SRO_3.2.2.13000_1033.cab da FWLINK 831785 come indicato nella finestra di dialogo programma di installazione, rinominare il file come SRO_3.2.2.16000_1033.cab prima di installare l'aggiornamento cumulativo.

Versione  |Collegamento di download  |
---------|---------|
**SQL Server 2016 RTM**     |
Microsoft R Open     |[SRO_3.2.2.803_1033.cab](https://go.microsoft.com/fwlink/?LinkId=761266)
Microsoft R Server     |[SRS_8.0.3.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=735051)
**SQL Server 2016 CU 1**     |
Microsoft R Open     |[SRO_3.2.2.10000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=808803)
Microsoft R Server     |[SRS_8.0.3.10000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=808805)
**SQL Server 2016 CU 2**     |
Microsoft R Open     |[SRO_3.2.2.12000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=827398)
Microsoft R Server     |[SRS_8.0.3.12000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=827399)
**SQL Server 2016 CU 3**     |
Microsoft R Open     |Nessuna modifica. Utilizzare precedente|
Microsoft R Server     | Nessuna modifica. Utilizzare precedente |
**SQL Server 2016 CU 4**     |
Microsoft R Open     |[SRO_3.2.2.13000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=831785)|
Microsoft R Server     |[SRS_8.0.3.13000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=831676)|
**SQL Server 2016 CU 5**     |
Microsoft R Open     |Nessuna modifica. Utilizzare precedente|
Microsoft R Server     |Nessuna modifica. Utilizzare precedente|
**SQL Server 2016 CU 6**     |
Microsoft R Open     |Nessuna modifica. Utilizzare precedente|
Microsoft R Server     |[SRS_8.0.3.14000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=850316)  |
**SQL Server 2016 CU 7**     |
Microsoft R Open     |Nessuna modifica. Utilizzare precedente|
Microsoft R Server     |Nessuna modifica. Utilizzare precedente |
**SQL Server 2016 SP 1**     |
Microsoft R Open     |[SRO_3.2.2.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824879)
Microsoft R Server     |[SRS_8.0.3.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824881)
**SQL Server 2016 SP 1 CU1**     |
Microsoft R Open     |Nessuna modifica. Utilizzare precedente|
Microsoft R Server     |Nessuna modifica. Utilizzare precedente|
**SQL Server 2016 SP 1 CU2**     |
Microsoft R Open     |[SRO_3.2.2.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836819)|
Microsoft R Server    |[SRS_8.0.3.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836818)|
**SQL Server 2016 SP 1 CU3**     |
Microsoft R Open     |Nessuna modifica. Utilizzare precedente|
Microsoft R Server     |Nessuna modifica. Utilizzare precedente|
**GDR e SQL Server 2016 SP 1 CU4**     |
Microsoft R Open     |Nessuna modifica. Utilizzare precedente|
Microsoft R Server    |[SRS_8.0.3.17000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=850317)
**SQL Server 2016 SP 1 CU5**     |
Microsoft R Open     |Nessuna modifica. Utilizzare precedente|
Microsoft R Server    |Nessuna modifica. Utilizzare precedente |

Se si desidera visualizzare il codice sorgente per Microsoft R, è disponibile per il download come archivio in formato con estensione tar: [programmi di installazione Scarica R Server](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows#download)

### <a name = "bkmk_OtherComponents"></a>Requisiti aggiuntivi

A seconda dell'ambiente, potrebbe essere necessario effettuare copie locali dei programmi di installazione per i prerequisiti seguenti.

Componente  |Versione
---------|---------
[Provider OLE DB Microsoft AS per SQL Server 2016](https://go.microsoft.com/fwlink/?linkid=834405)     |  13.0.1601.5
[Microsoft .NET Core](https://go.microsoft.com/fwlink/?linkid=834319)     | 1.0.1
[Microsoft MPI](https://go.microsoft.com/fwlink/?linkid=834316)     | 7.1.12437.25
[Microsoft Visual C++ 2013 Redistributable](https://go.microsoft.com/fwlink/?linkid=799853)     | 12.0.30501.0
[Microsoft Visual C++ 2015 Redistributable](https://go.microsoft.com/fwlink/?linkid=828641)     | 14.0.23026.0

## <a name="transfer-files"></a>Trasferimento di file

Trasferire il supporto di installazione di SQL Server compresso e i file già scaricati nel computer in cui si sta installando il programma di installazione.

Inserire, ad esempio i file CAB in una cartella utile **Scarica** o la cartella temp dell'utente del programma di installazione: \AppData\Local\Temp C:\Users < nome utente >.

Inserire il file en_sql_server_2017.iso in una cartella appropriata. Fare doppio clic su **setup.exe** per avviare l'installazione.

### <a name="run-setup"></a>Esecuzione del programma di installazione

Quando si esegue l'installazione di SQL Server in un computer disconnesso da internet, il programma di installazione aggiunge un **installazione Offline** pagina alla procedura guidata in modo che è possibile specificare il percorso dei file CAB è stato copiato nel passaggio precedente.

1. Avviare l'installazione guidata di SQL Server.

2. Dopo l'installazione guidata consente di visualizzare la pagina di gestione delle licenze per i componenti di Python o R open source, fare clic su **Accept**. Accettazione delle condizioni di licenza consente di procedere al passaggio successivo.

3. Nel **installazione Offline** nella pagina **percorso di installazione**, specificare la cartella che contiene i file con estensione cab copiato in precedenza.

4. Continuare seguito le istruzioni visualizzate per completare l'installazione.

Al termine dell'installazione, riavviare il servizio e quindi configurare il server per consentire l'esecuzione di script come descritto in [installare SQL Server 2017 Machine Learning Services (In-Database)](sql-machine-learning-services-windows-install.md) o [installazione di SQL Server 2016 R Services (In-Database)](sql-r-services-windows-install.md).

## <a name="slipstream-upgrades-for-offline-servers"></a>Aggiornamenti di integrazione per i server non in linea

L'installazione integrata si riferisce alla possibilità di applicare una patch a un'installazione di istanza non riuscita o di aggiornare tale installazione per risolvere i problemi esistenti. Il vantaggio di questo metodo è che SQL Server viene aggiornato mentre si esegue l'installazione, evitando il riavvio separato in un secondo momento.

+ Se il server non ha accesso a Internet, è necessario scaricare il programma di installazione di SQL Server e quindi scaricare le versioni dei programmi di installazione dei componenti R corrispondenti **prima** di iniziare il processo di aggiornamento.  I componenti di R non sono inclusi per impostazione predefinita con SQL Server.

+ Se si aggiunge questi componenti a un'installazione esistente, utilizzare la versione aggiornata del programma di installazione di SQL Server e la versione aggiornata corrispondente dei componenti aggiuntivi. Quando si specifica che deve essere installato sia la funzionalità di R, il programma di installazione cerca la versione corrispondente dei programmi di installazione per il machine learning componenti.

## <a name="get-help"></a>Supporto

Assistenza sull'installazione o aggiornamento? Per le risposte alle domande più comuni e i problemi noti, vedere l'articolo seguente:

* [Aggiornamento e l'installazione domande frequenti - servizi di Machine Learning](../r/upgrade-and-installation-faq-sql-server-r-services.md)

Per controllare lo stato di installazione dell'istanza e risolvere i problemi comuni, provare a questi report personalizzati.

* [Report personalizzati per SQL Server R Services](../r/monitor-r-services-using-custom-reports-in-management-studio.md)

In questo articolo dal team di supporto dei servizi R viene illustrato come eseguire un'installazione automatica o un aggiornamento di R services in SQL Server 2016: [la distribuzione di R Services in computer senza accesso a Internet](https://blogs.msdn.microsoft.com/sqlcat/2016/10/20/do-it-right-deploying-sql-server-r-services-on-computers-without-internet-access/).


## <a name="next-steps"></a>Passaggi successivi

Gli sviluppatori R possono iniziare a usare alcuni semplici esempi e apprendere le nozioni di base del funzionamento di R con SQL Server. Per il passaggio successivo, vedere i collegamenti seguenti:

+ [Esercitazione: Esecuzione di R in T-SQL](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)
+ [Esercitazione: In-database analitica per gli sviluppatori R](../tutorials/sqldev-in-database-r-for-sql-developers.md)

Gli sviluppatori di Python possono imparare a usare Python con SQL Server seguendo queste esercitazioni:

+ [Esercitazione: Esecuzione di Python in T-SQL](../tutorials/run-python-using-t-sql.md)
+ [Esercitazione: In-database analitica per sviluppatori Python](../tutorials/sqldev-in-database-python-for-sql-developers.md)

Per visualizzare esempi di machine learning basato su scenari reali, vedere [Machine learning esercitazioni](../tutorials/machine-learning-services-tutorials.md).

