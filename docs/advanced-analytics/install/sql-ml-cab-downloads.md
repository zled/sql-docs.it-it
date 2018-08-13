---
title: Download di file CAB per gli aggiornamenti cumulativi di SQL Server | Documenti di Microsoft
description: Download di file CAB per SQL Server 2017 Machine Learning Services e SQL Server 2016 R Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/02/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 6a2893e976e64315a1aad742062e962269439b72
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/06/2018
ms.locfileid: "39566318"
---
# <a name="cab-downloads-for-cumulative-updates-of-sql-server-in-database-analytics-instances"></a>File CAB di download per gli aggiornamenti cumulativi di analitica nel database di SQL Server le istanze

Le istanze di SQL Server configurate per analitica nel database includono funzionalità di R e Python disponibili nel file CAB, installato e serviti tramite installazione di SQL Server. 

Nei server connessi a internet, gli aggiornamenti di file CAB sono in genere applicati tramite Windows Update. Server disconnesso deve essere aggiornato manualmente. Questo articolo fornisce i collegamenti ai download per i file CAB per ogni aggiornamento cumulativo di SQL Server 2017 Machine Learning Services (R e Python) o SQL Server 2016 R Services in modo che è possibile aggiornare manualmente i server disconnessi da internet. 

## <a name="prerequisites"></a>Prerequisiti

Iniziare con un'installazione di base.

+ In SQL Server 2017 Machine Learning Services, la versione iniziale è l'installazione iniziale. 

+ In SQL Server 2016 R Services, è possibile iniziare con la versione iniziale, SP1 o SP2. 

Per altre informazioni, vedere [apprendimento installazione di SQL Server i componenti senza accesso a internet](sql-ml-component-install-without-internet-access.md).

Dopo aver creato un'installazione di base, è possibile eseguire una [slipstream aggiornamento](sql-ml-component-install-without-internet-access.md#slipstream-upgrades) che include i file CAB con funzionalità di aggiornamento di machine learning.

File CAB sono elencati in ordine cronologico inverso. Quando si scaricano i file CAB e li trasferiscono al computer di destinazione, inserirli in un'unica cartella, ad esempio **Scarica** o cartella % temp % dell'utente il programma di installazione.

## <a name="sql-server-2017-cabs"></a>SQL Server 2017 CABs

Versione  |Collegamento di download  |
---------|---------|
**SQL Server 2017 CU8-CU9** |
Microsoft R Open     |Nessuna modifica; uso precedente [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)|
Microsoft R Server      |[SRS_9.2.0.800_1033.cab](https://go.microsoft.com/fwlink/?LinkId=874708&clcid=1033)|
Python di Microsoft Open     |Nessuna modifica; uso precedente [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)|
Server Microsoft Python    |[SPS_9.2.0.800_1033.cab](https://go.microsoft.com/fwlink/?LinkId=874707&clcid=1033)]|
**SQL Server 2017 CU6-CU7** |
Microsoft R Open     |Nessuna modifica; uso precedente [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)|
Microsoft R Server      |[SRS_9.2.0.600_1033.cab](https://go.microsoft.com/fwlink/?LinkId=871074&clcid=1033)|
Python di Microsoft Open     |Nessuna modifica; uso precedente [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)|
Server Microsoft Python    |[SPS_9.2.0.600_1033.cab](https://go.microsoft.com/fwlink/?LinkId=871073&clcid=1033)|
**SQL Server 2017 CU5** |
Microsoft R Open     |Nessuna modifica; uso precedente [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)|
Microsoft R Server      |[SRS_9.2.0.500_1033.cab](https://go.microsoft.com/fwlink/?LinkId=869052&clcid=1033)|
Python di Microsoft Open     |Nessuna modifica; uso precedente [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)|
Server Microsoft Python    |[SPS_9.2.0.500_1033.cab](https://go.microsoft.com/fwlink/?LinkId=869053&clcid=1033)|
**SQL Server 2017 CU4** |
Microsoft R Open     |Nessuna modifica; uso precedente [SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)|
Microsoft R Server      |[SRS_9.2.0.400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866212&clcid=1033)|
Python di Microsoft Open     |Nessuna modifica; uso precedente [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)|
Server Microsoft Python    |[SPS_9.2.0.400_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866213&clcid=1033)|
**SQL Server 2017 CU3** |
Microsoft R Open     |[SRO_3.3.3.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863894)|
Microsoft R Server      |[SRS_9.2.0.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863893)|
Python di Microsoft Open     |Nessuna modifica; uso precedente [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)|
Server Microsoft Python    |[SPS_9.2.0.300_1033.cab](https://go.microsoft.com/fwlink/?LinkId=863892)|
**SQL Server 2017 da CU1 a CU2** |
Microsoft R Open     |Nessuna modifica; uso precedente [SRO_3.3.3.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851496)|
Microsoft R Server      |[SRS_9.2.0.100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851501)|
Python di Microsoft Open     |Nessuna modifica; uso precedente [SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502)|
Server Microsoft Python    |[SPS_9.2.0.100_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851500) |
**Versione iniziale di SQL Server 2017** |
Microsoft R Open     |[SRO_3.3.3.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851496)|
Microsoft R Server      |[SRS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851507)|
Python di Microsoft Open     |[SPO_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851502) |
Server Microsoft Python    |[SPS_9.2.0.24_1033.cab](https://go.microsoft.com/fwlink/?LinkId=851508) |


<a name="bkmk_2016Installers"></a>

## <a name="sql-server-2016-cabs"></a>SQL Server 2016 CABs

Per SQL Server 2016 R Services, le versioni baseline sono la versione RTM o una versione del service pack.

Versione  |Collegamento di download  |
---------|---------------|
**SQL Server 2016 SP2 da CU1 a CU2**     |
Microsoft R Open     |[SRO_3.2.2.20000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866039)|
Microsoft R Server    |[SRS_8.0.3.20000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=866038)|
**SQL Server 2016 SP1 CU4-CU10**     |
Microsoft R Open     |Nessuna modifica; uso precedente [SRO_3.2.2.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836819)|
Microsoft R Server    |[SRS_8.0.3.17000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=850317)
**SQL Server 2016 SP1 da CU1 a CU3**     |
Microsoft R Open     |[SRO_3.2.2.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836819)|
Microsoft R Server    |[SRS_8.0.3.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836818)|
**SQL Server 2016 SP1**     |
Microsoft R Open     |[SRO_3.2.2.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824879)
Microsoft R Server     |[SRS_8.0.3.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824881)=
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

# <a name="see-also"></a>Vedere anche

[Installare SQL Server machine learning componenti senza accesso a internet](sql-ml-component-install-without-internet-access.md)
