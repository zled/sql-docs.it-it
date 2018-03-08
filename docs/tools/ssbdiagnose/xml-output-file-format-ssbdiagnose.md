---
title: Formato di File di Output XML (ssbdiagnose) | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssbdiagnose
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML output file format [ssbdiagnose]
- ssbdiagnose
ms.assetid: 3ceb991b-6f15-4504-8828-de5adf448bc5
caps.latest.revision: "13"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 11c9dbc6f279782a0083a12b0ce304f5959e58ad
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="xml-output-file-format-ssbdiagnose"></a>Formato del file di output XML (ssbdiagnose)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Il **ssbdiagnose** utilità fornisce l'output come un file XML quando viene eseguita con il **- XML** passare. Nel file di output XML vengono elencate informazioni di intestazione e gli errori rilevati nella configurazione o nella conversazione di [!INCLUDE[ssSB](../../includes/sssb-md.md)] analizzata. È possibile scrivere un'applicazione per analizzare o generare un report relativo agli errori elencati nel file. In alternativa, è possibile visualizzare il file XML in un editor XML generico, ad esempio XML Notepad.  
  
 Un file di output di **ssbdiangose** contiene un elemento radice DiagnosticInformation con due tipi di figlio:  
  
-   Un elemento Banner con le informazioni di intestazione.  
  
-   Un elemento Issue per ogni problema segnalato da **ssbdiagnose**.  
  
## <a name="diagnosticinformation-root-element"></a>Elemento radice DiagnosticInformation  
  
-   [Elemento DiagnosticInformation &#40; ssbdiagnose &#41;](../../tools/ssbdiagnose/diagnosticinformation-element-ssbdiagnose.md)  
  
## <a name="banner-element"></a>Elemento Banner  
  
-   [Elemento banner &#40; ssbdiagnose &#41;](../../tools/ssbdiagnose/banner-element-ssbdiagnose.md)  
  
## <a name="issue-element"></a>Elemento Issue  
  
-   [Elemento Issue &#40; ssbdiagnose &#41;](../../tools/ssbdiagnose/issue-element-ssbdiagnose.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Utilità ssbdiagnose &#40; Service Broker &#41;](../../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md)  
  
  
