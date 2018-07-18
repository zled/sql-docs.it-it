---
title: Suggerimenti per l'utilizzo di pacchetti R installati nelle librerie utente in SQL Server | Documenti Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/30/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: e52a6f4a9a3830aab01e54819804785a7069c9d2
ms.sourcegitcommit: 2d93cd115f52bf3eff3069f28ea866232b4f9f9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/01/2018
ms.locfileid: "34708469"
---
# <a name="tips-for-using-r-packages-in-sql-server"></a>Suggerimenti per l'uso di pacchetti R in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In questo articolo include sezioni separate per gli amministratori di database non hanno familiarità con R ed esperti R gli sviluppatori l'accesso ai pacchetti non si ha dimestichezza in un'istanza di SQL Server.

## <a name="new-to-r"></a>Familiarità con R

Un amministratore di installazione di R pacchetti per la prima volta, conoscere che alcuni concetti di base sulla gestione dei pacchetti R utili per iniziare.

### <a name="package-dependencies"></a>Dipendenze dei pacchetti

Pacchetti R spesso dipendono da altri più pacchetti, alcuni dei quali potrebbero non essere disponibili nella libreria R predefinito utilizzata dall'istanza. A volte un pacchetto richiede una versione diversa di un pacchetto dipendente che è già installato. Le dipendenze del pacchetto sono indicate in un file di descrizione incorporato nel pacchetto, ma in alcuni casi sono incomplete. È possibile utilizzare un pacchetto chiamato [iGraph](http://igraph.org/r/) per articolare completamente il grafico delle dipendenze.

Se è necessario installare più pacchetti o per assicurarsi che tutti gli utenti dell'organizzazione Ottiene il tipo di pacchetto corretto e la versione, è consigliabile utilizzare il [miniCRAN](https://mran.microsoft.com/package/miniCRAN) pacchetto per analizzare la catena di dipendenze completo. minicRAN crea un repository locale che può essere condivisa tra più utenti o computer. Per ulteriori informazioni, vedere [creare un repository di pacchetti locali tramite miniCRAN](create-a-local-package-repository-using-minicran.md).

### <a name="package-sources-versions-and-formats"></a>Formati, le versioni e origini dei pacchetti

Sono presenti più origini per i pacchetti R, ad esempio [CRAN](https://cran.r-project.org/) e [Bioconductor](https://www.bioconductor.org/). Il sito ufficiale per il linguaggio R (<https://www.r-project.org/>) elenca molte di queste risorse. Microsoft offre [MRAN](https://mran.microsoft.com/) per la distribuzione di R open source ([MRO](https://mran.microsoft.com/open)) e altri pacchetti. Molti pacchetti vengono pubblicati in GitHub, in cui gli sviluppatori possono ottenere il codice sorgente.

I pacchetti R eseguiti su più piattaforme di elaborazione. Assicurarsi che le versioni che installare siano file binari di Windows.

### <a name="know-which-library-you-are-installing-to-and-which-packages-are-already-installed"></a>Conoscere la libreria che si sta installando a e quali pacchetti sono già installati.

Se è stata modificata in precedenza nell'ambiente R nel computer, prima di installare nulla, verificare che la variabile di ambiente R `.libPath` utilizza solo un percorso.

Questo percorso deve puntare alla cartella R_SERVICES per l'istanza. Per altre informazioni, incluse le modalità determinare quali pacchetti sono già installati, vedere [predefinito R e Python pacchetti in SQL Server](installing-and-managing-r-packages.md).

## <a name="new-to-sql-server"></a>Novità in SQL Server

In qualità di sviluppatore R lavorando codice in esecuzione in SQL Server, i criteri di sicurezza che protegge il server vincolano la possibilità di controllare l'ambiente R.

### <a name="r-user-libraries-not-supported-on-sql-server"></a>Librerie utente R: non è supportata in SQL Server

Gli sviluppatori R che devono installare i nuovi pacchetti R sono abituati per l'installazione dei pacchetti quando è necessario, mediante una privata e una libreria utente ogni volta che la libreria predefinita non è disponibile, oppure quando lo sviluppatore non è un amministratore nel computer. Ad esempio, in un tipico ambiente di sviluppo di R, l'utente sarebbe il percorso del pacchetto la variabile di ambiente R `libPath`, o riferimento al percorso completo del pacchetto, simile al seguente:

```R
library("c:/Users/<username>/R/win-library/packagename")
```

Non funziona durante l'esecuzione di soluzioni R in SQL Server, perché i pacchetti R devono essere installati in una raccolta predefinito specifico che viene associata all'istanza. Quando un pacchetto non è disponibile nella libreria predefinita, viene visualizzato questo errore quando si tenta di chiamare il pacchetto:

*Errore in library(xxx): nessun pacchetto denominato 'package-name'*

### <a name="avoid-package-not-found-errors"></a>Evitare gli errori di "non trovato nel pacchetto"

+ Eliminare le dipendenze sulle librerie utente. 

    È una procedura di sviluppo non valido per installare i pacchetti R richiesti in una raccolta di utente personalizzato, come può causare errori se una soluzione viene eseguita da un altro utente che non ha accesso al percorso di libreria.

    Inoltre, se è installato un pacchetto della libreria predefinita, il runtime di R carica il pacchetto dalla libreria predefinita, anche se si specifica una versione diversa nel codice R.

+ Modificare il codice per l'esecuzione in un ambiente condiviso.

+ Evitare di installare i pacchetti come parte di una soluzione. Se non si dispone delle autorizzazioni necessarie per installare i pacchetti, il codice avrà esito negativo. Anche se si dispone delle autorizzazioni per installare i pacchetti, è consigliabile pertanto separatamente da altro codice che si desidera eseguire.

+ Controllare il codice per assicurarsi che non ci siano chiamate a pacchetti non installati.

+ Aggiornare il codice per rimuovere i riferimenti diretti ai percorsi di pacchetti R o librerie R. 

+ Conoscere la libreria di package è associata all'istanza. Per altre informazioni, vedere [predefinito R e Python pacchetti in SQL Server](installing-and-managing-r-packages.md).

## <a name="see-also"></a>Vedere anche

+ [Installare nuovi pacchetti R](install-additional-r-packages-on-sql-server.md)
+ [Installare nuovi pacchetti Python](../python/install-additional-python-packages-on-sql-server.md)
+ [Esercitazioni, esempi, soluzioni](../tutorials/machine-learning-services-tutorials.md)