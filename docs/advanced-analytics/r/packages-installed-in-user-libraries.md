---
title: Evitare gli errori di pacchetti R installati nelle librerie utente | Documenti Microsoft
ms.custom: 
ms.date: 09/29/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 99ffd9b8-aa6d-4ac2-9840-4e66d0463978
caps.latest.revision: 2
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 29122bdf543e82c1f429cf401b5fe1d8383515fc
ms.openlocfilehash: 0de06ebee16d903b4b00c9d8e4673bf450c485d1
ms.contentlocale: it-it
ms.lasthandoff: 10/10/2017

---
# <a name="avoiding-errors-on-r-packages-installed-in-user-libraries"></a>Evitare gli errori di pacchetti R installati nelle librerie utente

Gli utenti esperti di R sono abituati a installare pacchetti R in una raccolta di utente, ogni volta che la libreria predefinita è bloccato o non disponibile. Tuttavia, questo approccio non è supportato in SQL Server e installazione di una libreria utente termina in genere un errore "Impossibile trovare il pacchetto".

In questo argomento vengono illustrate soluzioni alternative per evitare questo errore. Viene illustrato come è possibile modificare il codice R e suggerisce il processo di installazione di pacchetti R corretto per l'utilizzo di pacchetti R da un'istanza di SQL Server.

## <a name="why-r-user-libraries-cannot-be-accessed-from-sql-server"></a>Perché le librerie utente R non sono accessibili da SQL Server

Gli sviluppatori R che devono installare i nuovi pacchetti R sono abituati per l'installazione dei pacchetti quando è necessario e utilizza una libreria utente privato, ogni volta che la libreria predefinita non è disponibile, o quando lo sviluppatore non è un amministratore nel computer.

Ad esempio, in un tipico ambiente di sviluppo di R, l'utente sarebbe il percorso del pacchetto la variabile di ambiente R `libPath`, o riferimento al percorso completo del pacchetto, simile al seguente:

```R
library("c:/Users/<username>/R/win-library/packagename")  
```

Tuttavia, ciò non possa mai funzionare durante l'esecuzione di soluzioni R in SQL Server, perché i pacchetti R devono essere installati in una raccolta predefinito specifico che viene associata all'istanza.

Se il pacchetto non è installato nella libreria predefinita, potrebbe essere visualizzato un errore analogo al seguente quando si tenta di chiamare il pacchetto:

*Errore in library(xxx): nessun pacchetto denominato 'package-name'*

È inoltre una procedura di sviluppo non valido per installare i pacchetti R richiesti in una raccolta di utente personalizzato, come può causare errori se una soluzione viene eseguita da un altro utente che non ha accesso al percorso di libreria.

## <a name="how-to-install-r-packages-to-an-accessible-library"></a>Come installare i pacchetti R in una libreria accessibile

**Per SQL Server 2016**

Utilizzare la libreria di pacchetto associata all'istanza. Per informazioni dettagliate, vedere [pacchetti R installati con SQL Server](installing-and-managing-r-packages.md)

**Per SQL Server 2017**

SQL Server fornisce funzionalità che consentono di gestire più versioni del pacchetto e concedere agli utenti le autorizzazioni per singoli pacchetti, senza richiedere che gli utenti hanno accesso al file system.

Per informazioni dettagliate su come impostare una libreria condivisa pacchetto e assegnare utenti a ruoli, vedere [gestione dei pacchetti R per SQL Server](r-package-management-for-sql-server-r-services.md).

Se si adotta l'approccio di gestione di pacchetto in base ai ruoli di database, non è necessario installare più copie dello stesso pacchetto nella directory dell'utente diverso. Installare una singola copia del pacchetto è necessario e condividerlo con gli utenti autenticati. Poiché i pacchetti sono gestiti a livello di database, è inoltre possibile copiare i gruppi di pacchetti e le autorizzazioni correlate tra database.

## <a name="tips-for-avoiding-package-not-found-errors"></a>Suggerimenti per evitare errori di "non trovato nel pacchetto"

+ Modificare il codice per eliminare le dipendenze sulle librerie utente. Quando si esegue la migrazione di soluzioni R per l'esecuzione in [!INCLUDE [ssNoVersion_md](..\..\includes\ssnoversion-md.md)], è importante eseguire le operazioni seguenti:

    + Installare tutti i pacchetti che è necessario per la libreria predefinita associata all'istanza.

    + Modificare il codice per verificare che i pacchetti siano caricati dalla libreria predefinita, non dalla directory ad hoc o librerie utente.

+ Evitare l'installazione del pacchetto ad hoc come parte di una soluzione. Controllare il codice per assicurarsi che non sono presenti chiamate a pacchetti non installati o codice che consente di installare i pacchetti in modo dinamico. Se non si dispone delle autorizzazioni, il codice avrà esito negativo e, se si dispone delle autorizzazioni, è necessario installare separatamente i pacchetti da altro codice che si desidera eseguire.

+ Modificare tutti i percorsi di librerie del pacchetto R diretti. Se un pacchetto è installato nella libreria predefinita, il runtime R lo caricherà dalla libreria predefinita, anche se viene specificata un'altra libreria nel codice R.

