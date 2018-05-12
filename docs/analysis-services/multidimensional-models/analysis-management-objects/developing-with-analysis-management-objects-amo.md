---
title: Sviluppo con Analysis Management Objects (AMO) | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: amo
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6f47c7fe9abc3b7a23c0eea2dd78a536fb9e0ad2
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="developing-with-analysis-management-objects-amo"></a>Sviluppo con AMO (Analysis Management Objects)
Gli oggetti AMO (Analysis Management) è la raccolta completa di oggetti a cui si accede a livello di codice che consente a un'applicazione gestire un'istanza in esecuzione di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].

In questa sezione vengono illustrati i concetti di AMO, con particolare attenzione agli oggetti principali, e vengono descritti le modalità e il momento in cui utilizzarli nonché il modo in cui sono correlati. Per ulteriori informazioni su specifici oggetti o classi, vedere:

- [Microsoft. AnalysisServices Namespace](http://msdn.microsoft.com/library/microsoft.analysisservices.aspx), per la documentazione di riferimento
- [Analysis Services Management Objects (AMO)](http://www.bing.com/search?q=Analysis+Services+Management+Objects+%28AMO%29), come ricerca generale Bing.com.


 **Novità di SQL Server 2016**

In SQL Server 2016, viene effettuato il refactoring di AMO in più assembly. Le classi generiche, ad esempio Server, Database e dei ruoli, è il **AnalysisServices** Namespace. API specifiche multidimensionale rimangono [Microsoft. AnalysisServices Namespace](https://msdn.microsoft.com/library/ms146720.aspx).

Gli script personalizzati e le applicazioni scritte con le versioni precedenti della libreria AMO continueranno a funzionare senza modifiche. Tuttavia, se si dispone di script o applicazioni che hanno come destinazione SQL Server 2016 in particolare, o se è necessario ricompilare una soluzione personalizzata, assicurarsi di aggiungere il nuovo assembly e spazio dei nomi al progetto.

## <a name="see-also"></a>Vedere anche
[Sviluppo con Analysis Services Scripting Language &#40;ASSL&#41;](../../../analysis-services/multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)
[allo sviluppo con XMLA in Analysis Services](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)
