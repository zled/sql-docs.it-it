---
title: L'installazione hardware - Analitica Platform System | Documenti Microsoft
description: In questo articolo viene descritto come spostare, decomprimere e installare i componenti hardware per il dispositivo di SQL Server PDW. In questo articolo è esclusivamente informativo e consentono di comprendere il processo. Il dispositivo deve essere decompresso, installato e verificato prima che all'utente è attivata. La partecipazione cliente è obbligatoria per gli elementi, ad esempio data center di accesso, alimentazione elettrica e connessioni Ethernet.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 169b38a1228f909a79d7866eba20b85b4a56c30b
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
ms.locfileid: "31539091"
---
# <a name="hardware-installation-for-analytics-platform-system-appliance"></a>Installazione dell'hardware per il dispositivo di sistema della piattaforma Analitica
In questo articolo viene descritto come spostare, decomprimere e installare i componenti hardware per il dispositivo di SQL Server PDW. In questo articolo è esclusivamente informativo e consentono di comprendere il processo. Il dispositivo deve essere decompresso, installato e verificato prima che all'utente è attivata. La partecipazione cliente è obbligatoria per gli elementi, ad esempio data center di accesso, alimentazione elettrica e connessioni Ethernet.  
  
## <a name="BeforeMoving"></a>Prima di spostare tutti i componenti dal carico  
Le seguenti operazioni prima di spostare, decomprimere o rack i componenti del dispositivo.  
  
|Attività|Description|  
|--------|---------------|  
|Verificare che tutti i componenti sono arrivati|Utilizzare la distinta base (BOM) per verificare che tutti i componenti sono arrivati e sul loro palette all'ancoraggio ricevente per il data center.|  
|Verificare che il data center soddisfi tutti i requisiti per l'applicazione|Questa attività di avvio esaminando le specifiche hardware e cablaggio diagrammi fornendo per il fornitore. I passaggi successivi forniscono i dettagli su rack requisiti di spazio e la connettività.|  
|Verificare che il data center disponga di spazio appropriata nel rack|Verificare che il data center dispone di spazio sufficiente per tutti i rack del dispositivo.<br /><br />Verificare che lo spazio rack sia vuoto e pronto a ricevere il rack del dispositivo.|  
|Verificare che il data center soddisfi i requisiti di connettività|Verificare che il data center soddisfi i requisiti di cablaggi nei diagrammi di cablaggio.<br /><br />Verificare che non vi saranno spazio per tutti i cavi di alimentazione dopo che sono centralizzato in remoto i nodi dello strumento.|  
|Verificare che i piani tra ancoraggio e il rack soddisfino i requisiti di peso|Verificare che tutti impermeabili tra le palette e il rack possono supportare il peso dei nodi del dispositivo, in particolare nei data center con piani generati.<br /><br />Per informazioni sul peso di ogni componente, contattare il fornitore.|  
|Proteggere il data center rack|Proteggere il data center rack sul posto utilizzando apparecchiature aggiuntive necessarie per la posizione del data center, ad esempio rimovibili terremoto in aree geografiche soggette a terremoti.|  
|Preparazione per l'assistenza per il trasporto dei componenti|Determinare in anticipo quali assistenza, attrezzature e gli strumenti che necessari per gestire ogni componente in modo sicuro e senza causare danni.|  
  
## <a name="Moving"></a>Spostare il rack da ancoraggio durante il caricamento nel Data Center  
Ogni tavolozza contiene tutti i componenti per rack di un dispositivo, inclusi i nodi, cavi, cavi e così via.  
  
Utilizzare il seguente elenco per spostare ogni rack del dispositivo dalla tavolozza a carico posizione rack del centro dati. Spostare prima il rack di controllo e quindi spostare altri rack di dati di dispositivo.  
  
> [!WARNING]  
> Eseguire questi passaggi, esattamente come descritto può verificarsi lesioni personali, danni al dispositivo di SQL Server PDW o altri problemi.  
>   
> Non tentare mai di accuratezza o spostare un nodo di dispositivo o un altro componente elevato senza l'assistenza o ad apparecchiature appropriata. Per informazioni sul peso di ogni componente, in modo che è possibile determinare in anticipo quali assistenza, attrezzature e gli strumenti che necessari per gestire ogni componente in modo sicuro e senza causare danni, contattare il fornitore.  
  
|Attività|Description|  
|--------|---------------|  
|Verificare che la tavolozza livello|Prima di iniziare a spostare o decomprimere la tavolozza, assicurarsi che sia su livello zero.|  
|Un nodo dalla tavolozza unbolt|A partire dalla parte superiore della tavolozza, unbolt il nodo principale dalla tavolozza.|  
|Spostare il nodo in un carrello in grado di supportare il peso o un carrello|Utilizzare sfumature e tecniche appropriate alla rimozione o spostamento per spostare il nodo in un carrello in grado di supportare il peso o un carrello.|  
|Il nodo di trasporto nel data center|Per spostare il nodo nella posizione desiderata in rack del centro dati, utilizzare tecniche appropriate alla rimozione o spostamento.|  
|Proteggere il nodo nel data center rack|Proteggere il nodo sul posto nel data center rack.|  
|Ripetere questi passaggi per il nodo o il componente|Ripetere questi passaggi per spostare il nodo successivo o un altro componente di dispositivo nel data center.|  
  
## <a name="AfterMoving"></a>Installare i componenti aggiuntivi  
Utilizzare l'elenco di controllo seguente per installare i componenti aggiuntivi.  
  
|Attività|Description||  
|--------|---------------|-|  
|Decomprimere e rack PDU e switch di rete|Utilizzare i diagrammi di rack per posizionare i commutatori di rete e una PDU nella posizione corretta nel rack.||  
|Collegare i cavi Infiniband ed Ethernet in base alle etichette di cavo|Vedere il diagramma di cablaggio. Ogni cavo dispone di un'etichetta a ogni estremità che specifica in cui è necessario essere connessi.||  
|Collegare tutti i cavi di alimentazione|Vedere il diagramma di cablaggio.||  
|Attivare l'alimentatore rack e i PDU|Connettere l'alimentatore rack e dal rack, per il PDU. **Non accendere tutti gli altri componenti di dispositivo in questo momento.**||  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
