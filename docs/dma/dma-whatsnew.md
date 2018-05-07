---
title: Novità di Data Migration Assistant (SQL Server) | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2018
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.suite: sql
ms.technology: dma
ms.tgt_pltfrm: ''
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, new features
ms.assetid: ''
caps.latest.revision: ''
author: HJToland3
ms.author: jtoland
manager: craigg
ms.openlocfilehash: 2468bb700588310a397530f27c6c6d6960e75b06
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="whats-new-in-data-migration-assistant"></a>Novità di Data Migration Assistant

Questo argomento elenca le aggiunte in ogni versione di dati della migrazione guidata (DMA).

## <a name="dma-v34"></a>V3.4 DMA
La versione di v3.4 di DMA include le seguenti aggiunte:
- Supporto per SQL Server 2017 come origine per le migrazioni a Database SQL di Azure.
- Miglioramenti alla stabilità, prestazioni e valutazione correttezza di regola.

## <a name="dma-v33"></a>3.3 DMA
La versione 3.3 di DMA consente la migrazione di un'istanza di SQL Server locale per la nuova versione di SQL Server 2017, su Windows e Linux. Mentre il flusso di lavoro globale migrazione per Windows e Linux è lo stesso, lo spostamento 2017 di SQL Server per Linux richiede alcune considerazioni aggiuntive.

### <a name="specifying-the-back-up-path"></a>Specifica il percorso di backup
Linux e Windows utilizzano formati di percorso diversi. Di conseguenza, la migrazione a SQL Server 2017 in Linux, è necessario che l'utente fornisce le versioni di Windows e Linux di percorso del file fisico. Questa operazione viene eseguita in modi diversi a seconda della posizione del file fisico.
Se il file di backup fisico è in un computer che esegue:
- Linux, usare un 'samba' condivide per condividere il file con altri computer nella rete.
-   Windows, utilizzare il comando 'EID' per montare la condivisione al computer che eseguono Linux.

> [!NOTE]
> Informazioni dettagliate sull'utilizzo di una condivisione 'samba' o il comando 'EID' non rientrano nell'ambito di questo articolo.

### <a name="migrating-windows-logins"></a>La migrazione degli account di accesso di Windows
Durante la migrazione degli account di accesso Active Directory (AD) è ufficialmente supportata da SQL Server 2017 in Linux, richiede un'ulteriore configurazione per funzionare correttamente. Vedere l'argomento [l'autenticazione di Active Directory con SQL Server in Linux](https://docs.microsoft.com/en-us/sql/linux/sql-server-linux-active-directory-authentication) per informazioni dettagliate sulla configurazione di account di accesso di Active Directory in SQL Server 2017 in Linux. Al termine dell'installazione, è possibile eseguire la migrazione degli account di accesso di Active Directory come di consueto. L'autenticazione di SQL standard funziona come previsto senza eventuali impostazioni aggiuntive.

## <a name="dma-v32"></a>V 3.2 DMA
La versione v 3.2 di DMA include le seguenti aggiunte:

- Migrazione di schemi e dati sono abilitati dai database di SQL Server locale al Database SQL Azure con un nuovo flusso di lavoro di migrazione.

- Durante la migrazione dello schema per Database SQL di Azure, DMA generare script per oggetti di database di origine, vengono fornite indicazioni su come risolvere eventuali problemi di compatibilità e quindi distribuisce lo schema in Azure.

## <a name="dma-v31"></a>V 3.1 DMA
La versione v 3.1 di DMA include le seguenti aggiunte:

- Valutazione migliorata consigli per i database SQL di Azure in termini di regole di confronto del database, l'uso di non supportate stored procedure di sistema e gli oggetti CLR.

- Guida di valutazione per i livelli di compatibilità 130, 120, 110 e 100 durante la migrazione a database SQL di Azure.

## <a name="dma-v30"></a>V 3.0 DMA
La versione 3.0 di DMA estende la valutazione di database SQL di Azure per fornire indicazioni complete per aiutare a risolvere i problemi relativi a:

- Problemi di blocco di migrazione.

- Parzialmente o non supportato di funzioni e funzionalità.

## <a name="dma-v21"></a>V 2.1 DMA
La versione 2.1 di DMA include le seguenti aggiunte:
- Supporto della riga di comando per eseguire valutazioni in modalità automatica, che consente di eseguire valutazioni su larga scala. Per ulteriori dettagli, vedere l'argomento [eseguire Data Migration Assistant dalla riga di comando](dma-commandline.md).

- Miglioramenti delle prestazioni quando gli utenti di avviano e chiudere DMA.

- La possibilità di configurare il timeout della connessione SQL. Per ulteriori dettagli, vedere l'argomento [impostazioni di configurazione per dati Migration Assistant](dma-configurationsettings.md).

## <a name="dma-v20"></a>V 2.0 DMA
La versione 2.0 di DMA include migliorate indicazioni di funzionalità di database di estensione per fornire le tabelle con priorità appropriate che ottimizzano il risparmio di spazio di archiviazione.

## <a name="dma-v10"></a>DMA v1.0
La versione 1.0 di DMA è la versione iniziale, e consente di:
- Individuazione dei problemi che possono influire sull'aggiornamento a una versione locale di SQL Server. Le conclusioni sono descritte come problemi di compatibilità e la classificazione nelle aree seguenti:
    -   Modifiche di rilievo
    - Modifiche del comportamento
    - Funzionalità deprecate

- Individuazione di nuove funzionalità della piattaforma di SQL Server di destinazione che il database può trarre vantaggio da un aggiornamento. Le conclusioni sono descritte come indicazioni di funzionalità e la classificazione nelle aree seguenti:
    - restazioni
    - Sicurezza
    - Archiviazione

-   Esperienza utente moderna per eseguire valutazioni.

## <a name="see-also"></a>Vedere anche

[Panoramica dell'Assistente per la migrazione di dati](../dma/dma-overview.md)
