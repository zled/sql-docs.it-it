---
title: La migrazione di account di accesso di SQL Server (dati della migrazione guidata) | Documenti Microsoft
ms.custom: ''
ms.date: 08/31/2017
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.suite: sql
ms.technology: dma
ms.tgt_pltfrm: ''
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, login migration
ms.assetid: ''
caps.latest.revision: ''
author: HJToland3
ms.author: jtoland
manager: craigg
ms.openlocfilehash: 23da8fe364ffad914013719f54871e85213befc5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32865456"
---
# <a name="migrating-sql-server-logins-using-data-migration-assistant"></a>Migrazione account di accesso di SQL Server utilizzando dati Migration Assistant

In questo articolo viene fornita una panoramica degli account di accesso di SQL Server la migrazione utilizzando dati Migration Assistant. 

## <a name="key-concepts"></a>Concetti chiave
Di seguito vengono definiti i concetti fondamentali.

- È possibile migrare gli account di accesso basato su un'entità di Windows (ad esempio, un utente di dominio o un gruppo di dominio di Windows). È anche possibile eseguire la migrazione di account di accesso creati in base sull'autenticazione, denominato anche gli account di accesso di SQL Server.

- Dati Migration Assistant attualmente non supporta gli account di accesso associato a un certificato di sicurezza autonomo (account di accesso mappato a certificato), una chiave asimmetrica autonoma (account di accesso mappato a una chiave asimmetrica) e gli account di accesso mappato alle credenziali.

- Dati della migrazione guidata non si sposta il **sa** principi di account di accesso e i server con nomi racchiusi tra due simboli di cancelletto (\#\#), che sono solo per uso interno.

- Per impostazione predefinita, Assistatn la migrazione di dati seleziona tutti gli account di accesso completo per eseguire la migrazione. Facoltativamente, è possibile selezionare un account di accesso specifici per eseguire la migrazione. Quando i dati della migrazione guidata esegue la migrazione di tutti gli account di accesso completo, il mapping di account di accesso utente rimane nel database che vengono eseguita la migrazione. 

  Se si prevede di eseguire la migrazione di account di accesso specifici, assicurarsi di selezionare gli account di accesso viene eseguito il mapping a uno o più utenti nei database selezionati per la migrazione.

- Come parte della migrazione di account di accesso, Data Migration Assistant inoltre consente di spostare i ruoli del server definito dall'utente e aggiunge le autorizzazioni a livello di server per i ruoli del server definito dall'utente. Il proprietario del ruolo verrà automaticamente impostato **sa** principale.

- Come parte della migrazione di account di accesso, Data Migration Assistant assegna le autorizzazioni per entità a protezione diretta sulla destinazione SQL Server in cui si trovano in SQL Server di origine. 

  Se l'account di accesso esiste già nella destinazione SQL Server, dati Migration Assistant viene eseguita la migrazione solo delle autorizzazioni assegnate all'entità a protezione diretta e non ricrea l'intero account di accesso.

- Dati Migration Assistant rende i tentativi di eseguire il mapping dell'account di accesso agli utenti del database se l'account di accesso esiste già nel server di destinazione.

- È consigliabile esaminare i risultati di migrazione per comprendere lo stato complessivo della migrazione di account di accesso e le azioni consigliate di post-migrazione.

## <a name="resources"></a>Risorse

[Data Migration Assistant (DMA)](../dma/dma-overview.md)

[Dati Migration Assistant: Le impostazioni di configurazione](../dma/dma-configurationsettings.md)
