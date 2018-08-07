---
title: Tipo di sottoscrizione | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.rep.newsubwizard.subscriptiontype.f1
ms.assetid: 9a50f588-ee45-4a87-826f-372ff0798587
caps.latest.revision: 20
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: fc7416a12971d29c495293213e3f7c0180954dd7
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/06/2018
ms.locfileid: "39545261"
---
# <a name="subscription-type"></a>Tipo di sottoscrizione
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  La replica di tipo merge offre due tipi di sottoscrizioni, ovvero server e client, definiti rispettivamente come globale e locale nelle versioni precedenti di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ). I Sottoscrittori con una sottoscrizione di tipo server sono in grado di:  
  
-   Ripubblicare i dati di altri Sottoscrittori.  
  
-   Fungere da partner di sottoscrizione alternativi.  
  
-   Risolvere conflitti in base alla priorità impostata.  
  
 La maggior parte dei Sottoscrittori non necessita di questa funzionalità ed è in grado di utilizzare una sottoscrizione client. Le sottoscrizioni client consentono ancora il rilevamento e la risoluzione dei conflitti, ma ai Sottoscrittori non viene assegnata una priorità. In altre parole, il primo Sottoscrittore che inoltra una modifica al server di pubblicazione prevale nei conflitti eventualmente generati da tale modifica.  
  
> [!NOTE]  
>  Dopo aver creato la sottoscrizione non è possibile modificarne il tipo.  
  
## <a name="options"></a>Opzioni  
 **Proprietà sottoscrizione**  
 Per ogni Sottoscrittore, selezionare **Client** o **Server** nell'elenco a discesa nella colonna **Tipo di sottoscrizione** . Per i Sottoscrittori con sottoscrizioni server, immettere un numero compreso tra 0 e 99,99 nella colonna **Priorità per la risoluzione dei conflitti** . Maggiore è questo numero, più alta è la priorità per il Sottoscrittore.  
  
## <a name="see-also"></a>Vedere anche  
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Sottoscrizione delle pubblicazioni](../../relational-databases/replication/subscribe-to-publications.md)  
  
  
