---
title: "Il caricamento di capacità pianificazione foglio di lavoro Server (SQL Server PDW)"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: sql-non-specified
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: analytics-platform-system
ms.suite: sql
ms.custom: 
ms.technology: mpp-data-warehouse
description: "Questo foglio di lavoro Pianificazione della capacità consente di determinare i requisiti per un server di caricamento per il caricamento dei dati in SQL Server PDW."
ms.date: 01/05/2017
ms.topic: article
ms.assetid: df2155be-a624-40ba-9a85-58af708f7ce7
caps.latest.revision: "9"
ms.openlocfilehash: e14d4baca91e0b892b84620330655271fa67badb
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="loading-server-capacity-planning-worksheet"></a>Il caricamento di foglio di lavoro di pianificazione della capacità server
Questo foglio di lavoro Pianificazione della capacità consente di determinare i requisiti per un server di caricamento per il caricamento dei dati in SQL Server PDW. Consente di creare il piano per l'acquisto o provisioning esistente durante il caricamento di server.  
  
## <a name="worksheet-notes"></a>Note di foglio di lavoro
  
1.  Questo foglio di lavoro si applica ai server caricamento di dati con il **dwloader** strumento durante il caricamento della riga di comando.  
  
2.  Per il caricamento dei dati con Integration Services o un terzo strumento di caricamento di entità, i requisiti possono variare in base differenze nel processo di caricamento.  
  
3.  La maggior parte dei requisiti si applicano al caricamento di un file di dati compressa o non compressa. eventuali differenze nei requisiti sono indicate in grassetto.  
  
## <a name="clipboardmediaclipboard-iconpng-clipboard-capacity-planning-worksheet"></a>![Appunti](media/clipboard-icon.png "Appunti") foglio di lavoro di pianificazione della capacità  
  
Questo foglio di lavoro di stampa e popolarlo con i propri requisiti.  
  
