---
title: Evitare gli errori di pacchetti R installati nelle librerie utente | Documenti Microsoft
titleSuffix: SQL Server
ms.custom: ''
ms.date: 02/20/2018
ms.reviewer: ''
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.author: heidist
author: HeidiSteen
manager: cgronlun
ms.workload: Inactive
ms.openlocfilehash: a3498ca0940384dacf9f67ac916d78eee939f829
ms.sourcegitcommit: 059fc64ba858ea2adaad2db39f306a8bff9649c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/04/2018
---
# <a name="avoiding-errors-on-r-packages-installed-in-user-libraries"></a>Evitare gli errori di pacchetti R installati nelle librerie utente
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Gli utenti esperti di R sono abituati a installare pacchetti R in una raccolta di utente, ogni volta che la libreria predefinita è bloccato o non disponibile. Tuttavia, questo approccio non è supportato in SQL Server e installazione di una libreria utente termina in genere un errore "Impossibile trovare il pacchetto".

Questo articolo descrive soluzioni alternative per evitare questo errore. Viene illustrato come è possibile modificare il codice R e suggerisce il processo di installazione di pacchetti R corretto per l'utilizzo di pacchetti R da un'istanza di SQL Server.

## <a name="why-r-user-libraries-cannot-be-accessed-from-sql-server"></a>Perché le librerie utente R non sono accessibili da SQL Server

Gli sviluppatori R che devono installare i nuovi pacchetti R sono abituati per l'installazione dei pacchetti quando è necessario, mediante una privata e una libreria utente ogni volta che la libreria predefinita non è disponibile, oppure quando lo sviluppatore non è un amministratore nel computer.

Ad esempio, in un tipico ambiente di sviluppo di R, l'utente sarebbe il percorso del pacchetto la variabile di ambiente R `libPath`, o riferimento al percorso completo del pacchetto, simile al seguente:

```R
library("c:/Users/<username>/R/win-library/packagename")
```

Non funziona durante l'esecuzione di soluzioni R in SQL Server, perché i pacchetti R devono essere installati in una raccolta predefinito specifico che viene associata all'istanza. Quando un pacchetto non è disponibile nella libreria predefinita, viene visualizzato questo errore quando si tenta di chiamare il pacchetto:

*Errore in library(xxx): nessun pacchetto denominato 'package-name'*

## <a name="how-to-avoid-package-not-found-errors"></a>Come evitare errori di "non trovato nel pacchetto"

+ Eliminare le dipendenze sulle librerie utente 

    È una procedura di sviluppo non valido per installare i pacchetti R richiesti in una raccolta di utente personalizzato, come può causare errori se una soluzione viene eseguita da un altro utente che non ha accesso al percorso di libreria.

    Inoltre, se è installato un pacchetto della libreria predefinita, il runtime di R carica il pacchetto dalla libreria predefinita, anche se è specificata una versione diversa nel codice R.

+ Modificare il codice per l'esecuzione in un ambiente condiviso.

+ Evitare di installare i pacchetti come parte di una soluzione. Se non si dispone delle autorizzazioni necessarie per installare i pacchetti, il codice avrà esito negativo. Anche se si dispone delle autorizzazioni per installare i pacchetti, è consigliabile pertanto separatamente da altro codice che si desidera eseguire.

+ Controllare il codice per assicurarsi che non ci siano chiamate a pacchetti non installati.

+ Aggiornare il codice per rimuovere i riferimenti diretti ai percorsi di pacchetti R o librerie R. 

+ Conoscere la libreria di package è associata all'istanza. Per ulteriori informazioni, vedere [pacchetti R installati con SQL Server](installing-and-managing-r-packages.md)
