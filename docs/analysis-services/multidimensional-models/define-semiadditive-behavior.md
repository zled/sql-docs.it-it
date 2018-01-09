---
title: Definisci funzioni semiadditive | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- semiadditive
- Business Intelligence enhancements [Analysis Services], semiadditive behavior
- measures [Analysis Services], semiadditive
ms.assetid: b25726bc-728b-4601-ad87-9015c39dc615
caps.latest.revision: "28"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f78bd8b53f358b63393b374594ce76d31791c606
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="define-semiadditive-behavior"></a>Definire una funzione semiadditiva
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Misure semiadditive, che non aggregano in modo uniforme tra tutte le dimensioni, sono molto comuni in numerosi scenari aziendali. Ogni cubo basato su snapshot di saldi nel tempo sono caratterizzati da questo problema. Questi snapshot si trovano in applicazioni per la gestione di titoli, saldi contabili, budget, risorse umane, polizze e risarcimenti assicurativi e numerosi altri scenari aziendali.  
  
 L'aggiunta di funzioni semiadditive a un cubo consente di definire un metodo di aggregazione per singole misure o singoli membri dell'attributo del tipo Conto. Se il cubo contiene una dimensione di tipo Conti, è possibile impostare automaticamente le funzioni semiadditive in base al tipo di conto.  
  
 Per aggiungere funzioni semiadditive aprire un cubo in Progettazione cubi e scegliere **Aggiungi funzionalità di Business Intelligence** dal menu Cubo. Nella Configurazione guidata funzionalità di Business Intelligence selezionare l'opzione **Definizione funzioni semiadditive** nella pagina **Scelta funzionalità avanzata** . Questa procedura guidata consente di eseguire in modo semplificato i passaggi necessari per definire le misure contenenti funzioni semiadditive.  
  
 Ad eccezione di LastChild disponibile nell'edizione Standard, le funzioni semiadditive sono disponibili solo in Business Intelligence o nelle edizioni Enterprise.  
  
## <a name="define-semiadditive-behavior"></a>Definire una funzione semiadditiva  
 Nella pagina **Definizione funzioni semiadditive** della procedura guidata selezionare la modalità di definizione delle funzioni semiadditive selezionando una delle opzioni seguenti:  
  
 **Disabilita funzioni semiadditive**  
 Consente di rimuovere le funzioni semiadditive da un cubo in cui tali funzioni sono state precedentemente definite. Se si seleziona questa opzione, una misura viene reimpostata su **SUM** se è impostata su uno dei tipi di funzione di aggregazione seguenti:  
  
-   By Account  
  
-   Average of Children  
  
-   First Child  
  
-   Last Child  
  
-   Last Nonempty Child  
  
-   First Nonempty Child  
  
-   None  
  
 Questa opzione non modifica le misure che includono una funzione di aggregazione regolare: **Sum**, **Min**, **Max**, **Count**o **Distinct****Count**.  
  
 **È stata rilevata la dimensione di tipo Conti, "Conto", che contiene membri semiadditivi. Il server aggregherà i membri di questa dimensione in base alle funzioni semiadditive specificate per ogni tipo di account.**  
 Tutte le misure di un gruppo di misure dimensionate in base a una dimensione di tipo Conti verranno impostate dal sistema sulla funzione di aggregazione By Account e i membri della dimensione verranno aggregati dal server in base alle funzioni semiadditive specificate per ogni tipo di conto.  
  
> [!NOTE]  
>  Questa opzione è selezionata per impostazione predefinita se la procedura guidata rileva una dimensione di tipo Conti.  
  
 **Definisci funzioni semiadditive per singole misure**  
 Consente di selezionare individualmente le funzioni semiadditive di ogni misura. L'impostazione predefinita è **SUM** (additività completa).  
  
> [!NOTE]  
>  Questa opzione è selezionata per impostazione predefinita se la procedura guidata non rileva una dimensione di tipo Conti.  
  
 Per ogni misura è possibile selezionare tra i tipi di funzionalità semiadditive descritti nella tabella seguente.  
  
|Funzione semiadditiva|Description|  
|---------------------------|-----------------|  
|Average of Children|La funzione di aggregazione di un membro corrisponde alla media dei relativi figli.|  
|ByAccount|Il sistema legge le funzioni semiadditive specificate per il tipo di conto.|  
|Count|La funzione di aggregazione corrisponde a un conteggio dei membri.|  
|Distinct Count|La funzione di aggregazione corrisponde a un conteggio dei membri univoci.|  
|First Child|Il valore del membro viene valutato come il valore del relativo primo figlio assieme alla dimensione temporale.|  
|FirstNonEmpty|Il valore del membro viene valutato come il valore del relativo primo figlio assieme alla dimensione temporale contenente dati.|  
|LastChild|Il valore del membro viene valutato come il valore del relativo ultimo figlio assieme alla dimensione temporale.|  
|LastNonEmpty|Il valore del membro viene valutato come il valore del relativo ultimo figlio assieme alla dimensione temporale contenente dati.|  
|Max|Viene applicata la funzione di aggregazione massima standard.|  
|Min|Viene applicata la funzione di aggregazione minima standard.|  
|None|Non viene applicata alcuna funzione di aggregazione.|  
|SUM|Viene applicata la funzione di somma standard.|  
  
 Al termine della procedura guidata le funzioni semiadditive esistenti vengono sovrascritte.  
  
  
