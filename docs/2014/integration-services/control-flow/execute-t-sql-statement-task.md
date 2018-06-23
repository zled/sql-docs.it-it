---
title: Attività Esegui istruzione T-SQL | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.executetsqlstatementtask.f1
helpviewer_keywords:
- Transact-SQL statements, SSIS
- statements [Integration Services]
- Execute T-SQL Statement task [Integration Services]
ms.assetid: 7e9086ca-d27e-46c0-bfad-d61333ebd55e
caps.latest.revision: 34
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 74be247e47e50b61dfea84863a5969008f160ff0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36066502"
---
# <a name="execute-t-sql-statement-task"></a>Attività Esegui istruzione T-SQL
  L'attività Esegui istruzione T-SQL consente di eseguire istruzioni Transact-SQL. Per altre informazioni, vedere [Guida di riferimento a Transact-SQL &#40;Motore di database&#41;](/sql/t-sql/language-reference) e [Query di Integration Services &#40;SSIS&#41;](../integration-services-ssis-queries.md).  
  
 Questa attività è simile all'attività Esegui SQL, ma supporta solo la versione Transact-SQL del linguaggio SQL e non può essere utilizzata per eseguire istruzioni su server che utilizzano altri sottolinguaggi del linguaggio SQL. Se è necessario eseguire query con parametri, salvare i risultati delle query nelle variabili oppure utilizzare espressioni di proprietà, è necessario utilizzare l'attività Esegui SQL anziché l'attività Esegui istruzione T-SQL. Per altre informazioni, vedere [Attività Esegui SQL](execute-sql-task.md).  
  
## <a name="configuration-of-the-execute-t-sql-task"></a>Configurazione dell'attività Esegui istruzione T-SQL  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../../includes/ssis-md.md)] . Questa attività è disponibile nella sezione **Attività di manutenzione** della **casella degli strumenti** di Progettazione [!INCLUDE[ssIS](../../../includes/ssis-md.md)] .  
  
 Per ulteriori informazioni sulle proprietà che è possibile impostare in Progettazione [!INCLUDE[ssIS](../../../includes/ssis-md.md)] , fare clic sull'argomento seguente:  
  
-   [Attività Esegui istruzione T-SQL &#40;Piano di manutenzione&#41;](../../relational-databases/maintenance-plans/execute-t-sql-statement-task-maintenance-plan.md)  
  
 Per altre informazioni sull'impostazione di queste proprietà in Progettazione [!INCLUDE[ssIS](../../../includes/ssis-md.md)] , fare clic sull'argomento seguente:  
  
-   [Impostare le proprietà di un'attività o di un contenitore](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Attività di Integration Services](integration-services-tasks.md)   
 [Flusso di controllo](control-flow.md)   
 [MERGE nei pacchetti di Integration Services](merge-in-integration-services-packages.md)  
  
  
