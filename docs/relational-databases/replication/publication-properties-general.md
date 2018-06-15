---
title: Proprietà pubblicazione, Generale | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.rep.newpubwizard.pubproperties.general.f1
ms.assetid: 7912362f-c4d6-4f60-bd39-dee1f656ed18
caps.latest.revision: 25
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 31e04769dc8f7b6443a544505399c4f76ff6f43a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32961742"
---
# <a name="publication-properties-general"></a>Proprietà pubblicazione, Generale
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  La pagina **Generale** della finestra di dialogo **Proprietà pubblicazione** contiene informazioni di base sulla pubblicazione, tra cui il nome, la descrizione e i criteri di scadenza della sottoscrizione.  
  
## <a name="options"></a>Opzioni  
 **Nome**  
 Nome del database della pubblicazione (informazione di sola lettura).  
  
 **Database**  
 Nome del database di pubblicazione (informazione di sola lettura).  
  
 **Descrizione**  
 Descrizione della pubblicazione.  
  
 **Tipo**  
 Tipo di pubblicazione (informazione di sola lettura).  
  
 **Scadenza sottoscrizione**  
 Consente di selezionare una delle opzioni disponibili per la scadenza della sottoscrizione, ovvero **Le sottoscrizioni non hanno scadenza** oppure **Le sottoscrizioni scadono**, con un periodo di tempo esplicito (**Intervallo**).  
  
 Per le pubblicazioni snapshot e transazionali, [!INCLUDE[msCoName](../../includes/msconame-md.md)] consiglia di accettare l'impostazione predefinita **Le sottoscrizioni non hanno scadenza**.  
  
 Per la replica di tipo merge, [!INCLUDE[msCoName](../../includes/msconame-md.md)] consiglia di accettare l'impostazione predefinita **Le sottoscrizioni scadono** e di impostare il valore più basso possibile per **Intervallo**. Più è alto il valore del periodo di tempo di scadenza, maggiore è la quantità di metadati archiviati, con conseguenti possibili effetti negativi sulle prestazioni. Raggiungere un equilibrio tra la necessità di disconnettere i Sottoscrittori o semplicemente di non consentire ai Sottoscrittori di eseguire la sincronizzazione per un periodo di tempo esteso e i potenziali problemi di prestazioni derivanti dall'archiviazione e dall'elaborazione di grandi quantità di metadati.  
  
 Per altre informazioni, vedere [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md).  
  
 **Livello di compatibilità**  
 Solo per[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versioni successive. Solo per le pubblicazioni di tipo merge. Consente di selezionare la versione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] minima richiesta per i Sottoscrittori che eseguono la sincronizzazione con la pubblicazione. Il livello di compatibilità viene determinato da una serie di regole associate.  
  
## <a name="see-also"></a>Vedere anche  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Visualizzare e modificare le proprietà della pubblicazione](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Pubblicare dati e oggetti di database](../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  
