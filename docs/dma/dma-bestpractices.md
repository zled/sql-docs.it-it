---
title: Procedure consigliate per la Data Migration Assistant (SQL Server) | Documenti Microsoft
ms.custom: 
ms.date: 10/04/2017
ms.prod: sql-non-specified
ms.prod_service: dma
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: sql
ms.technology: sql-dma
ms.tgt_pltfrm: 
ms.topic: article
keywords: 
helpviewer_keywords: Data Migration Assistant, Best Practices
ms.assetid: 
caps.latest.revision: 
author: HJToland3
ms.author: jtoland
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f8842ca064494bc7ead99eb34d6ea2cc76bb2679
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="best-practices-for-running-data-migration-assistant"></a>Procedure consigliate per l'esecuzione di Assistente per la migrazione dei dati
Questo articolo fornisce le seguenti informazioni sulle procedure consigliate per l'installazione, valutazione e la migrazione.

## <a name="installation"></a>Installazione

Non installare ed eseguire Data Migration Assistant direttamente sul computer host di SQL Server.

## <a name="assessment"></a>Valutazione

- Eseguire valutazioni su database di produzione durante le ore non di punta.

- Eseguire il **problemi di compatibilità** e **nuove raccomandazioni funzionalità** valutazioni separatamente per ridurre la durata di valutazione.

## <a name="migration"></a>Migrazione

- Eseguire la migrazione di un server durante le ore non di punta.

- Durante la migrazione di un database, fornire un percorso di condivisione singolo accessibile dal server di origine e destinazione e, se possibile, evitare un'operazione di copia. Un'operazione di copia potrebbe introdurre ritardo in base alla dimensione del file di backup. L'operazione di copia aumenta inoltre la possibilità di una migrazione non riuscito a causa di un passaggio aggiuntivo. Quando viene fornita un'unica posizione, dati di migrazione guidata consente di ignorare l'operazione di copia.
 
    Inoltre assicurarsi che per fornire le autorizzazioni corrette per la cartella condivisa per evitare errori durante la migrazione. Le autorizzazioni corrette vengono specificate nello strumento. Se un'istanza di SQL Server viene eseguito con credenziali del servizio di rete, assegnare le autorizzazioni corrette per la cartella condivisa per l'account del computer per l'istanza di SQL Server.

- Abilitare la crittografia connessione durante la connessione al server di origine e destinazione. L'utilizzo di SSL crittografia aumenta la sicurezza dei dati trasmessi attraverso la rete tra Data Migration Assistant e l'istanza di SQL Server. Questo è utile soprattutto quando la migrazione di account di accesso SQL. Se non viene utilizzata la crittografia SSL e la rete è compromessa da un utente malintenzionato, gli account di accesso SQL viene eseguita la migrazione a potrebbero ottenere intercettati e/o modificare il volo dall'autore dell'attacco.

    Tuttavia, se tutti accedono attraverso una configurazione di Intranet sicura, la crittografia potrebbe non essere necessaria. L'abilitazione della crittografia determina un rallentamento delle prestazioni in seguito a aggiuntivo overhead necessario per crittografare e decrittografare i pacchetti. Per ulteriori informazioni, consultare [crittografia delle connessioni a SQL Server](https://go.microsoft.com/fwlink/?linkid=832513).
