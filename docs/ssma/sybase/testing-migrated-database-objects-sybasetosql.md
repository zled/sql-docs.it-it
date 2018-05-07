---
title: Test di eseguire la migrazione di oggetti di Database (SybaseToSQL) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssma-sybase
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 4937f6b4-86bd-4070-88df-3d216306c33a
caps.latest.revision: 7
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 02cc2deb2721759f938ba8e0244f46b4464b86fa
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="testing-migrated-database-objects-sybasetosql"></a>Test di eseguire la migrazione di oggetti di Database (SybaseToSQL)
Microsoft SQL Server Migration Assistant per Sybase Tester (Tester SSMA) vengono testati automaticamente la conversione di oggetti di database e la migrazione dei dati apportate da SSMA. Al termine di tutti i passaggi di migrazione di SSMA, è possibile utilizzare il Tester di SSMA per verificare che gli oggetti convertiti funzionano nello stesso modo e che tutti i dati è stato trasferito correttamente.  
  
> [!NOTE]  
> Componente tester è disabilitata nel caso di connettività di Azure.  
  
È possibile verificare i seguenti tipi di oggetto con SSMA Tester:  
  
-   Tabelle  
  
-   Stored procedure  
  
-   Visualizzazioni.  
  
-   Istruzioni autonome.  
  
SSMA Tester esegue gli oggetti selezionati per il testing di Sybase e le relative controparti in SQL Server. Successivamente, confronta i risultati in base ai criteri seguenti:  
  
-   Le modifiche nei dati di tabella sono identiche?  
  
-   I valori dei parametri di output per le procedure e funzioni identiche?  
  
-   Le funzioni restituiscono gli stessi risultati?  
  
-   Sono che i set di risultati identici?  
  
> [!NOTE]  
> Attenzione. Non utilizzare mai SSMA Tester nei sistemi di produzione. Durante l'esecuzione di Tester lo schema di origine e i dati vengono modificati. Nel frattempo, il ripristino completo dello stato originale potrebbe essere impossibile per alcuni tipi di codice testato.  
  
## <a name="prerequisites"></a>Prerequisiti  
Se si desidera utilizzare SSMA Tester, installare SSMA Sybase estensione con la **installare Database Tester** opzione attivata.  
  
Inoltre, verificare quanto segue:  
  
-   Provider OLE DB per Sybase è installato nel computer in cui [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] viene eseguito.  
  
-   Integrazione con Common Language Runtime (CLR) è stato attivato il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] motore di Database.  
  
Si noti che la versione corrente di SSMA Tester non supporta l'esecuzione parallela da utenti diversi nello stesso server di origine o di destinazione.  
  
## <a name="getting-started"></a>Introduzione  
[Creazione di Test case &#40;SybaseToSQL&#41;](../../ssma/sybase/creating-test-cases-sybasetosql.md)  
  
## <a name="see-also"></a>Vedere anche  
[Installazione dei componenti di SSMA in SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md)  
[Le impostazioni del progetto &#40;conversione&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-conversion-sybasetosql.md)  
  
