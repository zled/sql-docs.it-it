---
title: Modificare l'ordine delle colonne in una tabella | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: dbe-tables
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- columns [SQL Server], change order in a table
- column order, change
ms.assetid: cd99ef56-9085-431a-a0fc-58e7add5399f
caps.latest.revision: "15"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 21230fae3505719bd2b6f763391ed1687bba8fe8
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="change-column-order-in-a-table"></a>Modificare l'ordine delle colonne in una tabella
[!INCLUDE[tsql-appliesto-ss2016-all_md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  In Progettazione tabelle è possibile modificare l'ordine delle colonne in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
> [!CAUTION]  
>  La modifica dell'ordine delle colonne potrebbe influire su codice e applicazioni che dipendono da un ordine specifico, incluse query, viste, stored procedure, funzioni definite dall'utente e applicazioni client. è pertanto opportuno valutare attentamente ogni eventuale modifica da apportare all'ordine delle colonne prima di procedere. La procedura consigliata è specificare l'ordine nel quale le colonne vengono restituite all'applicazione e il livello della query. Non è necessario basarsi sull'utilizzo di SELECT * per restituire tutte le colonne nell'ordine previsto basato sull'ordine nel quale sono definiti nella tabella. Nelle query e nelle applicazioni, specificare sempre le colonne per nome nell'ordine nel quale si desidera visualizzarle.  
  
 **Contenuto dell'argomento**  
  
-   **Per modificare l'ordine delle colonne:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-change-the-column-order"></a>Per modificare l'ordine delle colonne  
  
1.  In **Esplora oggetti**fare clic con il pulsante destro del mouse sulle colonne da riordinare e selezionare **Progetta**.  
  
2.  Selezionare la casella a sinistra del nome della colonna che si desidera spostare.  
  
3.  Trascinare la colonna in una posizione diversa nella tabella.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
 **Per modificare l'ordine delle colonne**  
  
 Non è possibile eseguire questa attività utilizzando istruzioni Transact-SQL.  
  
###  <a name="TsqlExample"></a>  
