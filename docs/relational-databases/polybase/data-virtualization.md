---
title: Virtualizzare i dati esterni in SQL Server 2019 CTP 2.0 | Microsoft Docs
description: ''
author: Abiola
ms.author: aboke
manager: craigg
ms.date: 09/24/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: polybase
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: dfd4460c51e4aeef8e9faff8479e7edf2678c35f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47627319"
---
# <a name="use-the-data-external-table-wizard-with-external-tables"></a>Usare la procedura guidata Tabella esterna per i dati con le tabelle esterne

Uno degli scenari chiave per SQL Server 2019 CTP 2.0 è la possibilità di virtualizzare i dati.  Questo processo consente ai dati di rimanere nella posizione originale, ma è possibile **virtualizzare** i dati in un'istanza di SQL Server in modo da poter eseguire query nella versione virtualizzata come per qualsiasi altra tabella in SQL Server. In questo modo sarà possibile ridurre al minimo la necessità di ricorrere a processi ETL (estrazione, trasformazione e caricamento). Ciò è possibile grazie all'uso di connettori Polybase. Per altre informazioni sulla virtualizzazione dei dati, vedere il documento [Introduzione a PolyBase](polybase-guide.md).

## <a name="launch-the-external-table-wizard"></a>Avviare la procedura guidata Tabella esterna

Connettersi all'istanza master usando l'indirizzo IP/numero di porta (31433) ottenuti alla fine dello script di distribuzione. Espandere il nodo **Database** in Esplora oggetti. Selezionare quindi uno dei database in cui si vogliono virtualizzare i dati da un'istanza di SQL Server esistente. Fare clic con il pulsante destro del mouse sul database e quindi scegliere **Create External Table** (Crea tabella esterna) dal menu di scelta rapida. Verrà avviata la procedura guidata Virtualize Data (Virtualizza dati). È anche possibile avviare la procedura guidata Virtualize Data (Virtualizza dati) dal riquadro comandi digitando CTRL+MAIUSC+P (in Windows) e Comando+Maiuscole+P (in Mac).

![Procedura guidata Virtualize Data (Virtualizza dati)](media/data-virtualization/virtualize-data-wizard.png)
## <a name="select-a-data-source"></a>Selezione un'origine dati

Se la procedura guidata è stata avviata da uno dei database, l'elenco a discesa delle destinazioni viene compilato automaticamente. In questa schermata è comunque possibile immettere o modificare il database di destinazione. I tipi di origini dati esterne supportati dalla procedura guidata sono SQL Server e Oracle.

> [!NOTE]
>SQL Server è evidenziato per impostazione predefinita


![Selezione un'origine dati](media/data-virtualization/select-data-source.png)

Fare clic su Avanti per procedere al passaggio successivo della procedura guidata che consente di impostare la chiave master del database.

## <a name="create-database-master-key"></a>Creare la chiave master del database

In questo passaggio verrà richiesto di creare una chiave master del database. La creazione della chiave master è obbligatoria, perché protegge le credenziali usate da un'origine dati esterna. Scegliere una password complessa per la chiave master. È anche consigliabile eseguire il backup della chiave master usando l'istruzione BACKUP MASTER KEY e archiviarlo in un percorso esterno sicuro.

![Creare una chiave master del database](media/data-virtualization/virtualize-data-master-key.png)

> [!IMPORTANT]
> Se è già disponibile una chiave master del database, i campi di input saranno limitati ed è possibile ignorare questo passaggio. È sufficiente fare clic su "Avanti" per passare alla pagina successiva della procedura guidata.

> [!NOTE]
> Se non si sceglie una password complessa, la procedura guidata visualizzerà l'ultimo passaggio. Si tratta di un problema noto che verrà corretto in una prossima versione, in modo che sia più intuitivo.

## <a name="enter-the-external-data-source-credentials"></a>Immettere le credenziali dell'origine dati esterna

In questo passaggio, immettere i dettagli dell'origine dati esterna e delle credenziali. Questo passaggio crea un oggetto origine dati esterna e quindi usa le credenziali per l'oggetto database per la connessione all'origine dati. Specificare un nome dell'origine dati esterna (ad esempio, Test) e specificare i dettagli per la connessione a SQL Server dell'origine dati esterna, ovvero il nome del server e il nome del database in cui si vuole creare l'origine dati esterna in tale server.

Il passaggio successivo consiste nel configurare le credenziali, quindi specificare un nome per le credenziali, ovvero il nome delle credenziali con ambito database usate per archiviare in modo sicuro le informazioni di accesso per l'origine dati esterna che si sta creando (ad esempio, CredTest) e specificare il nome utente e la password per la connessione all'origine dati.

![Credenziali dell'origine dati esterna](media/data-virtualization/data-source-credentials.png)

## <a name="external-data-table-mapping"></a>Mapping della tabella dei dati esterna

Nella finestra successiva sarà possibile selezionare le tabelle di cui si vuole creare viste esterne. La selezione dei database padre includerà anche tutte le tabelle figlio. Dopo aver selezionato le tabelle, sul lato destro verrà visualizzata una tabella di mapping. In questa tabella è possibile apportare qualsiasi modifica di tipo o modificare il nome della tabella esterna selezionata stessa.

![Credenziali dell'origine dati esterna](media/data-virtualization/data-table-mapping.png)

> [!NOTE]
>Se si fa doppio clic su un'altra tabella selezionata cambierà la visualizzazione del mapping.

> [!IMPORTANT]
>Il tipo foto non è ancora supportato dallo strumento tabella esterna. La creazione di una vista esterna contenente il tipo foto genererà un errore dopo la creazione della tabella. La tabella verrà comunque creata.

## <a name="summary"></a>Riepilogo

Questo passaggio visualizza un riepilogo delle selezioni. Indica il nome delle credenziali con ambito database e gli oggetti origine dati esterna che verranno creati nel database di destinazione. In questo passaggio, è possibile scegliere **"Genera script"** per generare uno script con sintassi T-SQL per creare l'origine dati esterna o **Crea** per creare l'oggetto origine dati esterna.

![Schermata Riepilogo](media/data-virtualization/virtualize-data-summary.png)

Se si fa clic su "Crea" sarà possibile visualizzare l'oggetto origine dati esterna creato nel database di destinazione.

![Origini dati esterne](media/data-virtualization/external-data-sources.png)

Se si fa clic su **Genera script** verrà visualizzata la query T-SQL generata per la creazione dell'oggetto origine dati esterna.

![Genera script](media/data-virtualization/generated-script.png)

> [!NOTE]
> Il pulsante Genera script deve essere visibile solo nell'ultima pagina della procedura guidata. Attualmente viene visualizzato in tutte le pagine.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni sui cluster Big Data di SQL Server e gli scenari correlati, vedere [What is SQL Server Big Data Cluster?](../../big-data-cluster/big-data-cluster-overview.md) (Che cos'è un cluster Big Data di SQL Server?).
