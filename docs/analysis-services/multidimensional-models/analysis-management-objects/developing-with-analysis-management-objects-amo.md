---
title: Sviluppo con Analysis Management Objects (AMO) | Documenti Microsoft
ms.custom:
- SQL2016_New_Updated
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Analysis Management Objects, programming
- AMO, programming
ms.assetid: 91354fc9-22da-4724-b97f-3b1e7b0e69d3
caps.latest.revision: 47
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f746ed6c0ad7dc9c0702282f7a508d44cca7f8be
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

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
[Lo sviluppo con Analysis Services Scripting Language &#40; ASSL &#41; ](../../../analysis-services/multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md) 
 [Allo sviluppo con XMLA in Analysis Services](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)

