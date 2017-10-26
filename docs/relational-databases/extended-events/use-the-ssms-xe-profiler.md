---
title: Usare il profiler XEvent di SQL Server Management Studio | Microsoft Docs
ms.custom: 
ms.date: 10/02/2016
ms.prod: sql-non-specified
ms.reviewer: genemi
ms.suite: 
ms.technology:
- database-engine
- xevents
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- extended events [SQL Server], system health session
- extended events [SQL Server], system_health session
- system_health session [SQL Server extended events]
- system health session [SQL Server extended events]
ms.assetid: 1e1fad43-d747-4775-ac0d-c50648e56d78
author: yualan
ms.author: alayu
manager: craigg
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 29122bdf543e82c1f429cf401b5fe1d8383515fc
ms.openlocfilehash: 3794c4ee749902e6d453053405cc155bc1bbac1a
ms.contentlocale: it-it
ms.lasthandoff: 10/10/2017

---
# <a name="use-the-ssms-xevent-profiler"></a>Usare il profiler XEvent di SQL Server Management Studio
Il profiler XEvent è una funzionalità di SQL Server Management Studio (SSMS) che apre una finestra del visualizzatore degli eventi estesi. Questa panoramica descrive i motivi di utilizzo del profiler, le funzionalità principali e le istruzioni per iniziare a visualizzare gli eventi estesi.

## <a name="why-would-i-use-the-xevent-profiler"></a>Perché usare il profiler XEvent?
A differenza del profiler SQL, il profiler XEvent è integrato direttamente in SSMS ed è basato sulla tecnologia degli eventi estesi del motore SQL. Questa funzionalità consente di accedere rapidamente a una vista streaming live degli eventi di diagnostica del server SQL. Questa vista può essere personalizzata e le personalizzazioni possono essere condivise con altri utenti di SQL Server Management Studio come file con estensione viewsettings. La sessione creata dal profiler XE è meno intrusiva per il server SQL in esecuzione rispetto a una traccia SQL analoga con l'uso del profiler SQL. Questa sessione può essere personalizzata anche dall'utente tramite l'interfaccia utente delle proprietà della sessione XE esistente o tramite TSQL.

## <a name="prerequisites"></a>Prerequisiti
Questa funzionalità è disponibile solo in SQL Server Management Studio (SSMS) v17.3 o versioni successive. Verificare che sia in uso la versione più recente. La versione più recente è disponibile [qui](https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms).

## <a id="getting-started"></a>Introduzione
Per accedere al profiler XEvent, seguire questa procedura:

1. Aprire **SQL Server Management Studio**.

2. Connettersi a un'istanza del motore di database di SQL Server o a localhost.

3. In Esplora oggetti individuare la voce di menu Profiler XE ed espanderla facendo clic sul segno '+'.

   ![Menu Profiler XE](media/xevents-xe-profiler-menu.png)

4. Fare doppio clic su **Standard** per visualizzare tutti gli eventi estesi nella sessione. Fare clic su **T-SQL** per visualizzare le istruzioni SQL. Se non è già stata creata, viene creata automaticamente una sessione.

   ![Sessione del profiler XE](media/xevents-xe-profiler-start-session.png)

5. È ora possibile visualizzare gli eventi estesi.

   ![Visualizzatore del profiler XE](media/xevents-xe-profiler-start-viewer.png)

## <a name="see-also"></a>Vedere anche
[Eventi estesi](../../relational-databases/extended-events/extended-events.md)  
[Strumenti degli eventi estesi](../../relational-databases/extended-events/extended-events-tools.md)  
  
  

