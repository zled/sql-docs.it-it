---
title: includere file
description: includere file
services: sql-database
author: MightyPen
ms.service: sql-database
ms.topic: include
ms.date: 04/05/2018
ms.author: genemi
ms.custom: include file
ms.openlocfilehash: 842a7377bcd6bdcb649a78b2f31eb66de95bc5a3
ms.sourcegitcommit: a98ed7872afc055c65aa9697d571f8b300f6eeb4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/21/2018
ms.locfileid: "36313397"
---
## <a name="specifying-application-intent"></a>Specificazione della finalità dell'applicazione

La parola chiave **ApplicationIntent** può essere specificato nella stringa di connessione. Sono valori assegnabili **ReadWrite** oppure **ReadOnly**. Il valore predefinito è **ReadWrite**.

Quando si **ApplicationIntent = ReadOnly**, il client richieda un carico di lavoro di lettura durante la connessione. Il server applica la finalità al momento della connessione e durante un **uso** istruzione di database.

Il **ApplicationIntent** (parola chiave) non funziona con i database legacy di sola lettura.  


#### <a name="targets-of-readonly"></a>Destinazioni di sola lettura

Quando una connessione sceglie **ReadOnly**, la connessione viene assegnata a una delle seguenti configurazioni speciali che potrebbero essere disponibili per il database:

- [Always On](~/database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)
    - Un database è possibile consentire o negare carichi di lavoro di lettura sul database di AlwaysOn destinazione. Questa scelta è controllata tramite il **ALLOW_CONNECTIONS** clausola del **PRIMARY_ROLE** e **SECONDARY_ROLE** istruzioni Transact-SQL.

- [Replica geografica](https://docs.microsoft.com/azure/sql-database/sql-database-geo-replication-overview)

- [Leggere con scalabilità orizzontale](https://docs.microsoft.com/azure/sql-database/sql-database-read-scale-out)

Se nessuna di tali destinazioni speciale è disponibile, il database normale viene letto dal.

&nbsp;

Il **ApplicationIntent** parola chiave consente *routing di sola lettura*.


## <a name="read-only-routing"></a>Routing di sola lettura

Il routing di sola lettura è una funzionalità che può garantire la disponibilità di una replica di sola lettura di un database. Per abilitare il routing di sola lettura, tutte le condizioni seguenti:

- È necessario connettersi a un listener del gruppo di disponibilità Always On.

- La parola chiave della stringa di connessione **ApplicationIntent** deve essere impostata su **ReadOnly**.

- Il gruppo di disponibilità deve essere configurato dall'amministratore del database per abilitare il routing di sola lettura.

Più connessioni tramite routing di sola lettura potrebbe non connettersi a tutte la stessa replica di sola lettura. Le modifiche nella sincronizzazione del database o nella configurazione di routing del server possono comportare connessioni client a repliche di sola lettura diverse. È possibile garantire che tutte le richieste di sola lettura di connettersi alla stessa replica di sola lettura. Verificare l'uguaglianza dal *non* passando un listener del gruppo di disponibilità per il **Server** parola chiave di stringa di connessione. Specificare invece il nome dell'istanza di sola lettura.

Routing di sola lettura può richiedere più tempo rispetto alla connessione al database primario. Il tempo di attesa, infatti, sola lettura di routing si connette al database primario e quindi cerca il migliore secondario leggibile disponibile. A causa di questi staps più, è necessario aumentare il timeout di accesso per almeno 30 secondi.

