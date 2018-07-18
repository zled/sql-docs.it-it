---
title: Configurare Windows per la tabella remota copie - Parallel Data Warehouse di ricezione | Documenti Microsoft
description: Viene descritto come acquistare e configurare un sistema di Windows non strumento connesso tramite la rete InfiniBand da usare con la funzionalità di copia tabella remota in Parallel Data Warehouse. Il sistema di Windows verrà ospitato il database di SQL Server che riceve la copia della tabella remota da un database di SQL Server PDW. È acquistata separatamente dal dispositivo e connesso alla rete InfiniBand accessorio.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: ed7122f497b0bdebd893eec75606bbb6382e9a73
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
ms.locfileid: "31538771"
---
# <a name="configure-an-external-windows-system-to-receive-remote-table-copies-using-infiniband---parallel-data-warehouse"></a>Configurare un sistema esterno di Windows per la ricezione di copie di tabella remota utilizzando InfiniBand - Parallel Data Warehouse
Viene descritto come acquistare e configurare un sistema di Windows non strumento connesso tramite la rete InfiniBand da usare con la funzionalità di copia tabella remota in SQL Server PDW. Il sistema di Windows verrà ospitato il database di SQL Server che riceve la copia della tabella remota da un database di SQL Server PDW. È acquistata separatamente dal dispositivo e connesso alla rete InfiniBand accessorio.  
  
> [!NOTE]  
> Connessione attraverso la rete InfiniBand non è necessaria per l'utilizzo di copia della tabella remota. Connessione tramite rete Ethernet può essere eseguita se la larghezza di banda Ethernet soddisfa le proprie esigenze.  
  
In questo argomento viene descritto uno dei passaggi di configurazione per la configurazione di copia della tabella remota. Per un elenco di tutti i passaggi di configurazione, vedere [copia tabella remota](remote-table-copy.md)  
  
## <a name="before-you-begin"></a>Prima di iniziare  
Prima di configurare il sistema esterno di Windows, è necessario:  
  
1.  Acquistare o fornire un sistema di Windows che riceverà le copie remote.  
  
2.  Rack il sistema di Windows nel rack controllo (se è presente spazio sufficiente) o chiudere sufficiente per il dispositivo in modo che è possibile connettersi alla rete InfiniBand di dispositivo.  
  
3.  Acquistare una scheda di rete InfiniBand e dei cavi InfiniBand dal fornitore di hardware del dispositivo. Si consiglia di acquisto di una scheda di rete con due porte per la tolleranza di errore quando si ricevono i dati esportati. Una scheda di rete due porte è consigliabile, ma non è un requisito.  
  
## <a name="HowToWindows"></a>Configurare un sistema di Windows esterno per ricevono una copia di tabella remota  
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
  
