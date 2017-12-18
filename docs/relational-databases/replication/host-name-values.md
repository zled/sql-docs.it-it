---
title: Valori HOST_NAME | Microsoft Docs
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.rep.newsubwizard.hostnamevalue.f1
ms.assetid: 21548f08-2910-4a55-baac-b911ba9afaf1
caps.latest.revision: "20"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: eaaf642dce054262d08b0b54025104d428e6f4b4
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="hostname-values"></a>Valori HOST_NAME
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Le pubblicazioni di tipo merge provviste di filtri con parametri usano la funzione SUSER_SNAME() e/o HOST_NAME() per filtrare i dati. La funzione viene specificata in Creazione guidata nuova pubblicazione oppure nella finestra di dialogo **Proprietà pubblicazione** .  
  
 Per impostazione predefinita, la funzione HOST_NAME() restituisce il nome del computer che esegue la connessione al server di pubblicazione. Se si utilizzano filtri con parametri, è possibile sostituire questo valore indicandone uno diverso in questa pagina della creazione guidata. La funzione HOST_NAME() restituisce quindi il valore specificato anziché il nome del computer. Per altre informazioni, vedere la sezione "Sostituzione del valore di HOST_NAME()" nell'argomento [Filtri di riga con parametri](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md).  
  
> [!NOTE]  
>  Se si sostituisce il valore HOST_NAME(), tutte le chiamate alla funzione HOST_NAME() restituiranno il valore specificato dall'utente. Verificare che il funzionamento di altre applicazioni non dipenda dal fatto che HOST_NAME() restituisca il nome del computer.  
  
## <a name="options"></a>Opzioni  
 **Proprietà sottoscrizione**  
 Consente di specificare un valore per ogni Sottoscrittore nella colonna **Valore Host_NAME** . In alternativa, è possibile accettare il valore predefinito, ovvero il nome del computer Sottoscrittore.  
  
## <a name="see-also"></a>Vedere anche  
 [Creare una sottoscrizione pull](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Visualizzare e modificare le proprietà delle sottoscrizioni pull](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)   
 [Visualizzare e modificare le proprietà delle sottoscrizioni push](../../relational-databases/replication/view-and-modify-push-subscription-properties.md)   
 [HOST_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/host-name-transact-sql.md)   
 [Sottoscrivere le pubblicazioni](../../relational-databases/replication/subscribe-to-publications.md)  
  
  
