---
title: Valori HOST_NAME | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.newsubwizard.hostnamevalue.f1
ms.assetid: 21548f08-2910-4a55-baac-b911ba9afaf1
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 62aabb81bed2b7c887f2aa5ec39073550809e42a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47637775"
---
# <a name="hostname-values"></a>Valori HOST_NAME
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Le pubblicazioni di tipo merge provviste di filtri con parametri utilizzano la funzione SUSER_SNAME() e/o HOST_NAME() per filtrare i dati. La funzione viene specificata in Creazione guidata nuova pubblicazione oppure nella finestra di dialogo **Proprietà pubblicazione** .  
  
 Per impostazione predefinita, la funzione HOST_NAME() restituisce il nome del computer che esegue la connessione al server di pubblicazione. Se si utilizzano filtri con parametri, è possibile sostituire questo valore indicandone uno diverso in questa pagina della creazione guidata. La funzione HOST_NAME() restituisce quindi il valore specificato anziché il nome del computer. Per altre informazioni, vedere la sezione "Sostituzione del valore di HOST_NAME()" nell'argomento [Filtri di riga con parametri](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md).  
  
> [!NOTE]  
>  Se si sostituisce il valore HOST_NAME(), tutte le chiamate alla funzione HOST_NAME() restituiranno il valore specificato dall'utente. Verificare che il funzionamento di altre applicazioni non dipenda dal fatto che HOST_NAME() restituisca il nome del computer.  
  
## <a name="options"></a>Opzioni  
 **Proprietà sottoscrizione**  
 Consente di specificare un valore per ogni Sottoscrittore nella colonna **Valore Host_NAME** . In alternativa, è possibile accettare il valore predefinito, ovvero il nome del computer Sottoscrittore.  
  
## <a name="see-also"></a>Vedere anche  
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Visualizzare e modificare le proprietà delle sottoscrizioni pull](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)   
 [Visualizzare e modificare le proprietà delle sottoscrizioni push](../../relational-databases/replication/view-and-modify-push-subscription-properties.md)   
 [HOST_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/host-name-transact-sql.md)   
 [Sottoscrizione delle pubblicazioni](../../relational-databases/replication/subscribe-to-publications.md)  
  
  
