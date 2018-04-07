---
title: Impostare la Password di account di accesso amministratore nodi Active Directory in modalità ripristino servizi di Directory (AP)
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.technology: mpp-data-warehouse
ms.custom: ''
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 97a9c715-2763-417d-b45c-bb0180759e47
caps.latest.revision: 20
ms.openlocfilehash: 3e09305152a2892ae4acaf7096921d2a73345b63
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2018
---
# <a name="set-admin-password-for-logging-on-to-ad-nodes-in-directory-services-restore-mode-dsrm"></a>Impostare le Password di amministratore per accedere a nodi di Active Directory in modalità ripristino servizi di Directory (DSRM)
Modalità ripristino servizi directory (DSRM) è una modalità di avvio per il ripristino o il ripristino di servizi di dominio Active Directory (AD DS). Consente di accedere ai nodi del dispositivo AD dopo di dominio Active Directory non è riuscita o quando servizi di dominio Active Directory deve essere ripristinato. La password per la modalità ripristino servizi directory è stata inizializzata durante l'installazione dello strumento presso il fornitore dell'hardware e debba essere modificata dall'amministratore del dispositivo. Sistema della piattaforma Analitica ha due AD DS (controller di dominio). ***appliance_domain *-AD01** e ***appliance_domain *-AD02**. Per ogni nodo di dispositivo Active Directory, modificare la password modalità ripristino servizi directory utilizzando la procedura seguente.  
  
## <a name="HowToDSRM"></a>Per reimpostare la password dell'amministratore  
  
1.  Aprire una finestra del prompt dei comandi su un nodo di dispositivo Active ***appliance_domain*– AD*xx***macchina virtuale.  
  
2.  Al prompt dei comandi, digitare `ntdsutil`.  
  
3.  Nel **ntdsutil** digitare `set dsrm password`.  
  
4.  Nel **Reimposta Password amministratore:** digitare `reset password on server null`.  
  
5.  Al prompt, digitare la nuova password.  
  
6.  Ripetere i passaggi 1-5 per ogni macchina virtuale accessorio Active Directory.  
  
    > [!WARNING]  
    > Sistema della piattaforma Analitica non supporta il carattere di segno di dollaro ($) in cui l'amministratore di dominio o una password di amministratore locale. Una password contenente un segno di dollaro verrà convalidare e utilizzabile ma è possibile bloccare le attività di aggiornamento e manutenzione.  
  
> [!NOTE]  
> Se la macchina virtuale o servizi di dominio Active Directory danneggiata per una macchina virtuale di Active Directory specifica, in esecuzione **ReplaceVM** per l'annuncio interessato macchina virtuale è l'azione correttiva consigliata. Contatto CSS per assistenza.  
  
## <a name="see-also"></a>Vedere anche  
[La reimpostazione della password &#40;Analitica Platform System&#41;](password-reset.md)  
  
