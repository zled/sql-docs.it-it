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
ms.openlocfilehash: 8f7b0ee2b623f6a208a92823948bf0295bae33f6
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34707499"
---
# <a name="use-r-package-managers-to-install-r-packages-on-sql-server"></a>Utilizzare gestori di pacchetti R per installare pacchetti R in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

È possibile utilizzare gli strumenti standard di R per installare i nuovi pacchetti in un'istanza di SQL Server 2016 o SQL Server 2017, fornendo il computer dispone di una porta aperta 80 e disporre di diritti di amministratore.

> [!IMPORTANT] 
> Assicurarsi di installare i pacchetti per la libreria predefinita associata con l'istanza corrente. Non installare mai pacchetti in una directory dell'utente.

Questa procedura Usa RGui ma è possibile utilizzare RTerm o qualsiasi altro R della riga di comando dello strumento che supporta l'accesso con privilegi elevato.

## <a name="install-a-package-using-rgui"></a>Installare un pacchetto utilizzando RGui

1. [Determinare il percorso della libreria di istanza](installing-and-managing-r-packages.md). Passare alla cartella in cui sono installati gli strumenti di R. Ad esempio, il percorso predefinito per un'istanza predefinita di SQL Server 2017 è come segue: `C:\Program Files\MSSQL14.MSSQLSERVER\R_SERVICES\bin\x64`

1. RGui.exe e scegliere **Esegui come amministratore**. Se non si dispone delle autorizzazioni necessarie, contattare l'amministratore del database e fornire un elenco dei pacchetti che è necessario.

1. Dalla riga di comando, se si conosce il nome del pacchetto, è possibile digitare: `install.packages("the_package-name")` tra virgolette sono necessarie per il nome del pacchetto.

1. Quando viene richiesto un sito mirror, è possibile selezionare qualsiasi sito a cui è utile per il percorso.

Se il pacchetto di destinazione dipende da pacchetti aggiuntivi, il programma di installazione di R automaticamente le dipendenze vengono scaricate e li installa automaticamente.

Se sono presenti più istanze di SQL Server, ad esempio le istanze side-by-side di SQL Server 2016 R Services e SQL Server 2017 Machine Learning Services, installazione separatamente per ogni istanza se si desidera utilizzare il pacchetto in entrambi i contesti. Pacchetti non possono essere condivisa tra più istanze.

## <a name = "bkmk_offlineInstall"></a> Installazione offline utilizzando gli strumenti di R

Se il server non ha accesso a internet, sono necessari ulteriori passaggi per preparare i pacchetti. Per installare pacchetti R in un server che non dispone dell'accesso a internet, è necessario:

+ Analizzare le dipendenze in anticipo.
+ Scaricare il pacchetto di destinazione in un computer con accesso a Internet.
+ Scaricare tutti i pacchetti necessari nello stesso computer e inserire tutti i pacchetti in un archivio singolo pacchetto.
+ Codice postale archivio se non è già in formato compresso.
+ Copiare l'archivio di pacchetto in un percorso sul server.
+ Installare il pacchetto di destinazione, specificando il file di archivio come origine.

> [!IMPORTANT] 
>  Verificare che per analizzare tutte le dipendenze e scaricare **tutti** necessari pacchetti **prima** iniziare l'installazione. È consigliabile [miniCRAN](https://mran.microsoft.com/package/miniCRAN) per questo processo. Il pacchetto R accetta un elenco di pacchetti da installare, consente di analizzare le dipendenze e ottiene tutti i file compressi automaticamente. miniCRAN crea quindi un singolo archivio che è possibile copiare nel computer server. Per informazioni dettagliate, vedere [creare un repository di pacchetti locali tramite miniCRAN](create-a-local-package-repository-using-minicran.md)

Questa procedura si presuppone che sia stato preparato tutti i pacchetti necessari, in formato compresso e sono pronti per copiarli nel server.

1. Copia il pacchetto compresso file o per più pacchetti, il repository completo che contiene tutti i pacchetti compressi formato, in una posizione che il server può accedere.

2. Aprire la cartella nel server in cui sono installati gli strumenti R per l'istanza. Ad esempio, se si utilizza il prompt dei comandi di Windows in un sistema con SQL Server 2016 R Services, passare al `C:\Program Files\MSSQL13.MSSQLSERVER\R_SERVICES\bin\x64`.

3. Fare clic su RGui o RTerm e selezionare **Esegui come amministratore**.

4. Eseguire il comando di R `install.packages` e specificare il pacchetto o nome di repository e il percorso del file ZIP.

    ```R
    install.packages("C:\\Temp\\Downloaded packages\\mynewpackage.zip", repos=NULL)
    ```

    Questo comando consente di estrarre il pacchetto R `mynewpackage` dal file compresso locale, presupponendo che la copia è stato salvato nella directory `C:\Temp\Downloaded packages`, quindi installa il pacchetto nel computer locale. Se il pacchetto contiene tutte le dipendenze, il programma di installazione verifica i pacchetti esistenti nella libreria. Se è stato creato un repository che include le dipendenze, il programma di installazione installa anche i pacchetti richiesti.

    Se tutti i pacchetti necessari non sono presenti nella libreria di istanza e non possono essere disponibile nei file compressi, l'installazione del pacchetto di destinazione non riesce.

## <a name="see-also"></a>Vedere anche

+ [Installare nuovi pacchetti R](install-additional-r-packages-on-sql-server.md)
+ [Installare nuovi pacchetti Python](../python/install-additional-python-packages-on-sql-server.md)
+ [Esercitazioni, esempi, soluzioni](../tutorials/machine-learning-services-tutorials.md)