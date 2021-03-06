---
title: Download di file CAB per gli aggiornamenti cumulativi di SQL Server | Documenti di Microsoft
description: Download di file CAB per SQL Server 2017 Machine Learning Services e SQL Server 2016 R Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/01/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 25568dc5a76283b18affd10ef0419f83515f6403
ms.sourcegitcommit: 615f8b5063aed679495d92a04ffbe00451d34a11
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48232605"
---
# <a name="cab-downloads-for-cumulative-updates-of-sql-server-in-database-analytics-instances"></a>File CAB di download per gli aggiornamenti cumulativi di analitica nel database di SQL Server le istanze

Istanze di SQL Server configurate per l'analitica nel database includono funzionalità di R e Python. Queste funzionalità fornito con i file CAB, installato e gestite tramite il programma di installazione di SQL Server. Sui dispositivi connessi a internet, gli aggiornamenti di file CAB sono in genere applicati tramite Windows Update. Nel disconnesso server, è necessario scaricare e applicare manualmente i file CAB. 

Questo articolo fornisce i collegamenti ai download per i file CAB per ogni aggiornamento cumulativo. Vengono forniti collegamenti per sia SQL Server 2017 Machine Learning Services (R e Python), nonché SQL Server 2016 R Services. Per altre informazioni sulle installazioni non in linea, vedere [apprendimento installazione di SQL Server i componenti senza accesso a internet](sql-ml-component-install-without-internet-access.md#apply-cu).

## <a name="prerequisites"></a>Prerequisiti

Iniziare con un'installazione di base.

+ In SQL Server 2017 Machine Learning Services, la versione iniziale è l'installazione iniziale. 
+ In SQL Server 2016 R Services, è possibile iniziare con la versione iniziale, SP1 o SP2. 

È anche possibile applicare gli aggiornamenti cumulativi per un server autonomo.

## <a name="sql-server-2017-cabs"></a>SQL Server 2017 CABs

File CAB sono elencati in ordine cronologico inverso. Quando si scaricano i file CAB e li trasferiscono al computer di destinazione, inserirli in un'unica cartella, ad esempio **Scarica** o cartella % temp % dell'utente il programma di installazione.

Versione  |Collegamento di download  | Problemi risolti | 
---------|---------------|-------|
**[SQL Server 2017 CU10](https://support.microsoft.com/help/4342123)-[CU11](https://support.microsoft.com/help/4462262)** |  |  |
Microsoft R Open     | [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)| Nessuna modifica rispetto alle versioni precedenti. |
R Server      |[SRS_9.2.0.1000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2006287&clcid=1033)| Correzioni minori.|
Python di Microsoft Open     | [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| Nessuna modifica rispetto alle versioni precedenti. |
Server di Python    |[SPS_9.2.0.1000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=2006805&clcid=1033)| Python rx_data_step perde lo stato dell'ordine di riga quando vengono eliminati i duplicati. <br/>SPEE avrà esito negativo di tipo di dati rilevamento sull'indice columnstore cluster. <br/>Restituisce una tabella vuota quando le colonne contengono tutti i valori null. |
**[SQL Server 2017 CU8](https://support.microsoft.com/help/4338363)-[CU9](https://support.microsoft.com/help/4341265)** |  |  |
Microsoft R Open     | [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)| Nessuna modifica rispetto alle versioni precedenti. |
R Server      |[SRS_9.2.0.800_1033.cab](https://go.microsoft.com/fwlink/?LinkId=874708&clcid=1033)|
Python di Microsoft Open     | [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| Nessuna modifica rispetto alle versioni precedenti. |
Server di Python    |[SPS_9.2.0.800_1033.cab](https://go.microsoft.com/fwlink/?LinkId=874707&clcid=1033)|
**[SQL Server 2017 CU6](https://support.microsoft.com/help/4101464)-[CU7](https://support.microsoft.com/help/4229789)** |  |  |
Microsoft R Open     | [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)| Nessuna modifica rispetto alle versioni precedenti. |
R Server      |[SRS_9.2.0.600_1033.cab](https://go.microsoft.com/fwlink/?LinkId=871074&clcid=1033)|
Python di Microsoft Open     | [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| Nessuna modifica rispetto alle versioni precedenti. |
Server di Python    |[SPS_9.2.0.600_1033.cab](https://go.microsoft.com/fwlink/?LinkId=871073&clcid=1033)| Tipi di dati DateTime nelle query SPEES.<br/>messaggi di errore in microsoftml migliorati quando non sono presenti modelli con training preliminare.<br/> Correzioni per revoscalepy trasformano le funzioni e variabili.|
**[SQL Server 2017 CU5](https://support.microsoft.com/help/4092643)** |  |  |
Microsoft R Open     | [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)| Nessuna modifica rispetto alle versioni precedenti. |
R Server      |[SRS_9.2.0.500_1033.cab](https://go.microsoft.com/fwlink/?LinkId=869052&clcid=1033)| Errori di tempo relativo al percorso rxInstallPackages.<br/>Connessioni in un loopback per RxExec.
Python di Microsoft Open    | Nessuna modifica rispetto alle versioni precedenti. |
Server di Python    |[SPS_9.2.0.500_1033.cab](https://go.microsoft.com/fwlink/?LinkId=869053&clcid=1033)| <br/>Connessioni in un loopback per rx_exec.
**[SQL Server 2017 CU4](https://support.microsoft.com/help/4056498)** |  |   |
Microsoft R Open     | [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)| Nessuna modifica rispetto alle versioni precedenti. |
R Server      |[SRS_9.2.0.400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866212&clcid=1033)|
Python di Microsoft Open     |[SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| Nessuna modifica rispetto alle versioni precedenti. |
 Server di Python    |[SPS_9.2.0.400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866213&clcid=1033)|
**[SQL Server 2017 CU3](https://support.microsoft.com/help/4052987)** |  |  |
Microsoft R Open     |[SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)|
R Server      |[SRS_9.2.0.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863893)|
Python di Microsoft Open     |[SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| Nessuna modifica rispetto alle versioni precedenti. |
Server di Python    |[SPS_9.2.0.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863892)| Serializzazione in revoscalepy, del modello Python usando il [rx_serialize_model funzione](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-serialize-model).<br/>[Assegnazione dei punteggi nativa](../sql-native-scoring.md) supporto, oltre a miglioramenti [assegnazione dei punteggi in tempo reale](../real-time-scoring.md). 
**SQL Server 2017 [CU1](https://support.microsoft.com/help/4038634)-[CU2](https://support.microsoft.com/help/4052574)** |  |  |
Microsoft R Open     | [SRO_3.3.3.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851496)| Nessuna modifica rispetto alle versioni precedenti. |
R Server      |[SRS_9.2.0.100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851501)|
Python di Microsoft Open     | [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)| Nessuna modifica rispetto alle versioni precedenti. | 
Server di Python    |[SPS_9.2.0.100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851500) | Aggiunge rx_create_col_info per la restituzione di informazioni sullo schema. <br/>Miglioramenti [rx_exec](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/rx-exec) per supportare gli scenari paralleli utilizzando il `RxLocalParallel` contesto di calcolo.|
**Versione iniziale** |  |  |
Microsoft R Open     |[SRO_3.3.3.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851496)|
R Server      |[SRS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851507)|
Python di Microsoft Open     |[SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502) |
Server di Python    |[SPS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851508) |


<a name="bkmk_2016Installers"></a>

## <a name="sql-server-2016-cabs"></a>SQL Server 2016 CABs

Per SQL Server 2016 R Services, le versioni baseline sono la versione RTM o una versione del service pack.

Versione  |Collegamento di download  |
---------|---------------|
**SQL Server 2016 SP2 da CU1 a CU2**     |
Microsoft R Open     |[SRO_3.2.2.20000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866039)|
Microsoft R Server    |[SRS_8.0.3.20000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866038)|
**SQL Server 2016 SP1 CU4-CU10**     |
Microsoft R Open     |[SRO_3.2.2.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836819)|
Microsoft R Server    |[SRS_8.0.3.17000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=850317)
**SQL Server 2016 SP1 da CU1 a CU3**     |
Microsoft R Open     |[SRO_3.2.2.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836819)|
Microsoft R Server    |[SRS_8.0.3.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836818)|
**SQL Server 2016 SP1**     |
Microsoft R Open     |[SRO_3.2.2.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824879)
Microsoft R Server     |[SRS_8.0.3.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824881)
**SQL Server 2016 CU4-CU9**     |
Microsoft R Open     |[SRO_3.2.2.13000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=831785)|
Microsoft R Server     |[SRS_8.0.3.13000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=831676)|
**SQL Server 2016 CU2-CU3**     |
Microsoft R Open     |[SRO_3.2.2.12000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=827398)
Microsoft R Server     |[SRS_8.0.3.12000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=827399)
**SQL Server 2016 da CU1**     |
Microsoft R Open     |[SRO_3.2.2.10000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=808803)
Microsoft R Server     |[SRS_8.0.3.10000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=808805)
**SQL Server 2016 RTM**     |
Microsoft R Open     |[SRO_3.2.2.803_1033.cab](https://go.microsoft.com/fwlink/?LinkId=761266)
Microsoft R Server     |[SRS_8.0.3.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=735051)

> [!NOTE]
> 
> Durante l'installazione offline di SQL Server 2016 SP1 CU4 o CU5 SP1, scaricare SRO_3.2.2.16000_1033.cab. Se hai scaricato SRO_3.2.2.13000_1033.cab da FWLINK 831785 come indicato nella finestra di dialogo programma di installazione, rinominare il file come SRO_3.2.2.16000_1033.cab prima di installare l'aggiornamento cumulativo.

Se si desidera visualizzare il codice sorgente per Microsoft R, è disponibile per il download come un archivio nel formato con estensione tar: [programmi di installazione Scarica R Server](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows#download)

## <a name="see-also"></a>Vedere anche

[Applicare aggiornamenti cumulativi in computer senza accesso a internet](sql-ml-component-install-without-internet-access.md#apply-cu)

[Applicare aggiornamenti cumulativi in computer che dispongono di connettività internet](sql-ml-component-install-without-internet-access.md#apply-cu)

[Applicare aggiornamenti cumulativi per un server autonomo](sql-machine-learning-standalone-windows-install.md#apply-cu)
