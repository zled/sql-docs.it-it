---
title: 'Lezione 2: Valutare i criteri consigliate in base a una pianificazione | Documenti Microsoft'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 37ffad63-d6db-4609-8deb-786200659554
caps.latest.revision: 4
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cd4874e722c12813eb574d94c073cc069f72a4b6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36157043"
---
# <a name="lesson-2-evaluate-best-practices-policies-on-a-scheduled-basis"></a>Lezione 2: Valutazione di criteri per procedure consigliate in base a una pianificazione prestabilita
  È possibile configurare valutazioni pianificate di criteri per procedure consigliate in una o più istanze di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Per configurare i criteri per procedure consigliate da eseguire in base a una pianificazione prestabilita, è necessario importare i criteri nell'istanza di destinazione.  
  
 Per distribuire criteri pianificati in più server, è possibile importare i criteri in un'istanza, configurare le pianificazioni per tutti i criteri, esportare i criteri pianificati in una cartella, quindi distribuire i criteri pianificati nelle istanze di destinazione tramite Server registrati.  
  
> [!IMPORTANT]  
>  Le istanze di destinazione devono eseguire [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] o una versione successiva. Ai fini dell'automazione è necessario che i criteri siano archiviati localmente nell'istanza, operazione non supportata dalle versioni di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] precedenti a [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)].  
  
 In questa lezione verranno effettuate le operazioni seguenti:  
  
-   Importazione di criteri per procedure consigliate in un'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
-   Configurazione di criteri da eseguire in base a una pianificazione.  
  
-   Distribuzione di criteri per procedure consigliate pianificati in più istanze mediante Server registrati.  
  
 In questa lezione sono inclusi gli argomenti seguenti:  
  
-   [Importare i criteri in una singola istanza](../../2014/tutorials/import-the-policies-to-a-single-instance.md)  
  
-   [Pianificazione criteri](../../2014/tutorials/schedule-the-policies.md)  
  
-   [Distribuire criteri pianificati in più istanze](../../2014/tutorials/deploy-scheduled-policies-to-multiple-instances.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Amministrare più server tramite server di gestione centrale](../relational-databases/administer-multiple-servers-using-central-management-servers.md)  
  
  