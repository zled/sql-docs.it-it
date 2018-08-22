---
title: Test di eseguire la migrazione di oggetti di Database (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
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
ms.openlocfilehash: ac7654f43f2d453ad0e55a0a7ebcfee79ac2c91c
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/14/2018
ms.locfileid: "40394038"
---
# <a name="testing-migrated-database-objects-sybasetosql"></a>Test di oggetti di database migrati (SybaseToSQL)
Microsoft SQL Server Migration Assistant per Sybase Tester (SSMA Tester) vengono testati automaticamente la conversione di oggetti di database e la migrazione dei dati apportate da SSMA. Al termine di tutti i passaggi di migrazione di SSMA, utilizzare il Tester di SSMA per verificare che gli oggetti convertiti funzionano allo stesso modo e che tutti i dati è stato trasferito correttamente.  
  
> [!NOTE]  
> Componente tester è disabilitato in caso di connettività di Azure.  
  
È possibile testare i seguenti tipi di oggetto con SSMA Tester:  
  
-   Tabelle  
  
-   Stored procedure  
  
-   Visualizzazioni.  
  
-   Istruzioni autonome.  
  
SSMA Tester esegue gli oggetti selezionati per il testing in Sybase e le relative controparti in SQL Server. Successivamente, confronta i risultati in base ai criteri seguenti:  
  
-   Le modifiche nei dati di tabella sono identici?  
  
-   Sono i valori dei parametri di output per le procedure e le funzioni identiche?  
  
-   Le funzioni restituiscono gli stessi risultati?  
  
-   Sono che i set di risultati identici?  
  
> [!NOTE]  
> Attenzione! Non utilizzare mai SSMA Tester nei sistemi di produzione. Durante l'esecuzione di Tester lo schema di origine e i dati vengono modificati. Nel frattempo, al ripristino completo dello stato originale potrebbe essere impossibile per alcuni tipi di codice testato.  
  
## <a name="prerequisites"></a>Prerequisiti  
Se si desidera utilizzare Tester SSMA, installare SSMA Sybase Extension Pack con le **installare Database Tester** opzione impostata su on.  
  
Inoltre, verificare quanto segue:  
  
-   Provider OLE DB per Sybase è installato nel computer in cui [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene eseguito.  
  
-   Integrazione con Common Language Runtime (CLR) è stato attivato il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] motore di Database.  
  
Si noti che la versione corrente di SSMA Tester non supporta l'esecuzione parallela da utenti diversi nello stesso server di origine o destinazione.  
  
## <a name="getting-started"></a>Introduzione  
[Creazione di Test case &#40;SybaseToSQL&#41;](../../ssma/sybase/creating-test-cases-sybasetosql.md)  
  
## <a name="see-also"></a>Vedere anche  
[Installazione di componenti SSMA in SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md)  
[Le impostazioni di progetto &#40;conversione&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-conversion-sybasetosql.md)  
  