|Componente|Requisito|Compilare questa colonna con i propri requisiti|Indicazioni|  
|-------------|---------------|--------------------------------------------------|-------------------|  
|Archiviazione|Numero massimo di byte che si prevede di archiviare nel server durante il caricamento in qualsiasi periodo di tempo specificato.|![Icona della matita](media/pencil-icon.png "icona della matita")|Per determinare i requisiti di archiviazione, determinare la quantità di dati si intende archiviare nel server durante il caricamento in qualsiasi periodo di tempo specificato.  Requisiti di capacità sono per caricare file di sola lettura. il sistema operativo e i file del carico devono essere in array di dischi diverso.<br /><br />Ad esempio: se si intende caricare 100 GB di dati dal disco 3 volte al giorno, ma non eliminare i file di dati fino alla fine della settimana, quindi è necessario un minimo TB 2.1 per archiviare i file di dati. È consigliabile essere conservativo e recupero sull'archiviazione di più di 30% per tenere conto delle varianze e aumento delle dimensioni.  Per questo esempio, sarebbe migliore 2,73 TB di spazio di archiviazione.|  
|Frequenza di caricamento|Numero massimo di byte all'ora di dati da caricare in PDW.|![Icona della matita](media/pencil-icon.png "icona della matita")|Si tratta di una stima. Durante il calcolo di questo requisito, si presuppone che i file sono già nel server durante il caricamento e che siano ottimale, altre condizioni di carico.<br /><br />Ad esempio: non è necessario tenere in considerazione la compressione dati poiché dwloader invia sempre i dati non compressi a di PDW. Non è necessario tenere in considerazione le conversioni di tipo di dati e le dimensioni della tabella di destinazione.|  
|Rete|Tipo di connessione di rete.|![Icona della matita](media/pencil-icon.png "icona della matita")|Determinare il tipo di connessione di rete migliore per i requisiti di velocità di carico.<br /><br />Ad esempio: InfiniBand o 10 GB Ethernet fornirà le velocità di caricamento ottimale. 1 Gbit Ethernet limiterà i tassi di carico a 360 GB all'ora o meno.|  
|I/O|Byte per ogni ora per le letture e scritture.|![Icona della matita](media/pencil-icon.png "icona della matita")|Per caricare i dati, dwloader deve leggere tutti i dati dal disco prima di inviarlo a PDW.<br /><br />Ogni server di caricamento non è possibile caricare i dati più velocemente di quanto il dispositivo può ricevere dati da tutte le origini di caricamento. Per risparmiare denaro, pianificare il / o leggere la capacità per il caricamento in modo che non superi la capacità di carico del dispositivo.<br /><br />Esempio:<br />PDW riceve e carica i dati in un dispositivo 1 rack una velocità massima di 1,8 TB per ogni ora. Per un dispositivo con 2 o più rack, la velocità di carico massimo è 3,6 TB per ogni ora.<br /><br />Se si prevede di caricare contemporaneamente da più server di caricamento, i requisiti dei / o per ogni server di caricamento sarà minore rispetto a quando un server esegue tutti il caricamento.<br /><br />Ad esempio: un server di caricamento può caricare un massimo di 1,8 TB per ogni ora per un dispositivo 1 rack. Due server il caricamento potrebbe ogni caricare simultaneamente i 900 GB all'ora in un dispositivo 1 rack. Livelli superiori di concorrenza consente di ridurre l'efficienza e la velocità effettiva massima.<br /><br />Capacità dei / o, prendere in considerazione tutti il / o nel server durante il caricamento in corso. Se il server durante il caricamento ha altro traffico dei / o oltre ai carichi di dati, ad esempio la ricezione di file di dati da un server ETL, aumenta i requisiti dei / o.<br /><br />I dati compressi, i requisiti dei / o dipendono dal tasso di compressione dati. dwloader legge i dati compressi e quindi decomprime, prima di inviarlo a PDW. Maggiore il rapporto di compressione, minore quantità di dati di caricamento server dovrà essere letti dal disco.<br /><br />Ad esempio: se la velocità di carico richiesto è 1,8 TB per ogni ora, i dati vengono archiviati nel server durante il caricamento con la compressione di 2:1, quindi il server di caricamento deve solo leggere 900 GB all'ora dal disco anziché 1,8 TB. Un rapporto di compressione 3:1 indica che il server di caricamento deve leggere 600 GB all'ora dal disco.|  
|CPU|Numero di socket.|![Icona della matita](media/pencil-icon.png "icona della matita")|Per il caricamento dei dati non compressi, dwloader non è un'applicazione con utilizzo intensivo della CPU.  Come requisito minimo, è consigliabile utilizzare un server socket 2 prodotta di recente.<br /><br />Per il caricamento dei dati compressi, è necessario sufficiente potenza della CPU per decomprimere i dati prima di inviarlo a PDW. dwloader eseguire 10 thread attivi in una sola volta. Se si prevede di caricare simultaneamente i 10 file compressi, è consigliabile che il server disponga di almeno 10 core CPU o due 6 core CPU.|  
|RAM|GB di memoria che consente a Windows per i file di cache durante carica.|![Icona della matita](media/pencil-icon.png "icona della matita")|dwloader utilizza minima di RAM nel server durante il caricamento. Per le prestazioni, Windows Usa la memoria per memorizzare nella cache i file di caricamento dopo la relativa lettura dal disco.<br /><br />Per determinare i requisiti di RAM, vedere Installazione di Windows Server e qualsiasi 3 requisiti dell'applicazione di terze parti. Se non si prevedono requisiti da altre origini, è consigliabile un minimo di 32 GB.<br /><br />I dati compressi, RAM più veloce è utile perché velocizza la decompressione.|  
  
## <a name="see-also"></a>Vedere anche  
[Acquisire e configurare un server di caricamento](acquire-and-configure-loading-server.md)  
[dwloader caricatore della riga di comando](dwloader.md)  
  
