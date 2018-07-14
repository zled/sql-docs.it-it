---
title: Configurare l'accesso DirectQuery per un Database modello tabulare o In memoria | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a5d439a9-5be1-4145-90e8-90777d80e98b
caps.latest.revision: 5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ee6b2f55d1b630b489f65e16a39cb602d5fd5a6d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37243441"
---
# <a name="configure-in-memory-or-directquery-access-for-a-tabular-model-database"></a>Configurare l'accesso in memoria o DirectQuery per un database di modello tabulare
  In questo argomento viene illustrato come modificare le proprietà di connessione di un modello tabulare che è già stato distribuito, per consentire l'utilizzo del modello in modalità DirectQuery.  
  
 Per altre informazioni su queste proprietà e configurazione per gli scenari più comuni, vedere [scenari di distribuzione DirectQuery &#40;modello tabulare di SSAS&#41;](../directquery-deployment-scenarios-ssas-tabular.md).  
  
## <a name="requirements"></a>Requisiti  
 L'abilitazione dell'utilizzo della modalità DirectQuery su un modello tabulare è un processo a più passaggi. È necessario:  
  
1.  Verificare che il modello non disponga di funzionalità che potrebbero provocare errori di convalida in modalità DirectQuery.  
  
2.  Modificare la modalità di archiviazione del modello per supportare DirectQuery.  
  
3.  Distribuire il modello in una modalità che supporti le query in modalità DirectQuery pura o ibrida.  
  
4.  Modificare la stringa di connessione nel database distribuito per supportare la modalità DirectQuery.  
  
 In questo argomento si presuppone che sia stato creato e convalidato il modello e che occorra soltanto abilitare l'accesso DirectQuery da un client quale [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)].  
  
## <a name="procedure"></a>Procedura  
  
#### <a name="change-the-connection-string-properties-of-the-model"></a>Modificare le proprietà della stringa di connessione del modello  
  
1.  In SQL Server Management Studio aprire l'istanza in cui distribuire il modello.  
  
2.  In Esplora oggetti fare doppio clic il nome del database modello e selezionare **proprietà**.  
  
3.  Individuare la proprietà **DirectQueryMode**. Per abilitare l'utilizzo dell'origine dati relazionale, è necessario impostare questa proprietà su uno dei valori seguenti:  
  
    -   **DirectQuery**  
  
    -   **InMemoryWithDirectQuery**  
  
    -   **DirectQueryWithInMemory**  
  
  
