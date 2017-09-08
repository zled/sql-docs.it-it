---
title: L'installazione di Machine Learning Components without Internet Access | Documenti Microsoft
ms.custom: 
ms.date: 04/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a90c438-d78b-47be-ac05-479de64378b2
caps.latest.revision: 30
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7307104b9ad5df2bb8f034525cc82847d21a14bf
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="installing-machine-learning-components-without-internet-access"></a>L'installazione di Machine Learning componenti senza accesso a Internet

Poiché i componenti di R e Python forniti con SQL Server 2016 o SQL Server 2017 sono open source di, Microsoft non vengono installati i componenti di R o Python per impostazione predefinita.

È invece fornire i programmi di installazione correlate e in bundle di pacchetti per motivi di praticità nel Microsoft Download Center e altri siti attendibili. Deve accettare la licenza appropriata e quindi il programma di installazione di SQL Server installerà i componenti di R o Python per l'utente.

In questo argomento fornisce i percorsi di download per i programmi di installazione e una panoramica del processo di installazione offline.

## <a name="installation-process"></a>Processo di installazione

In genere, il programma di installazione dei componenti di computer utilizzati in SQL Server 2016 e SQL Server 2017 richiede una connessione Internet. Quando viene eseguito il programma di installazione di SQL Server, se è stata selezionata una qualsiasi delle opzioni learnig macchina, il programma di installazione controlla il Python o R i programmi di installazione, nonché altri componenti necessari. Se è presente una connessione Internet, SQL Server verrà installarli automaticamente.

> [!IMPORTANT]
> In un server senza accesso a Internet, è necessario scaricare i programmi di installazione aggiuntive prima di continuare.

Come minimo, è necessario scaricare i programmi di installazione R o Python che sono supportati per la versione o numero di build del Server SQL che si sta installando.

