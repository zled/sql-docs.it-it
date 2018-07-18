---
title: Altre architetture Driver | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- drivers [ODBC], heterogeneous join engines
- drivers [ODBC], ODBC on the server
- ODBC architecture [ODBC], drivers
- heterogeneous join engines[ODBC]
- drivers [ODBC], middle component
ms.assetid: 1cad06ee-5940-4361-8d01-7d850db1dd66
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 52b51847dee6dbe59a7bb4495e0739d2ee08c005
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32916876"
---
# <a name="other-driver-architectures"></a>Altre architetture di Driver
Alcuni driver ODBC è strettamente conforme all'architettura descritto in precedenza. È possibile che i driver di svolgere i compiti diversi da quelli di un driver ODBC tradizionale, o non sono driver in senso normale.  
  
## <a name="driver-as-a-middle-component"></a>Driver come un componente centrale  
 Il driver ODBC può trovarsi tra gestione Driver e uno o più driver ODBC. Quando il driver al centro è in grado di lavorare con più origini dati, serve un dispatcher di chiamate ODBC (o chiamate tradotte in modo appropriato) ad altri moduli che effettivamente accedere alle origini dati. In questa architettura, il driver nella parte centrale richiede alcuni del ruolo di una gestione Driver.  
  
 Un altro esempio di questo tipo di driver è un programma spy per ODBC, che consente di intercettare e copia le funzioni ODBC inviate tra il gestore di Driver e il driver. Questo livello può essere utilizzato per emulare un driver o un'applicazione. Per la gestione di Driver, il livello viene visualizzato per il driver; per il driver, il livello viene visualizzato da Gestione Driver.  
  
## <a name="heterogeneous-join-engines"></a>Motori di Join eterogeneo  
 Alcuni driver ODBC vengono compilate al momento di un motore di query per l'esecuzione di join eterogenei. In un'architettura di un motore di join eterogenei (vedere la figura seguente), il driver viene visualizzato l'applicazione come un driver ma viene visualizzato a un'altra istanza di gestione Driver come un'applicazione. Il driver elabora un join eterogeneo dall'applicazione chiamando nei driver in istruzioni SQL separate per ogni database unito in join.  
  
 ![Architettura di un motore di join eterogeneo](../../odbc/reference/media/fig3-4.gif "fig3-4")  
  
 Questa architettura fornisce un'interfaccia comune per l'applicazione di accedere ai dati da database diversi. È possibile utilizzare una modalità comune per recuperare metadati, ad esempio informazioni sulle colonne speciali (identificatori di riga), e può chiamare funzioni di catalogo comuni per recuperare le informazioni di dizionario di dati. Chiamando la funzione ODBC **SQLStatistics**, ad esempio, l'applicazione può recuperare informazioni sugli indici su tabelle da unire, anche se le tabelle si trovano in due database separati. Query processor non necessario preoccuparsi di come i database di archiviano i metadati.  
  
 L'applicazione dispone inoltre dell'accesso standard per i tipi di dati. ODBC definisce tipi di dati SQL comuni mappati ai tipi di dati specifici del DBMS. Un'applicazione può chiamare **SQLGetTypeInfo** per recuperare le informazioni sui tipi di dati in database diversi.  
  
 Quando l'applicazione genera un'istruzione join eterogeneo, il processore di query in questa architettura consente di analizzare l'istruzione SQL e quindi genera istruzioni SQL separate per ogni database da unire. Utilizzando i metadati relativi a tutti i driver, query processor può determinare il join più efficiente e intelligente. Ad esempio, se l'istruzione join due tabelle in un database con una tabella in un altro database, query processor possibile unire le due tabelle in un database prima di unire il risultato con la tabella di altro database.  
  
## <a name="odbc-on-the-server"></a>ODBC nel Server  
 Driver ODBC possono essere installati in un server in modo che possono essere utilizzati dalle applicazioni in uno qualsiasi di una serie di computer client. In questa architettura (vedere la figura seguente), un Driver Manager e un singolo driver ODBC vengono installati in ogni client e un altro Driver Manager e una serie di driver ODBC installati nel server. In questo modo ogni accesso client a un'ampia gamma di driver utilizzate e gestite nel server.  
  
 ![Architettura dei driver ODBC in un server](../../odbc/reference/media/fig3-5.gif "FIG3 5")  
  
 Uno dei vantaggi di questa architettura è a configurazione e manutenzione efficiente del software. I driver devono essere aggiornati solo in un'unica posizione: nel server. Origini dati con origini dati di sistema, è possibile definire sul server da usare per tutti i client. Non è necessario definire le origini dati nel client. Il pool di connessioni consente di semplificare il processo mediante il quale i client si connettono a origini dati.  
  
 Il driver nel client è in genere un driver molto piccolo che trasferisce la chiamata di gestione Driver al server. Sua può essere notevolmente più piccolo rispetto ai driver ODBC completamente funzionanti nel server. In questa architettura, è possibile liberare risorse di client se il server dispone di maggiore potenza di elaborazione. Inoltre, è possibile migliorare l'efficienza e la sicurezza dell'intero sistema l'installazione di server di backup e di eseguire il bilanciamento del carico per ottimizzare l'utilizzo di server.
