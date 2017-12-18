---
title: Ordinare con ORDER BY (Visual Database Tools) | Microsoft Docs
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
helpviewer_keywords: ORDER BY clause [Visual Database Tools]
ms.assetid: 459f5640-8058-4c24-97e7-7bbd6168bc39
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3ecce7bc4a64a0fdbaf43120d348315b16b90888
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2017
---
# <a name="sort-with-order-by-visual-database-tools"></a>Ordinamento tramite la clausola ORDER BY (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Usando la clausola ORDER BY è possibile ordinare i risultati delle query in base a una o più colonne delle righe restituite. Per definire una clausola ORDER BY, scegliere le opzioni desiderate nel riquadro Criteri.  
  
### <a name="to-sort-a-query-using-an-order-by-clause"></a>Per ordinare una query utilizzando una clausola ORDER BY  
  
1.  Aprire una query esistente o crearne una nuova.  
  
2.  Nel [riquadro Criteri](../../ssms/visual-db-tools/criteria-pane-visual-database-tools.md)fare clic sulla colonna **Tipo di ordinamento** della riga corrispondente alla colonna da usare per ordinare i risultati della query.  
  
3.  Scegliere *Crescente* o *Decrescente* dall'elenco a discesa.  
  
> [!NOTE]  
> Se si deseleziona la voce **Tipo di ordinamento** per una colonna, la colonna verrà rimossa dalla clausola ORDER BY.  
  
Quando si utilizza il riquadro Criteri, la clausola UNION della query cambia in base alle azioni più recenti.  
  
> [!NOTE]  
> Per ordinare i risultati in base a più colonne, usare la colonna **Ordinamento** per specificare l'ordine in cui deve essere effettuata la ricerca nelle diverse colonne. Per altre informazioni, vedere **Procedura: Ordinare più colonne nelle query**.  
  
## <a name="see-also"></a>Vedere anche  
[Ordinare e raggruppare i risultati delle query &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/sort-and-group-query-results-visual-database-tools.md)  
[Creare un riepilogo dei risultati di query &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/summarize-query-results-visual-database-tools.md)  
[Procedure per la progettazione di query e viste &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
