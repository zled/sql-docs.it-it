---
title: Estensione di 2019 Server SQL Studio di dati di Azure (anteprima) | Microsoft Docs
description: Estensione di anteprima di SQL Server 2019 per Data Studio di Azure
ms.custom: tools|sos
ms.date: 09/24/2018
ms.reviewer: alayu; sstein
ms.prod: sql
ms.prod_service: sql-tools
ms.topic: conceptual
author: yualan
ms.author: alayu
manager: craigg
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 8f9d10fbdec028549f9b23b23506882d5c5afe5d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48131231"
---
# <a name="sql-server-2019-extension-preview"></a>Estensione di SQL Server 2019 (anteprima)

L'estensione di SQL Server 2019 (anteprima) offre supporto in anteprima per nuove funzionalità e strumenti di spedizione supportare [!INCLUDE [sql-server-2019](..\includes\sssqlv15-md.md)]. Ciò include il supporto di anteprima per [i cluster di SQL Server 2019 dei big data](../big-data-cluster/big-data-cluster-overview.md), un integrata [esperienza notebook](../big-data-cluster/notebooks-guidance.md), un PolyBase [guidata Create External Table](../relational-databases/polybase/data-virtualization.md?toc=%2fsql%2fbig-data-cluster%2ftoc.json)e [Esplora risorse di azure](azure-resource-explorer.md).

## <a name="install-the-sql-server-2019-extension-preview"></a>Installare l'estensione di SQL Server 2019 (anteprima)

Scaricare e installare l'estensione di SQL Server 2019 (anteprima):

  |Piattaforma|Scarica|Data di rilascio|
  |:---|:---|:---|
  |Windows|[VSIX](https://go.microsoft.com/fwlink/?linkid=2024911)|24 settembre 2018|
  |macOS|[VSIX](https://go.microsoft.com/fwlink/?linkid=2024587)|24 settembre 2018 |
  |Linux|[VSIX](https://go.microsoft.com/fwlink/?linkid=2024841)|24 settembre 2018 |


In Azure Data Studio scegliere **installare l'estensione dal pacchetto VSIX** dalle **File** menu e selezionare il file VSIX scaricato. Scegli **Sì** quando viene richiesto di confermare l'installazione e attendere la notifica che l'installazione è riuscita.

Selezionare **Ricarica** per abilitare l'estensione (richiesto solo la prima volta in cui l'estensione viene installata).


##  <a name="sql-server-2019-big-data-cluster-support"></a>Supporto di SQL Server 2019 Big Data Cluster

* Fare clic su **Aggiungi connessione** nelle *Esplora oggetti* e scegliere **cluster di big data di SQL Server** come tipo di connessione.
* Immettere il nome host o indirizzo IP dell'endpoint del cluster più il nome utente e password utilizzata per la connessione.
* Facoltativamente, includere un nome descrittivo visualizzato nei **nome** campo.
* Fare clic su **Connect** e quindi è possibile avviare attività comuni nel dashboard, esplorare **HDFS** in Esplora oggetti ed esecuzione di attività nel contesto da tale posizione.
* Per inviare un processo Spark nel cluster, fare doppio clic sul nodo del server nella *Esplora oggetti* e scegliere **Submit Spark Job** per visualizzare la finestra di dialogo di invio.
* Per aprire un Notebook, vedere la sezione successiva.

Per informazioni dettagliate, vedere [i cluster di Big Data](../big-data-cluster/big-data-cluster-overview.md).


## <a name="azure-data-studio-notebooks"></a>Notebook di Studio dei dati di Azure

* Aprire un notebook in uno dei modi seguenti:
  * Aprire un nuovo notebook dal *comandi*.
  * Aprire l'albero di Esplora oggetti di HDFS per un cluster di big data 2019 di SQL Server e uno:
    * Fare clic con il pulsante destro sul nodo del server e scegliere **nuovo Jupyter Notebook**.
    * Fare clic con il pulsante destro su un file CSV e scegliere **analizza in Notebook**.
  * Aprire un file con estensione ipynb esistente dal **File** dal menu o Esplora file *(file con estensione ipynb devono essere aggiornati alla versione 4 o versione successiva per caricare correttamente)*
* Scegliere un kernel. Per l'esecuzione di notebook locale, scegliere Python 3. Per l'esecuzione remota, scegliere PySpark o Spark | Scala.
* Scegliere un endpoint del cluster SQL Server i big data a cui connettersi se l'esecuzione in modalità remota (non necessario per lo sviluppo locale con Python 3).
* Aggiunta di celle di codice o markdown tramite i pulsanti nell'intestazione del notebook. Rimuovere le celle con l'icona del Cestino a sinistra di ciascuna cella.
* Eseguire le celle con il pulsante play per le celle di codice e attivare la modifica di markdown e visualizzare in anteprima con l'icona sotto controllo


## <a name="azure-resource-explorer"></a>Esplora risorse di Azure

* Per accedere ad Azure, fare clic sull'icona di persona in basso a sinistra di Studio dei dati di Azure e seguire le finestre di dialogo per l'accesso ad Azure.
* Una volta effettuato l'accesso, fare clic sull'icona di Azure triangolare in a sinistra sulla barra di Azure Data Studio ed espandere l'albero per visualizzare le risorse SQL associate alle sottoscrizioni.
* Pulsante destro del mouse oppure fare clic sull'icona della spina su qualsiasi database SQL o SQL Server per aprire la finestra di dialogo di connessione. Immettere la password per la connessione e aggiungere la risorsa a Esplora oggetti di Studio dei dati di Azure.

Per informazioni dettagliate, vedere [Azure Resource Explorer](azure-resource-explorer.md).


## <a name="polybase-create-external-table-wizard"></a>Polybase Creazione guidata tabella esterna

* Da un'istanza di SQL Server 2019 il *Creazione guidata tabella esterna* possono essere aperti in tre modi:
  * Fare clic con il pulsante destro su un server, scegliere **Manage**, fare clic sulla scheda per SQL Server 2019 (anteprima) e scegliere **Create External Table**.
  * Con un'istanza di SQL Server 2019 selezionata in *Esplora oggetti*, visualizziamo *Creazione guidata esterno* tramite il *comandi*.
  * Fare clic con il pulsante destro su un database di SQL Server 2019 *Esplora oggetti* e scegliere **Create External Table**.
* In questa versione dell'estensione, è possibile creare tabelle esterne per accedere a tabelle remote di SQL Server e Oracle.

  > [!NOTE]
  > Mentre la funzionalità tabella esterna è una funzionalità 2019 SQL, il Server SQL remoto potrebbe essere in esecuzione una versione precedente di SQL Server.

* Scegliere se accede a SQL Server o Oracle nella prima pagina della procedura guidata e continuare.
* Verrà richiesto di creare una chiave Master del Database se non ne è stato creato (verranno bloccate le password di complessità insufficiente).
* Creare una connessione all'origine dati e denominato di credenziali per il server remoto.
* Scegliere quali oggetti per eseguire il mapping alla nuova tabella esterna.
* Scegli **genera Script** oppure **crea** per completare la procedura guidata.
* Dopo la creazione della tabella esterna, viene immediatamente visualizzato nell'albero degli oggetti del database in cui è stato creato.


## <a name="known-issues"></a>Problemi noti

* Se la password non viene salvata quando si crea una connessione, alcune azioni, ad esempio l'invio del processo Spark potrebbero non riuscire.
* I notebook con estensione ipynb esistente devono essere aggiornati alla versione 4 o versione successiva per caricare contenuto nel Visualizzatore.
