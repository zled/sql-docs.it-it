---
title: 'Lezione 1: Creare Account di archiviazione di Azure di Windows e contenitore | Documenti Microsoft'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: efdbd930-cde5-41b0-90ad-58a6cc68dddc
caps.latest.revision: 15
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9c4a2fb1db64456fe63bc814adda8278b253937a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36166965"
---
# <a name="lesson-1-create-windows-azure-storage-account-and-container"></a>Lezione 1: creare un contenitore e un account di Archiviazione di Windows Azure
  Prima di poter avviare l'archiviazione di file di dati di SQL Server nel servizio di archiviazione Windows Azure, è innanzitutto necessario creare un account del servizio di archiviazione Windows Azure con un contenitore BLOB e una firma di accesso condivisa. Nella lezione 1 vengono illustrati i passaggi per l'accesso al portale di gestione di Windows Azure e per la creazione di un account di archiviazione, di un contenitore BLOB e di una firma di accesso condivisa.  
  
 Per impostazione predefinita, solo il proprietario dell'account di archiviazione può accedere ai BLOB, alle tabelle e alle code dell'account in uso. Per accedere alle risorse utilizzando questa nuova funzionalità di SQL Server senza condividere la chiave di accesso dell'account di archiviazione, è necessario eseguire le seguenti operazioni:  
  
-   Impostare le autorizzazioni del contenitore su privato.  
  
-   Creare una firma di accesso condivisa. Consente di delegare l'accesso limitato alla risorsa di un contenitore, un BLOB, una tabella o una coda specificando l'intervallo in cui le risorse sono disponibili e le relative autorizzazioni del client.  
  
-   Utilizzare i criteri di accesso archiviati per gestire le firme di accesso condivise di un contenitore o dei relativi BLOB. I criteri di accesso archiviati costituiscono una misura di controllo aggiuntiva sulle firme di accesso condivise e forniscono strumenti semplici per revocarli.  
  
 Per altre informazioni, vedere [gestire l'accesso alle risorse di archiviazione Windows Azure](http://msdn.microsoft.com/library/windowsazure/ee393343.aspx).  
  
## <a name="create-storage-account"></a>Creare un account di archiviazione  
 Per creare un account di archiviazione nel portale di gestione di Windows Azure, effettuare i passaggi riportati di seguito:  
  
1.  Accedi per il [portale di gestione di Windows Azure](https://manage.windowsazure.com) utilizzando il proprio account. Se non si dispone di un account di Windows Azure, visitare [versione di valutazione gratuita di Windows Azure](http://www.windowsazure.com/pricing/free-trial/).  
  
     ![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-1.gif "SQL 14 CTP2")  
  
2.  Utilizzare le istruzioni dettagliate per [creare un account di archiviazione](http://azure.microsoft.com/documentation/articles/storage-create-storage-account/). Si noti che quando si crea un account di archiviazione da utilizzare con la funzionalità relativa ai file di dati di SQL Server in Windows Azure, è necessario deselezionare o disabilitare la replica a livello geografico. Ciò si richiede perché l'ordine di scrittura non è garantito quando più BLOB partecipano alla replica a livello geografico. Se un account di archiviazione viene sottoposto alla replica a livello geografico ed è necessario il recupero, si verifica un errore.  
  
     ![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-2.gif "SQL 14 CTP2")  
  
## <a name="create-a-blob-container"></a>Creare un contenitore BLOB  
 In Windows Azure, un contenitore fornisce un raggruppamento di un set di BLOB. Tutti i BLOB devono essere inclusi in un contenitore. Un account di archiviazione può contenere un numero illimitato di contenitori, tuttavia ne deve contenere almeno uno. In un contenitore è possibile archiviare un numero illimitato di BLOB. Per informazioni più aggiornate sui limiti di dimensioni di archiviazione, vedere [come utilizzare il servizio di archiviazione Blob di Windows Azure in .NET](http://www.windowsazure.com/develop/net/how-to-guides/blob-storage/).  
  
 Per creare un contenitore in Windows Azure, effettuare i passaggi riportati di seguito:  
  
1.  Accedi per il [portale di gestione Azure](https://manage.windowsazure.com).  
  
2.  Selezionare l'account di archiviazione, fare clic sui **contenitori** scheda e fare clic su **Aggiungi contenitore** nella parte inferiore dello schermo, che consente di aprire una nuova finestra di dialogo.  
  
3.  Immettere un nome per il contenitore.  
  
4.  Selezionare **privato** per **tipo di accesso**. Quando si imposta l'accesso su privato, i dati del contenitore e del BLOB possono essere letti solo dal proprietario dell'account di Windows Azure.  
  
     ![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-4.gif "SQL 14 CTP2")  
  
> [!NOTE]  
>  Per creare un contenitore a livello di programmazione è possibile utilizzare anche le API REST. Per altre informazioni, vedere [Create Container](http://msdn.microsoft.com/library/windowsazure/dd179468.aspx) nonché [riferimento all'API di Windows Azure Storage servizi REST](http://msdn.microsoft.com/library/windowsazure/dd179355.aspx).  
  
 **Lezione successiva:**  
  
 [Lezione 2. Creare un criterio di contenitore e generare una firma di accesso condiviso &#40;sa&#41; chiave](../relational-databases/lesson-1-create-stored-access-policy-and-shared-access-signature.md)  
  
  