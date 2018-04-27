---
title: Escludere le righe duplicate (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssms-visual-db
ms.reviewer: ''
ms.suite: sql
ms.technology:
- tools-ssms
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- search criteria [SQL Server], excluding rows
- row duplicates [SQL Server]
- duplicate rows
- row excluded in search [SQL Server]
- result sets [SQL Server], duplicate values
- excluding rows
ms.assetid: ab35a363-421d-4665-946b-ae3f6397af50
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 314556d85b57f20e05f91aa1e0d18735ee6a520e
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="exclude-duplicate-rows-visual-database-tools"></a>Escludere le righe duplicate (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Per visualizzare solo valori univoci in un set di risultati, è possibile impostare l'esclusione dei duplicati dai risultati.  
  
### <a name="to-exclude-duplicate-rows-from-the-result-set"></a>Per escludere le righe duplicate dal set di risultati  
  
1.  Fare clic con il pulsante destro del mouse sullo sfondo del riquadro diagramma e scegliere **Proprietà** dal menu di scelta rapida.  
  
2.  Nella finestra Proprietà fare clic su **Valori Distinct** e impostare il valore su **Sì**.  
  
    In Progettazione query e Progettazione viste la parola chiave DISTINCT verrà inserita davanti all'elenco di colonne visualizzate nell'istruzione SQL.  
  
    > [!NOTE]  
    > Se si utilizza la parola chiave DISTINCT, potrebbe non essere possibile modificare il set di risultati nel riquadro Risultati.  
  
## <a name="see-also"></a>Vedere anche  
[Specifica dei criteri di ricerca &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/specify-search-criteria-visual-database-tools.md)  
[Ordinare e raggruppare i risultati delle query &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/sort-and-group-query-results-visual-database-tools.md)  
  
