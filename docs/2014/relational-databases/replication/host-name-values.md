---
title: Valori HOST_NAME | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.rep.newsubwizard.hostnamevalue.f1
ms.assetid: 21548f08-2910-4a55-baac-b911ba9afaf1
caps.latest.revision: 19
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: ad7fb0521406a7b3befe0667c16d000d7c750823
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36156674"
---
# <a name="hostname-values"></a>Valori HOST_NAME
  Le pubblicazioni di tipo merge provviste di filtri con parametri utilizzano la funzione SUSER_SNAME() e/o HOST_NAME() per filtrare i dati. La funzione viene specificata in Creazione guidata nuova pubblicazione oppure nella finestra di dialogo **Proprietà pubblicazione** .  
  
 Per impostazione predefinita, la funzione HOST_NAME() restituisce il nome del computer che esegue la connessione al server di pubblicazione. Se si utilizzano filtri con parametri, è possibile sostituire questo valore indicandone uno diverso in questa pagina della creazione guidata. La funzione HOST_NAME() restituisce quindi il valore specificato anziché il nome del computer. Per altre informazioni, vedere la sezione "Sostituzione del valore di HOST_NAME()" nell'argomento [Filtri di riga con parametri](merge/parameterized-filters-parameterized-row-filters.md).  
  
> [!NOTE]  
>  Se si sostituisce il valore HOST_NAME(), tutte le chiamate alla funzione HOST_NAME() restituiranno il valore specificato dall'utente. Verificare che il funzionamento di altre applicazioni non dipenda dal fatto che HOST_NAME() restituisca il nome del computer.  
  
## <a name="options"></a>Opzioni  
 **Proprietà sottoscrizione**  
 Consente di specificare un valore per ogni Sottoscrittore nella colonna **Valore Host_NAME** . In alternativa, è possibile accettare il valore predefinito, ovvero il nome del computer Sottoscrittore.  
  
## <a name="see-also"></a>Vedere anche  
 [Create a Pull Subscription](create-a-pull-subscription.md)   
 [Create a Push Subscription](create-a-push-subscription.md)   
 [Visualizzare e modificare le proprietà delle sottoscrizioni pull](view-and-modify-pull-subscription-properties.md)   
 [Visualizzare e modificare le proprietà delle sottoscrizioni push](view-and-modify-push-subscription-properties.md)   
 [HOST_NAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/host-name-transact-sql)   
 [Sottoscrizione delle pubblicazioni](subscribe-to-publications.md)  
  
  
