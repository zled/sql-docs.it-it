---
title: Distribuire e utilizzare analitica utilizzando mrsdeploy | Documenti Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 0f785b4aece13dd2df27988ef6a2e5c6934045fd
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
ms.locfileid: "31201773"
---
# <a name="deploy-and-consume-analytics-using-mrsdeploy"></a>Distribuire e utilizzare analitica utilizzando mrsdeploy
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Microsoft R Server include una funzionalità, rendere operativo il **mrsdeploy**, che supporta queste attività:

+ La pubblicazione e gestione di modelli R e Python e codice sotto forma di servizi web
+ Utilizzo di questi servizi all'interno delle applicazioni client

In questo argomento vengono fornite informazioni su come abilitare e configurare la funzionalità.

Per informazioni generali sugli scenari supportati da **mrsdeploy**, vedere [rendere operativo con R Server](https://docs.microsoft.com/r-server/what-is-operationalization).

## <a name="using-mrsdeploy-for-operationalization"></a>Utilizzo di mrsdeploy per rendere operativo

La parola *rendere operativo il* può avere numerosi significati:

+ La possibilità di pubblicare i modelli a un servizio web per l'utilizzo da applicazioni
+ Supporto per il calcolo scalabile o distribuita
+ Una volta sviluppare, distribuire più volte
+ Assegnazione dei punteggi veloci, per entrambi a riga singola e dell'assegnazione punteggio batch

Se è stato installato Servizi di Machine Learning con SQL Server, *rendere operativo il* è una questione di wrapping del codice R o Python in una stored procedure. Qualsiasi applicazione può quindi chiamare la stored procedure per ripetere il training di un modello, generare punteggi o creare report. È inoltre possibile automatizzare i processi tramite meccanismi di pianificazione esistenti in SQL Server.

Tuttavia, Microsoft R Server fornisce un meccanismo diverso per il supporto di distribuzione, tramite i servizi web che supportano la pubblicazione di processi R e un'utilità di amministrazione per eseguire processi R distribuiti. Microsoft R Server utilizza le funzioni di **mrsdeploy** pacchetto per stabilire una sessione con nodi di calcolo remoto ed eseguire codice R in un'applicazione console.

Questa funzionalità di distribuzione di R Server offre i seguenti vantaggi:

+ Controllo di accesso basato sui ruoli per servizi web analitici

    Determinare chi può pubblicare, aggiornare ed eliminare i propri servizi web, gli utenti possono inoltre, aggiornare ed eliminare i servizi web pubblicati da altri utenti e l'utente può solo elenco e utilizzare i servizi web.

+ Più veloce di punteggio
  
  È possibile utilizzare in tempo reale di punteggio con un oggetto modello R supportato per migliorare la velocità di operazioni di assegnazione dei punteggi.

+ Utilizzo di batch asincrone

  Servizi Web che chiamano per dati di input di grandi dimensioni ora possono essere utilizzati in modo asincrono tramite l'esecuzione del batch.

+ Ridimensionamento automatico di una griglia dei nodi di calcolo e web

  Per consentire di creare facilmente rapidamente un set di macchine virtuali di Server di R in Azure e quindi configurarli come una griglia per operatività analitica ed esecuzione remota viene fornito un modello di script. In questa griglia può essere ridimensionato verso l'alto o verso il basso in base all'utilizzo della CPU.

+ Esecuzione remota asincrona

    Ora è supportata tramite il **mrsdeploy** pacchetto R. Per continuare a lavorare nell'ambiente di sviluppo durante l'esecuzione di script remoto, eseguire lo script di R in modo asincrono utilizzando il `async` parametro. Questo è particolarmente utile quando si eseguono gli script con lunghi tempi di esecuzione.

## <a name="requirements-and-configuration"></a>Requisiti e la configurazione

SQL Server 2017 CTP 2.0 e versioni successive è disponibile questa funzionalità, che in precedenza era disponibile solo con R Server e non è installato con SQL Server R Services. Il **mrsdeploy** pacchetto è installato nel computer SQL Server, se si seleziona l'opzione per installare **Microsoft Machine Learning Server**, dal **Caratteristiche condivise di** sezione del programma di installazione di SQL Server.

In genere, non è consigliabile installare Machine Learning Server nello stesso computer che esegue servizi di SQL Server Machine Learning. Si consiglia di installare **Microsoft Machine Learning Server** in un computer diverso da SQL Server e quindi configurare le funzionalità di rendere operativo del computer.

Tuttavia, se è necessario installarlo insieme, seguire questi passaggi aggiuntivi per configurare correttamente il servizio.

1. Installare DotNetCore 1.1

    Se .NET Core non è stato installato come parte di SQL Server, è necessario installarlo prima di iniziare l'installazione di R Server.

2. Installare Microsoft Machine Learning Server.

3. Al termine dell'installazione di **Microsoft Machine Learning Server**manualmente la chiave del Registro di sistema seguente per aggiungere **mrsdeploy**, che consente di specificare la cartella di base per i file R_SERVER. 

    + Creare una nuova chiave del Registro di sistema `H_KEY_LOCAL_MACHINE\SOFTWARE\R Server\Path`
    + Impostare il valore della chiave da `"C:\Program Files\Microsoft SQL Server\140\R_SERVER"`.

4. Al termine, aprire il [amministratore utilità](https://docs.microsoft.com/r-server/operationalize/configure-use-admin-utility).

5. Continuare a configurare il **mrsdeploy** service come descritto qui: [configurazione per gli amministratori](https://docs.microsoft.com/r-server/operationalize/configure-start-for-administrators)

6. Per ulteriori informazioni, vedere [mrsdeploy funzioni](https://docs.microsoft.com/r-server/r-reference/mrsdeploy/mrsdeploy-package).
