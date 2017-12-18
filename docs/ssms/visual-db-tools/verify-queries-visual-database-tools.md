---
title: Verificare le query (Visual Database Tools) | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssms-visual-db
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vdtsql.chm:100644
helpviewer_keywords:
- verifying queries
- queries [SQL Server], verifying
- checking queries
ms.assetid: 1382c0c0-46dc-45f9-ab38-9bba1d347eea
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0353c23f4a47d8a4e432736e703b3115124bd7e2
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2017
---
# <a name="verify-queries-visual-database-tools"></a>Verifica delle query (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Per evitare problemi, è possibile verificare la correttezza della sintassi usata nella query compilata. Questa opzione si rivela particolarmente utile per l'inserimento delle istruzioni nel [riquadro SQL](../../ssms/visual-db-tools/sql-pane-visual-database-tools.md).  
  
In relazione alla verifica delle query, tenere presente quanto segue:  
  
-   Un'istruzione può essere valida, e dare esito positivo alla verifica, anche se non può essere rappresentata nel **riquadro Diagramma** e nel **riquadro Criteri**.  
  
-   Con la verifica SQL è possibile rilevare alcuni, ma non tutti gli errori SQL. Se una query contiene un errore non individuato durante la verifica SQL, questo verrà rilevato dal database al momento dell'esecuzione della query.  
  
-   Le query contenenti parametri non possono essere verificate.  
  
### <a name="to-verify-an-sql-statement"></a>Per verificare un'istruzione SQL  
  
-   Fare clic con il pulsante destro del mouse nel **riquadro SQL**e scegliere **Verifica sintassi SQL** dal menu di scelta rapida.  
  
## <a name="see-also"></a>Vedere anche  
[Esecuzione di query &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/run-queries-visual-database-tools.md)  
[Esecuzione di operazioni di base con le query &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
  
