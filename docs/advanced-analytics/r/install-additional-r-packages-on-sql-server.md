---
title: Installare i nuovi pacchetti di R in servizi di SQL Server Machine Learning | Documenti Microsoft
description: Aggiungere i nuovi pacchetti R per SQL Server 2016 R Services o SQL Server 2017 Machine Learning Services (In-Database)
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/29/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: e05842a8e8a5a1d2454dbbe500b4d5aa95fca660
ms.sourcegitcommit: 2d93cd115f52bf3eff3069f28ea866232b4f9f9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/01/2018
ms.locfileid: "34707079"
---
# <a name="install-new-r-packages-on-sql-server"></a>Installare i nuovi pacchetti di R in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In questo articolo viene descritto come installare i nuovi pacchetti di R a un'istanza di SQL Server in cui è abilitato l'apprendimento. Sono disponibili diversi metodi per l'installazione di nuovi pacchetti di R, a seconda di quale versione di SQL Server in uso e se il server dispone di una connessione a internet. Sono possibili approcci seguenti per la nuova installazione del pacchetto.

| Approccio                           | Autorizzazioni               | Remoto o locale |
|------------------------------------|---------------------------|--------------|
| [Utilizzare gestori di pacchetti R convenzionali](use-r-package-managers-on-sql-server.md)  | Amministrativi | Local |
| [Usare RevoScaleR](use-revoscaler-to-manage-r-packages.md) |  Amministrazione abilitati, i ruoli del database in un secondo momento | both|
| [Utilizzare T-SQL (Crea raccolta esterni)](install-r-packages-tsql.md) | Amministrazione abilitati, i ruoli del database in un secondo momento | both 

## <a name="who-installs-permissions"></a>Che consente di installare (autorizzazioni)

La libreria di pacchetti R fisicamente si trova nella cartella file di programma dell'istanza di SQL Server, in una cartella sicura con accesso limitato. La scrittura in questa posizione richiede le autorizzazioni di amministratore.

Gli amministratori non possono installare i pacchetti, ma questa operazione richiede funzionalità non disponibili nelle installazioni iniziale e configurazione supplementari. Esistono due approcci per le installazioni del pacchetto non-admin: RevoScaleR uso versione 9.0.1 e versioni successive, o a utilizzare creare libreria esterna (solo SQL Server 2017). In SQL Server 2017, **dbo_owner** o un altro utente con autorizzazione di creazione libreria esterna è possibile installare pacchetti R nel database corrente.

Gli sviluppatori R sono abituati alla creazione di librerie utente per i pacchetti di che cui hanno bisogno se centralizzate librerie sono off-limits. Questa pratica è problematica per il codice R in esecuzione in un'istanza di motore di database di SQL Server. SQL Server non è possibile caricare i pacchetti da librerie esterne, anche se tale libreria nello stesso computer. Solo i pacchetti dalla libreria di istanza possono essere utilizzati nel codice R in esecuzione in SQL Server.

Accesso al file system è in genere limitata nel server, o anche se si dispone di diritti di amministratore e l'accesso in una cartella di documento utente nel server, il runtime dello script esterno che viene eseguita in SQL Server non può accedere tutti i pacchetti installati all'esterno dell'istanza predefinita libreria. 

## <a name="considerations-for-package-installation"></a>Considerazioni per l'installazione del pacchetto

Prima di installare i nuovi pacchetti, prendere in considerazione se le funzionalità abilitate per un determinato pacchetto sono adatti in un ambiente di SQL Server. In un ambiente di SQL Server protetti, è opportuno evitare quanto segue:

+ Pacchetti che richiedono l'accesso alla rete
+ Pacchetti che richiedono Java o altri Framework non è in genere utilizzato in un ambiente di SQL Server
+ Pacchetti che richiedono l'accesso con privilegi elevati di file system
+ Pacchetto venga utilizzato per lo sviluppo web o altre attività che non traggono vantaggio dall'esecuzione all'interno di SQL Server

