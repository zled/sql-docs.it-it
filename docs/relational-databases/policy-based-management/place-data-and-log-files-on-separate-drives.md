---
title: Posizionare dati e file di log in unità distinte | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: performance-monitor
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 6cbedc27-4d77-44ad-bed2-c23b628475a7
caps.latest.revision: 9
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 44af688bdeff93dac64d4225966e10c0e973ea14
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="place-data-and-log-files-on-separate-drives"></a>Posizionamento di dati e file di log in unità distinte
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Questa regola consente di controllare se i dati e i file di log si trovano in unità logiche distinte. Il posizionamento dei dati E dei file di log nello stesso dispositivo può provocare contesa nel dispositivo stesso, causando una riduzione delle prestazioni. Il posizionamento dei file in unità distinte fa sì che l'attività di I/O si verifichi contemporaneamente sia per i dati sia per i file di log.  
  
## <a name="recommendations"></a>Indicazioni  
 Quando si crea un nuovo database, specificare unità distinte per i dati e per i log. Per spostare i file una volta creato il database, è necessario che il database sia offline. Spostare i file usare uno dei metodi seguenti:  
  
> [!NOTE]  
>  Questi criteri non sono in grado di rilevare dispositivi fisici separati mediante punti di montaggio  
  
-   Ripristinare il database dal backup utilizzando l'istruzione RESTORE DATABASE con l'opzione WITH MOVE.  
  
-   Scollegare e quindi ricollegare il database specificando posizioni distinte per i dispositivi dei dati e dei log.  
  
-   Specificare una nuova posizione eseguendo l'istruzione ALTER DATABASE con l'opzione MODIFY FILE, riavviando quindi l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="for-more-information"></a>Ulteriori informazioni  
 [Spostare file del database](../../relational-databases/databases/move-database-files.md)  
  
 [Spostare database utente](../../relational-databases/databases/move-user-databases.md)  
  
 [Collegamento e scollegamento di un database &#40;SQL Server&#41;](../../relational-databases/databases/database-detach-and-attach-sql-server.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Monitorare e applicare le procedure consigliate tramite la gestione basata su criteri](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
