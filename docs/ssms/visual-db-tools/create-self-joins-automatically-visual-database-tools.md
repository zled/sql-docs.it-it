---
title: Creare self-join in modo automatico (Visual Database Tools) | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automatic joins
- self-joins
- joins [SQL Server], self
ms.assetid: f9ec90e8-3aad-415c-a5c4-8dfa9540e37f
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: c25ca1aa33e069fdb08d58196d274aa2198ae3af
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="create-self-joins-automatically-visual-database-tools"></a>Creare self-join in modo automatico (Visual Database Tools)
Se una tabella ha una relazione riflessiva nel database, sarà possibile metterla in join con se stessa automaticamente.  
  
### <a name="to-create-a-self-join-automatically"></a>Per creare automaticamente un self-join  
  
1.  Aggiungere la tabella appropriata al [riquadro Diagramma](../../ssms/visual-db-tools/diagram-pane-visual-database-tools.md) .  
  
2.  Aggiungere nuovamente la stessa tabella in modo che venga visualizzata due volte nel riquadro Diagramma.  
  
    In [Progettazione query e Progettazione viste](../../ssms/visual-db-tools/query-and-view-designer-tools-visual-database-tools.md) verrà assegnato un alias alla seconda istanza aggiungendo un numero sequenziale al nome della tabella. Inoltre, verrà inserita una linea di join tra i due rettangoli che rappresentano i due diversi tipi di partecipazione della tabella nella query.  
  
## <a name="see-also"></a>Vedere anche  
[Eseguire query con join &amp;#40;Visual Database Tools&amp;#41;](../../ssms/visual-db-tools/query-with-joins-visual-database-tools.md)  
  

