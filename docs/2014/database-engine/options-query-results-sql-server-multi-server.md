---
title: Opzioni (risultati SQL Server-Multi-Server di Query) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.sqleditors.multiserverresultssettings
- VS.ToolsOptionsPages.QueryResults.SqlServer.SQLMultiServerResults
ms.assetid: d6768bd8-9cb5-4606-a726-a33a1df9e1bb
caps.latest.revision: 9
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: c3088e2e265ef44a7d490001b9a7060186ba2c3c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37271797"
---
# <a name="options-query-results-sql-server-multi-server"></a>Opzioni (risultati SQL Server-Multi-Server di Query)
  Quando si esegue una query su più server contemporaneamente, utilizzare questa pagina per specificare le opzioni per la visualizzazione dei set di risultati. Con la funzione Unisci risultati, i set di risultati di tutti i server vengono combinati in un singolo set. Quando si uniscono i risultati, il server che risponde per primo imposta lo schema per il set di risultati. Perché sia possibile unire i set di risultati, la query deve restituire lo stesso numero di colonne con nomi uguali da ogni server. Quando si uniscono i risultati, viene visualizzato un messaggio per ogni server che non corrisponde allo schema (numero di colonne e nomi di colonna) restituito dal server che ha risposto per primo.  
  
 Quando non si uniscono i risultati, il set di risultati restituito da ciascun server verrà visualizzato nella rispettiva griglia con uno schema proprio.  
  
## <a name="uielement-list"></a>Elenco degli elementi di interfaccia  
 **Unisci risultati**  
 Selezionare questa casella di controllo per combinare i set di risultati di molti server nella stessa griglia.  
  
 **Aggiungi nome del server ai risultati**  
 Selezionare questa casella di controllo per includere una colonna aggiuntiva contenente il nome del server che ha generato ogni riga.  
  
 **Aggiungi nome di accesso ai risultati**  
 Selezionare questa casella di controllo per includere una colonna aggiuntiva contenente il nome di accesso utilizzato per connettersi al server che ha generato ogni riga.  
  
## <a name="see-also"></a>Vedere anche  
 [Creare un Server di gestione centrale e un gruppo di Server &#40;SQL Server Management Studio&#41;](../ssms/register-servers/create-a-central-management-server-and-server-group.md)   
 [Eseguire istruzioni su più server contemporaneamente &#40;SQL Server Management Studio&#41;](../ssms/register-servers/execute-statements-against-multiple-servers-simultaneously.md)  
  
  
