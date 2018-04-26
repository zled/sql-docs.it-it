---
title: Creazione di Test case (SybaseToSQL) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-sybase
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Tester component,Test Case Wizard
ms.assetid: b52dfd93-95af-4299-bc8f-83f2a7a6a518
caps.latest.revision: 5
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8f844c2dcd2dfcbbe1b1096722fb65494e05fb55
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="creating-test-cases-sybasetosql"></a>Creazione di Test case (SybaseToSQL)
Utilizzare la procedura guidata di Test Case per creare un test. Questa procedura guidata consente di creare test case scegliendo testato e verificato gli oggetti e specificando i parametri di test.  
  
## <a name="starting-the-test-case-wizard"></a>Avvio della procedura guidata di Test Case  
Per avviare Creazione guidata Test Case **nuovo Test Case...** dal **Tester** menu.  
  
All'avvio, la procedura guidata Cerca database ssmatester2005db o ssmatester2008db (a seconda del tipo di progetto) nel server di Sybase di origine. È lo schema di estensione Tester utilizzato per archiviare gli oggetti ausiliari. Se la procedura guidata di Test Case non è possibile trovare ssmatester2005db o ssmatester2008db, verrà visualizzata una finestra di dialogo che si propone di creare il database di estensione Tester. (Questa situazione si verifica in genere durante la prima esecuzione di SSMA Tester)  
  
Se si ottiene la finestra di dialogo, fare clic su **Sì** per creare i database di Sybase tester nel server di origine. Una nuova finestra di dialogo verrà quindi visualizzati in cui è necessario aggiungere uno o più dispositivi in cui individuare di nuovo database Tester. Fare clic su **Aggiungi** per aggiungere un dispositivo. Nel **spazio di allocazione per Database Tester** finestra di dialogo selezionare il dispositivo e specificare le dimensioni utilizzata dal database di tester. Inoltre, è possibile impostare il dispositivo separato per i log di database. Si noti che è necessario disporre di privilegi per creare i database di Sybase.  
  
## <a name="overview-of-creating-test-cases-using-the-wizard"></a>Panoramica della creazione di Test case usando la procedura guidata  
Il processo di creazione di un test case è costituita da cinque passaggi:  
  
1.  [L'inizializzazione di Test case &#40;SybaseToSQL&#41;](../../ssma/sybase/initializing-test-cases-sybasetosql.md).  
  
2.  [La selezione e configurazione di oggetti di Test &#40;SybaseToSQL&#41;](../../ssma/sybase/selecting-and-configuring-objects-to-test-sybasetosql.md).  
  
3.  [La selezione e la configurazione di oggetti interessati &#40;SybaseToSQL&#41;](../../ssma/sybase/selecting-and-configuring-affected-objects-sybasetosql.md).  
  
4.  [Personalizzazione dell'ordine delle chiamate &#40;SybaseToSQL&#41;](../../ssma/sybase/customizing-calls-order-sybasetosql.md).  
  
5.  [Completamento della preparazione del Test Case &#40;SybaseToSQL&#41;](../../ssma/sybase/finishing-test-case-preparation-sybasetosql.md).  
  
## <a name="see-also"></a>Vedere anche  
[Test di eseguire la migrazione di oggetti di Database &#40;SybaseToSQL&#41;](../../ssma/sybase/testing-migrated-database-objects-sybasetosql.md)  
  
