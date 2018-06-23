---
title: Più transazioni | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- transactions [Integration Services], multiple
- multiple transactions
ms.assetid: c3664a94-be89-40c0-a3a0-84b74a7fedbe
caps.latest.revision: 31
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: c98fa7454a1a01ee6879a514f369e6fb6c1a0570
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36064771"
---
# <a name="multiple-transactions"></a>Più transazioni
  Un pacchetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] potrebbe includere transazioni non correlate. Quando un contenitore all'interno di una gerarchia di contenitori nidificati non supporta le transazioni, i contenitori di livello superiore o inferiore nella gerarchia avviano transazioni distinte se sono configurati per il supporto di transazioni. Viene quindi eseguito il commit o il rollback delle transazioni a partire dall'attività più interna della gerarchia fino al livello del pacchetto. Dopo il commit della transazione più interna, tuttavia, viene eseguito il rollback solo in caso di interruzione di una transazione esterna.  
  
## <a name="illustration-of-multiple-transactions"></a>Illustrazione di più transazioni  
 Si supponga, ad esempio, che un pacchetto includa un contenitore Sequenza con due contenitori Ciclo Foreach ognuno dei quali include due attività Esegui SQL. A differenza del contenitore Sequenza e delle attività Esegui SQL, i contenitori Ciclo Foreach non supportano transazioni. In questo esempio, ogni attività Esegui SQL avvia la propria transazione e non viene eseguito il rollback in caso di interruzione della transazione nell'attività Sequenza.  
  
 Le proprietà TransactionOption del contenitore Sequenza, del contenitore Ciclo Foreach e delle attività Esegui SQL vengono impostate nel modo seguente:  
  
-   La proprietà TransactionOption del contenitore Sequenza viene impostata su **Required**.  
  
-   La proprietà TransactionOption dei contenitori Ciclo Foreach viene impostata su **NotSupported**.  
  
-   La proprietà TransactionOption dell'attività Esegui SQL viene impostata su **Required**.  
  
 Nella figura seguente vengono illustrate le cinque transazioni non correlate del pacchetto. Una transazione viene avviata nel contenitore Sequenza e le altre quattro vengono avviate dalle attività Esegui SQL.  
  
 ![Implementazione di più transazioni](media/mw-dts-trans2.gif "Implementazione di più transazioni")  
  
## <a name="related-tasks"></a>Related Tasks  
 [Configurare un pacchetto per l'utilizzo di transazioni](../relational-databases/native-client-ole-db-transactions/transactions.md)  
  
  