A seconda della configurazione del server, potrebbe essere necessario per i componenti aggiuntivi, ad esempio .NET Core.  Vedere [i componenti aggiuntivi](#bkmk_OtherComponents) per informazioni dettagliate.

Dopo avere scaricato i programmi di installazione, utilizzarli quando l'installazione della funzionalità come parte del programma di installazione di SQL Server.

### <a name="step-1-obtain-additional-installers"></a>Passaggio 1. Ottenere i programmi di installazione aggiuntivi

Per **R** in SQL Server 2016 e SQL Server 2017, è necessario ottenere due programmi di installazione diversi. L'Installazione guidata di SQL Server garantisce che i programmi siano installati nell'ordine corretto.

+ Programmi di installazione con **SRO** nel nome di fornire i componenti di origine aperti.
+ Insallers con **SRS** nel nome contengono i componenti forniti da Microsoft, inclusi quelli per l'integrazione di database.


Per **Python** in SQL Server 2017, scaricare il file CAB singolo e tutti i prerequisiti.


1. Scaricare i programmi di installazione dai [siti dell'Area download Microsoft](#installerlocs) in un computer con accesso a Internet e salvare il programma di installazione invece di eseguirlo.
2. Copiare i file di programma di installazione (CAB) nel computer in cui si installerà i componenti di machine learning.
3. Attualmente, l'installazione guidata installa inglese per impostazione predefinita. Per installare utilizzando una lingua diversa, modificare i nomi dei file di programma di installazione come descritto qui: [modifiche necessarie per diverse lingue](#modslocales).
4. Scaricare tutti i componenti aggiuntivi necessari, ad esempio MPI o .NET Core.
5. Facoltativamente, è possibile scaricare il codice sorgente archiviato per i componenti di origine aperti, ma questo non è necessario per l'installazione di SQL Server e può essere completato in qualsiasi momento. Per ulteriori informazioni, vedere [R Server per Windows](https://msdn.microsoft.com/microsoft-r/rserver-install-windows).


> [!NOTE]
> Assicurarsi di ottenere i file corrispondenti alla versione di SQL Server che verrà installata.
> 
> Supporto per Python viene fornito in SQL Server 2017 CTP 2.0. Le versioni precedenti, tra cui SQL Server 2016 non supportano Python.

Per una descrizione dettagliata del processo di installazione offline per R Services in SQL Server 2016, è consigliabile l'articolo di [Team di consulenza clienti di SQL Server](https://blogs.msdn.microsoft.com/sqlcat/2016/10/20/do-it-right-deploying-sql-server-r-services-on-computers-without-internet-access/). Vengono inoltre descritti gli scenari di applicazione di patch e installazione integrata.


### <a name="step-2-run-offline-setup-using-the-sql-server-setup-wizard"></a>Passaggio 2. Eseguire il programma di installazione offline utilizzando l'installazione guidata di SQL Server

1. Eseguire l'Installazione guidata di SQL Server.
2. Quando l'installazione guidata consente di visualizzare la pagina di gestione delle licenze, fare clic su **Accept**.
3. Verrà visualizzata una finestra di dialogo in cui è richiesto il **percorso di installazione** dei pacchetti necessari.
4. Fare clic su **Sfoglia** per individuare la cartella che contiene i file di programma di installazione copiato in precedenza.
5. Se vengono trovati i file corretti, fare clic su **Avanti** per indicare che i componenti sono disponibili.
10. Completare l'Installazione guidata di SQL Server.
11. Eseguire i passaggi di post-installazione necessari per assicurarsi che il servizio è abilitato.

## <a name="installerlocs"></a>Scarica

Versione  |Collegamento di download  
---------|---------
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
Microsoft R Open     |[SRO_3.2.2.13000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=831785)
Microsoft R Server     |[SRS_8.0.3.13000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=831676)  |
**SQL Server 2016 SP 1**     |
Microsoft R Open     |[SRO_3.2.2.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824879)
Microsoft R Server     |[SRS_8.0.3.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824881)
**SQL Server 2016 SP 1 GDR**     |
Microsoft R Open     |[SRO_3.2.2.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836819)
Microsoft R Server     |[SRS_8.0.3.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836818)
**SQL Server 2017 CTP 1**     |
Microsoft R Open     |[SRO_3.3.0.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836819)
Microsoft R Server     |[SRS_9.0.0.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836818)
**SQL Server 2017 CTP 1.1** |
Microsoft R Open     |[SRO_3.3.2.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=834568)
Microsoft R Server     |[SRS_9.0.1.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=834567)
**SQL Server 2017 CTP 1.4** |
Microsoft R Open     |[SRO_xxxx_1033.cab](https://go.microsoft.com/fwlink/?LinkId=842483)
Microsoft R Server     |[SRS_xxx.xxx_1033.cab](https://go.microsoft.com/fwlink/?LinkId=842482)
**SQL Server 2017 CTP 2.0** |
Microsoft R Open     |[SRO_3.3.3.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=842800)
Microsoft R Server     |[SRS_9.1.0.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=842799)
Aprire Microsoft Python     |[SPO_9.1.0.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=842828)
Server Microsoft Python    |[SPS_9.1.0.0__1033.cab](https://go.microsoft.com/fwlink/?LinkId=842848)

Se si desidera visualizzare il codice sorgente per Microsoft R, è disponibile per il download come archivio in formato con estensione tar: [programmi di installazione Scarica R Server](https://msdn.microsoft.com/microsoft-r/rserver-install-windows#download)

### <a name = "bkmk_OtherComponents"></a>Requisiti aggiuntivi

A seconda dell'ambiente, potrebbe essere necessario effettuare copie locali dei programmi di installazione per i prerequisiti seguenti.

Componente  |Versione
---------|---------
[Provider OLE DB Microsoft AS per SQL Server 2016](https://go.microsoft.com/fwlink/?linkid=834405)     |  13.0.1601.5
[Microsoft .NET Core](https://go.microsoft.com/fwlink/?linkid=834319)     | 1.0.1
[Microsoft MPI](https://go.microsoft.com/fwlink/?linkid=834316)     | 7.1.12437.25
[Microsoft Visual C++ 2013 Redistributable](https://go.microsoft.com/fwlink/?linkid=799853)     | 12.0.30501.0
[Microsoft Visual C++ 2015 Redistributable](https://go.microsoft.com/fwlink/?linkid=828641)     | 14.0.23026.0


## <a name="modslocales"></a>L'installazione di lingue diverse

Se si scaricano i file con estensione cab durante l'installazione di SQL Server in un computer con accesso a Internet, l'Installazione guidata rileva la lingua locale e imposta automaticamente la lingua del programma di installazione.

Tuttavia, se si installa una delle versioni localizzate di SQL Server in un computer senza accesso a Internet e si scaricano i programmi di installazione di R in una condivisione locale, è necessario modificare manualmente il nome dei file scaricati e inserire l'identificatore di lingua corretto per la lingua di installazione.

Se ad esempio si installa la versione giapponese di SQL Server, modificare il nome file da SRS_8.0.3.0_**1033**.cab a SRS_8.0.3.0_**1041**.cab.


## <a name="slipstream-upgrades"></a>Aggiornamenti di integrazione

L'installazione integrata si riferisce alla possibilità di applicare una patch a un'installazione di istanza non riuscita o di aggiornare tale installazione per risolvere i problemi esistenti. Il vantaggio di questo metodo è che SQL Server viene aggiornato mentre si esegue l'installazione, evitando il riavvio separato in un secondo momento.

+ Se il server non ha accesso a Internet, è necessario scaricare il programma di installazione di SQL Server e quindi scaricare le versioni dei programmi di installazione dei componenti R corrispondenti **prima** di iniziare il processo di aggiornamento.  I componenti di R non sono inclusi per impostazione predefinita con SQL Server.

+ Se si è *aggiunta* questi componenti di un *esistente* installazione, utilizzare la versione aggiornata del programma di installazione di SQL Server e il corrispondente aggiornato versione dei componenti aggiuntivi. Quando si specifica che deve essere installato sia la funzionalità di R, il programma di installazione cerca la versione corrispondente dei programmi di installazione per il machine learning componenti.

## <a name="command-line-arguments-for-setup"></a>Argomenti della riga di comando per l'installazione

Quando si esegue un'installazione automatica, sarà necessario fornire gli argomenti della riga di comando seguenti. Si noti che non è necessario impostare ulteriori eventuali flag aggiuntivi per installare i componenti necessari. Prerequisiti, ad esempio .NET core vengono automaticamente installati per impostazione predefinita.

**Percorso dei programmi di installazione**

- `/UPDATESOURCE`Per specificare il percorso del file locale contenente il programma di installazione di aggiornamento di SQL Server
- `/MRCACHEDIRECTORY`Per specificare la cartella contenente i file CAB del componente R

**Componenti di R in SQL Server 2016**

- `/ADVANCEDANALYTICS`Per ottenere supporto del motore di script esterni
- `/IACCEPTROPENLICENSETERMS="True"`per accettare R separate contratto di licenza

**Componenti di R in SQL Server SQL Server 2017**

- `/ADVANCEDANALYTICS`Per ottenere supporto del motore di script esterni
- `/SQL_INST_MR`usare il linguaggio R
- `/IACCEPTROPENLICENSETERMS="True"`per accettare R separate contratto di licenza

**Componenti di Python 2017 di SQL Server**

- `/ADVANCEDANALYTICS`Per ottenere supporto del motore di script esterni
- `/SQL_INST_MPY`Per utilizzare Python
- `/IACCEPTPYTHONLICENSETERMS="True"`per accettare R separate contratto di licenza

> [!TIP]
> In questo articolo dal team di supporto dei servizi R viene illustrato come eseguire un'installazione automatica o un aggiornamento di R services in SQL Server 2016: [la distribuzione di R Services in computer senza accesso a Internet](https://blogs.msdn.microsoft.com/sqlcat/2016/10/20/do-it-right-deploying-sql-server-r-services-on-computers-without-internet-access/).

## <a name="see-also"></a>Vedere anche

[Installare Microsoft R Server](https://msdn.microsoft.com/microsoft-r/rserver-install-windows)