## <a name="offline-installation-no-internet-access"></a>Installazione offline (Nessun accesso a internet)

In generale, i server che ospitano i database di produzione bloccano le connessioni internet. Installazione di nuovi pacchetti R o Python in tali ambienti è necessario preparare in anticipo i pacchetti e le dipendenze e copiare i file in una cartella sul server per l'installazione offline.

Identificare tutte le dipendenze diventa complicata. Per R, è consigliabile utilizzare [miniCRAN per creare un repository locale](create-a-local-package-repository-using-minicran.md) e quindi trasferire il repository completamente definito in un'istanza di SQL Server isolata.

In alternativa, è possibile eseguire questa procedura manualmente:

1. Identificare tutte le dipendenze di pacchetto. 
2. Verificare se tutti i pacchetti necessari sono già installati nel server. Se il pacchetto è installato, verificare che la versione sia corretta.
3. Scaricare il pacchetto e tutte le dipendenze in un computer separato.
4. Spostare i file in una cartella accessibile dal server.
5. Eseguire un comando di installazione supportati o l'istruzione DDL per installare il pacchetto nella libreria di istanza.

### <a name="download-the-package-as-a-zipped-file"></a>Scaricare il pacchetto come file compresso

Per l'installazione in un server senza accesso a internet, è necessario scaricare una copia del pacchetto nel formato di un file compresso per l'installazione offline. **Non decomprimere il pacchetto.**

Ad esempio, la procedura seguente descrive adesso per ottenere la versione corretta del [FISHalyseR](http://bioconductor.org/packages/release/bioc/html/FISHalyseR.html) pacchetto da Bioconductor, supponendo che il computer abbia accesso a internet.

1.  Nell'elenco **Archivi dei pacchetti** , individuare la versione **binaria di Windows** .

2.  Fare doppio clic sul collegamento per il. File ZIP e selezionare **destinazione Salva come**.

3.  Passare alla cartella locale in cui vengono archiviati, pacchetti compressi e fare clic su **salvare**.

    Questo processo crea una copia locale del pacchetto. 

4. Se si verifica un errore di download, provare a un sito mirror diversi.

5. Dopo aver scaricato l'archivio pacchetti, è possibile installare il pacchetto o copiare il pacchetto compresso in un server che non dispone dell'accesso a internet.

> [!TIP]
> Se per errore, si installa il pacchetto anziché essere scaricato i file binari, una copia del file compresso scaricato viene salvata anche nel computer. Controllare i messaggi di stato mentre il pacchetto viene installato per determinare il percorso del file. È possibile copiare il file compresso per il server che non dispone dell'accesso a internet.
> 
> Tuttavia, quando si ottiene utilizzando questo metodo di pacchetti, le dipendenze non vengono incluse. 


## <a name="side-by-side-installation-with-standalone-r-or-python-servers"></a>Installazione side-by-side con server Python o Standalone R

R e Python sono incluse in diversi prodotti Microsoft, ognuno dei quali può coesistere nello stesso computer.

Se è installato SQL Server 2017 Microsoft Machine Learning Server (Standalone) o SQL Server 2016 R Server (Standalone) oltre a analitica nel database (SQL Server 2017 Machine Learning Services e SQL Server 2016 R Services), il computer dispone separato installazioni di R per ogni, con i duplicati di tutti i strumenti di R e librerie.

I pacchetti installati nella libreria R_SERVER vengono utilizzati solo da un server autonomo e non accessibili da un'istanza di SQL Server (In-Database). Utilizzare sempre il `R_SERVICES` libreria quando si installano pacchetti che si desidera utilizzare nel database in SQL Server. Per ulteriori informazioni sui percorsi, vedere [libreria posizione pacchetto](installing-and-managing-r-packages.md#package-library-location).


## <a name="see-also"></a>Vedere anche

+ [Installare nuovi pacchetti Python](../python/install-additional-python-packages-on-sql-server.md)
+ [Esercitazioni, esempi, soluzioni](../tutorials/machine-learning-services-tutorials.md)