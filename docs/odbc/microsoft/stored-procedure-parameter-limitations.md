---
title: Stored Procedure parametro limitazioni | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- stored procedures [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], stored procedures
ms.assetid: 8b804bcf-4cce-4e6f-aa45-00bab9ef9921
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 59beb012675e3f6af8e1aef65fe2905d353e31ab
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="stored-procedure-parameter-limitations"></a>Limitazioni di parametro di stored Procedure
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. In alternativa, utilizzare il driver ODBC fornito da Oracle.  
  
 Quando si esegue Oracle stored procedure che utilizzano 10 o più parametri di output, la chiamata della stored procedure, verrà prodotto un errore di violazione di accesso o gli oggetti ADO (ActiveX Data). Ciò può verificarsi quando si utilizza il Driver ODBC di Microsoft per Oracle con le versioni 8.0.4.0.0 e 8.0.4.0.4 del software client Oracle.  
  
 Per risolvere il problema, il software client Oracle deve essere aggiornato alla versione 8.0.4.2.0 o versione successiva. Contatto Oracle Corporation per ulteriori informazioni sul [patch](../../odbc/microsoft/oracle-software-patches.md).  
  
> [!NOTE]  
>  Questo problema si verifica con la versione del software client Oracle versione 8.0.3.0.0 anticipata.

