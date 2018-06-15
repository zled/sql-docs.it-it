---
title: Impostare la password di Active Directory - Analitica Platform System | Documenti Microsoft
description: Impostare password di accesso amministratore di Active Directory i nodi in modalità ripristino servizi Directory in Analitica Platform System (AP).
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: e74689216c1485fc0c11c588acb151269e2b5d2b
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
ms.locfileid: "31538381"
---
# <a name="set-admin-password-for-logging-on-to-ad-nodes-in-directory-services-restore-mode-dsrm---analytics-platform-system"></a>Impostare la Password di amministratore per accedendovi nodi di Active Directory in servizi di Directory ripristinare la modalità (DSRM) - Analitica Platform System
Modalità ripristino servizi directory (DSRM) è una modalità di avvio per il ripristino o il ripristino di servizi di dominio Active Directory (AD DS). Consente di accedere ai nodi del dispositivo AD dopo di dominio Active Directory non è riuscita o quando servizi di dominio Active Directory deve essere ripristinato. La password per la modalità ripristino servizi directory è stata inizializzata durante l'installazione dello strumento presso il fornitore dell'hardware e debba essere modificata dall'amministratore del dispositivo. Sistema della piattaforma Analitica ha due AD DS (controller di dominio). ***appliance_domain *-AD01** e ***appliance_domain *-AD02**. Per ogni nodo di dispositivo Active Directory, modificare la password modalità ripristino servizi directory utilizzando la procedura seguente.  
  
## <a name="HowToDSRM"></a>Per reimpostare la password dell'amministratore  
  
1.  Aprire una finestra del prompt dei comandi su un nodo di dispositivo Active ***appliance_domain *– AD*xx***macchina virtuale.  
  
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
  
