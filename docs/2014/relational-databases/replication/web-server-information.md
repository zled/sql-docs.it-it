---
title: Informazioni server Web | Microsoft Docs
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
- sql12.rep.newsubwizard.webserverinformation.f1
ms.assetid: 86d72275-45c7-459f-98cf-f5a366ed279c
caps.latest.revision: 18
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: c40a9e43e15e948f816379ee751de7ad529a67dd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36166602"
---
# <a name="web-server-information"></a>Informazioni server Web
  Le informazioni sul server Web sono necessarie per l'utilizzo dell'opzione relativa alla sincronizzazione Web per la replica di tipo merge. Per informazioni sulla configurazione della sincronizzazione Web, vedere [Configurare la sincronizzazione Web](configure-web-synchronization.md).  
  
## <a name="options"></a>Opzioni  
 **Indirizzo server Web**  
 Se si è specificato l'indirizzo di un server Web nella pagina **Snapshot FTP e Internet** della finestra di dialogo **Proprietà pubblicazione**, tale indirizzo viene visualizzato in questa casella di testo per impostazione predefinita. È possibile accettare l'impostazione predefinita oppure immettere l'indirizzo di un server Web completo per il server [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Information Services (IIS) che esegue la sincronizzazione della sottoscrizione.  
  
 **Indicare la modalità di connessione di ogni Sottoscrittore al server Web**  
 Consente di specificare il tipo di autenticazione utilizzato per la connessione al server Web. È consigliabile utilizzare l'autenticazione di base per le connessioni al server IIS realizzate in combinazione con SSL (Secure Sockets Layer). Se si seleziona l'autenticazione di base, immettere l'account e la password che verranno utilizzati per la connessione dal Sottoscrittore al server IIS.  
  
## <a name="see-also"></a>Vedere anche  
 [Create a Pull Subscription](create-a-pull-subscription.md)   
 [Visualizzare e modificare le proprietà delle sottoscrizioni pull](view-and-modify-pull-subscription-properties.md)   
 [Sottoscrittori non SQL Server](non-sql/non-sql-server-subscribers.md)   
 [Subscribe to Publications](subscribe-to-publications.md)   
 [Sincronizzazione Web per la replica di tipo merge](web-synchronization-for-merge-replication.md)  
  
  