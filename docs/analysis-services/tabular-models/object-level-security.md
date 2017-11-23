---
title: Sicurezza a livello di oggetto del modello tabulare | Documenti Microsoft
ms.custom: 
ms.date: 06/20/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tabular-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: 
ms.assetid: 
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: bc44742d56d744e9d0d4c1f1697d0bcd4e40488c
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="object-level-security"></a>Sicurezza a livello di oggetto

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

Protezione del modello di dati inizia con l'implementazione in modo efficace [ruoli](../../analysis-services/tabular-models/roles-ssas-tabular.md) e filtri a livello di riga per definire le autorizzazioni utente per gli oggetti del modello di dati e i dati. A partire da modelli tabulari di 1400, è inoltre possibile definire la sicurezza a livello di oggetto, che include la sicurezza a livello di tabella e la sicurezza a livello di colonna nel [oggetto ruoli](../../analysis-services/tabular-models-scripting-language-objects/roles-object-tmsl.md).

## <a name="table-level-security"></a>Sicurezza a livello di tabella

Con la sicurezza a livello di tabella, non è possibile solo limitare l'accesso ai dati di tabella, ma anche i nomi di tabella sensibili, contribuendo a evitare che utenti malintenzionati a scoprire se una tabella esistente. 

 Sicurezza a livello di tabella è impostato nei metadati basato su JSON in Model.bim, [Tabular Model Scripting Language (TMSL)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md), o [modello a oggetti tabulare (TOM)](../../analysis-services/tabular-model-programming-compatibility-level-1200/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo.md). Impostare il **metadataPermission** proprietà del **gli oggetti Tablepermission** classe il [oggetto ruoli](../../analysis-services/tabular-models-scripting-language-objects/roles-object-tmsl.md) a **Nessuno**.

In questo esempio, la proprietà metadataPermission della classe gli oggetti Tablepermission per la tabella Product è impostata su none:

```
"roles": [
  {
    "name": "Users",
    "description": "All allowed users to query the model",
    "modelPermission": "read",
    "tablePermissions": [
      {
        "name": "Product",
        "metadataPermission": "none"
      }
    ]
  }
```

## <a name="column-level-security"></a>Sicurezza a livello di colonna

Simile alla protezione a livello di tabella, con la sicurezza a livello di colonna è possibile non solo limitare l'accesso a dati della colonna, ma anche i nomi di colonna riservati, aiutare a impedire agli utenti malintenzionati di individuazione di una colonna.

 Sicurezza a livello di colonna è impostata nei metadati basato su JSON in Model.bim, [Tabular Model Scripting Language (TMSL)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md), o [modello a oggetti tabulare (TOM)](../../analysis-services/tabular-model-programming-compatibility-level-1200/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo.md). Impostare il **metadataPermission** proprietà del **columnPermissions** classe il [oggetto ruoli](../../analysis-services/tabular-models-scripting-language-objects/roles-object-tmsl.md) a **Nessuno**.

In questo esempio, la proprietà metadataPermission della classe per la colonna tariffa di Base nella tabella Employees columnPermissions è impostata su none:

```
"roles": [
  {
    "name": "Users",
    "description": "All allowed users to query the model",
    "modelPermission": "read",
    "tablePermissions": [
      {
        "name": "Employee",
        "columnPermissions": [
          {
            "name": "Base Rate",
            "metadataPermission": "none"
          }
        ]
      }
    ]
  }
```

## <a name="restrictions"></a>Restrizioni

*  Impossibile impostare la sicurezza a livello di tabella per un modello se si interrompe una catena di relazioni. Viene generato un errore in fase di progettazione.
 Ad esempio, se esistono relazioni tra le tabelle A e B, B e C, è possibile proteggere tabella B. Se nella tabella B è protetto, una query in una tabella non è di transito le relazioni tra la tabella A e B, B e C. In questo caso, potrebbe essere configurata una relazione separata tra le tabelle A e B.

    ![Sicurezza a livello di tabella](../../analysis-services/tabular-models/media/ssas-ols.png)  


*  Impossibile combinare la sicurezza a livello di riga e la sicurezza a livello di oggetto dai diversi ruoli perché potrebbe introdurre accesso non autorizzato ai dati protetti. Viene generato un errore in fase di query per gli utenti che sono membri di tale combinazione di ruoli.

*  Calcoli dinamici (misure, indicatori KPI, DetailRows) sono automaticamente limitati che fanno riferimento a una tabella protetta o una colonna. Non esiste alcun meccanismo per proteggere in modo esplicito una misura, è possibile proteggere in modo implicito una misura aggiornando l'espressione per fare riferimento a una tabella protetta o una colonna.

*  Relazioni che fanno riferimento a una colonna protetta di lavoro fornite nella tabella che è la colonna non è protetto.




## <a name="see-also"></a>Vedere anche  
[Roles](../../analysis-services/tabular-models/roles-ssas-tabular.md)  
[Oggetto Roles (TMSL)](../../analysis-services/tabular-models-scripting-language-objects/roles-object-tmsl.md)  
[Supporto per TMSL (Tabular Model Scripting Language) in SSMS](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)  
[Modello a oggetti tabulare (TOM)](../../analysis-services/tabular-model-programming-compatibility-level-1200/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo.md).

  
