---
title: Configurare il sistema di Windows esterno per ottenere copie della tabella remota InfiniBand PDW
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: 
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/13/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f866890b-cad5-49ac-bbeb-848bfb26c2d5
caps.latest.revision: "11"
ms.openlocfilehash: efebff74a8c17952b39efb43006051603c624a03
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="configure-an-external-windows-system-to-receive-remote-table-copies-using-infiniband"></a>Configurare un sistema di Windows esterno per la ricezione di copie di tabella remota utilizzando InfiniBand
Viene descritto come acquistare e configurare un sistema di Windows non strumento connesso tramite la rete InfiniBand da usare con la funzionalità di copia tabella remota in SQL Server PDW. Il sistema di Windows verrà ospitato il database di SQL Server che riceve la copia della tabella remota da un database di SQL Server PDW. È acquistata separatamente dal dispositivo e connesso alla rete InfiniBand accessorio.  
  
> [!NOTE]  
> Connessione attraverso la rete InfiniBand non è necessaria per l'utilizzo di copia della tabella remota. Connessione tramite rete Ethernet può essere eseguita se la larghezza di banda Ethernet soddisfa le proprie esigenze.  
  
In questo argomento viene descritto uno dei passaggi di configurazione per la configurazione di copia della tabella remota. Per un elenco di tutti i passaggi di configurazione, vedere [copia della tabella remota](remote-table-copy.md)  
  
## <a name="before-you-begin"></a>Prima di iniziare  
Prima di configurare il sistema esterno di Windows, è necessario:  
  
1.  Acquistare o fornire un sistema di Windows che riceverà le copie remote.  
  
2.  Rack il sistema di Windows nel rack controllo (se è presente spazio sufficiente) o chiudere sufficiente per il dispositivo in modo che è possibile connettersi alla rete InfiniBand di dispositivo.  
  
3.  Acquistare una scheda di rete InfiniBand e dei cavi InfiniBand dal fornitore di hardware del dispositivo. Si consiglia di acquisto di una scheda di rete con due porte per la tolleranza di errore quando si ricevono i dati esportati. Una scheda di rete due porte è consigliabile, ma non è un requisito.  
  
## <a name="HowToWindows"></a>Configurare un sistema di Windows esterno per la ricezione di copie di una tabella remota  
Per configurare il sistema esterno di Windows, utilizzare la procedura seguente:  
  
1.  Installare la scheda di rete InfiniBand nel sistema di Windows.  
  
2.  Connettere la scheda di rete InfiniBand al commutatore InfiniBand principale nel rack controllo mediante cavi InfiniBand.  
  
3.  Installare e configurare il driver di Windows appropriato per la scheda di rete InfiniBand.  
  
    Driver InfiniBand per Windows vengono sviluppati da OpenFabrics Alliance, un consorzio di settore di fornitori InfiniBand.  Il driver corretto può distribuito con l'adattatore InfiniBand. In caso contrario, il driver può essere scaricato da www.openfabrics.org.  
  
4.  Configurare l'indirizzo IP per ogni porta nella scheda. Sistemi SMP devono utilizzare gli indirizzi IP statici da un intervallo di indirizzi riservati per questo scopo. Configurare la prima porta in base ai parametri seguenti:  
  
    -   Indirizzo IP: 172.16.132.x  
  
    -   Subnet mask IP: 255.255.128.0  
  
    -   Intervallo IP host: 1 a 254.  
  
    Per le schede di rete InfiniBand con due porte, configurare la seconda porta in base ai parametri seguenti:  
  
    -   Indirizzo IP: 172.16.132.x  
  
    -   Subnet mask IP: 255.255.128.0  
  
    -   Intervallo IP host: 1 a 254.  
  
5.  Se viene utilizzata una scheda di due porta o più sistemi Windows esterni connessi a un dispositivo, assegnare ogni sistema di un numero di host diverso all'interno di ogni subnet IP.  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
