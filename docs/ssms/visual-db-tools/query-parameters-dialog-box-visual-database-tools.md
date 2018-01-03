---
title: Finestra di dialogo Parametri query (Visual Database Tools) | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-visual-db
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vdtsql.chm:69645
- vdt.dlgbox.definequeryparameters
ms.assetid: 31cdaee2-d7cd-4d64-a45f-924b27e8b1f0
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7ea119f11de0cc4adec8d3239b17cb528b7408c1
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="query-parameters-dialog-box-visual-database-tools"></a>Finestra di dialogo Parametri query (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Questa finestra di dialogo consente di immettere valori per i parametri definiti nella query. Viene visualizzata quando si esegue una query contenente parametri che richiedono la presenza dell'utente finale in fase di esecuzione.  
  
## <a name="options"></a>Opzioni  
**Nome**  
Elenca i parametri definiti per la query eseguita. Se la query contiene parametri denominati, i nomi vengono visualizzati nell'elenco. Se nella query sono contenuti parametri senza nome, per ogni parametro della query verranno elencati i nomi di parametro definiti dal sistema.  
  
**Value**  
Immettere il valore per ogni parametro elencato in **Nome**. Il valore utilizzato per ultimo viene visualizzato come valore del parametro predefinito.  
  
## <a name="example"></a>Esempio  
La query del riquadro SQL riportata di seguito consente di aprire la finestra di dialogo Parametri query quando viene eseguita nel database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject_md.md)] .  
  
```  
SELECT   FirstName, LastName  
FROM    Person.Person AS Lastname  
WHERE   (LastName = @Param1);  
```  
  
## <a name="see-also"></a>Vedere anche  
[Esecuzione di query mediante parametri &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/query-with-parameters-visual-database-tools.md)  
  
