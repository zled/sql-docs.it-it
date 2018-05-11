---
title: Creare un conto finanziario della dimensione di tipo padre-figlio | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 66414c6d9959c8a619cb028a244384392cdd1bfb
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="database-dimensions---finance-account-of-parent-child-type"></a>Dimensioni del database - conto finanziario di tipo padre-figlio
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] una dimensione di tipo Conto è una dimensione i cui attributi rappresentano un grafico dei conti per la generazione di report finanziari.  
  
 Una dimensione di tipo Conti consente di gestire in modo selettivo le modalità di aggregazione dei conti nel tempo. Una dimensione di tipo Conti consente inoltre di utilizzare un meccanismo standard per risolvere la maggior parte dei problemi di aggregazione non standard che in genere di verificano nelle soluzione di Business Intelligence per la gestione dei dati finanziari. Se non si disponesse di tale meccanismo standard, la risoluzione dei problemi di aggregazione non standard richiederebbe formule personalizzate di rollup, membri calcolati o script MDX (Multidimensional Expressions).  
  
 Per identificare una dimensione come dimensione di tipo Conti, impostare la proprietà **Type** della dimensione su **Accounts**.  
  
## <a name="dimension-structure"></a>Struttura dimensione  
 In una dimensione di tipo Conti sono contenuti almeno due attributi:  
  
-   Un attributo chiave, ovvero un attributo che consente di identificare singoli conti nella tabella per la dimensione di tipo Conti.  
  
-   Un attributo Conto, ovvero un attributo padre che descrive in che modo i conti vengono disposti in modo gerarchico nella dimensione di tipo Conti.  
  
     Per identificare un attributo come attributo Conto, impostare la proprietà **Type** dell'attributo su **Account** e la proprietà **Usage** su **Parent**.  
  
 Facoltativamente, nelle dimensioni di tipo Conti possono essere contenuti gli attributi seguenti:  
  
-   Un attributo di tipo Conto, ovvero un attributo che definisce il tipo di conto per ogni conto nella dimensione. Viene eseguito il mapping tra i nomi dei membri dell'attributo di tipo Conto e i tipi di conto definiti per il database o il progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] e tali nomi indicano la funzione di aggregazione usata da [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] per tali conti. È inoltre possibile utilizzare operatori unari o formule personalizzate di rollup per determinare le modalità di aggregazione per gli attributi Conto, ma gli attributi di tipo Conto consentono di applicare in modo semplice un comportamento consistente a un grafico dei conti senza che sia necessario apportare modifiche al database relazionale sottostante.  
  
     Per identificare un attributo di tipo Conto, impostare la proprietà **Type** dell'attributo su **AccountType**.  
  
-   Un attributo Nome conto, utilizzato per la generazione di report. Per identificare un attributo relativo al nome del Conto, impostare la proprietà **Type** dell'attributo su **AccountName**.  
  
-   Un attributo Numero conto, utilizzato per la generazione di report. Per identificare un attributo relativo al numero del Conto, impostare la proprietà **Type** dell'attributo su **AccountNumber**.  
  
 Per altre informazioni sui tipi di attributi, vedere [Configurare tipi di attributi](../../analysis-services/multidimensional-models/attribute-properties-configure-attribute-types.md).  
  
## <a name="adding-account-intelligence-with-the-business-intelligence-wizard"></a>Aggiunta di funzionalità di Business Intelligence per la contabilità tramite la Configurazione guidata funzionalità di Business Intelligence  
 Dopo avere definito una dimensione di tipo Conti e avere aggiunto tale dimensione a un cubo, è possibile utilizzare la Configurazione guidata funzionalità di Business Intelligence per aggiungere funzionalità di Business Intelligence per la contabilità, ad esempio funzionalità di identificazione e mapping dei tipi di conto, alla dimensione. Per altre informazioni, vedere [Aggiungere funzionalità di Business Intelligence per la contabilità a una dimensione](../../analysis-services/multidimensional-models/bi-wizard-add-account-intelligence-to-a-dimension.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Gli attributi e gerarchie di attributi](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [Business Intelligence guidata F1 Help](http://msdn.microsoft.com/library/155ac80c-63ae-47aa-9e86-9396e3d920eb)   
 [Tipi di dimensione](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/database-dimension-properties-types.md)  
  
  
