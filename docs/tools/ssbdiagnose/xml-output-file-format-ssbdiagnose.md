---
title: Formato di File di Output XML (ssbdiagnose) | Documenti Microsoft
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssbdiagnose
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- XML output file format [ssbdiagnose]
- ssbdiagnose
ms.assetid: 3ceb991b-6f15-4504-8828-de5adf448bc5
caps.latest.revision: 13
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 260025d94044d834b4834a84af7b633964c05f6b
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MTE
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="xml-output-file-format-ssbdiagnose"></a>Formato del file di output XML (ssbdiagnose)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  L'utilità **ssbdiagnose** restituisce un file di output in formato XML quando viene eseguita con l'opzione **-XML** . Nel file di output XML vengono elencate informazioni di intestazione e gli errori rilevati nella configurazione o nella conversazione di [!INCLUDE[ssSB](../../includes/sssb-md.md)] analizzata. È possibile scrivere un'applicazione per analizzare o generare un report relativo agli errori elencati nel file. In alternativa, è possibile visualizzare il file XML in un editor XML generico, ad esempio XML Notepad.  
  
 Un file di output di **ssbdiangose** contiene un elemento radice DiagnosticInformation con due tipi di figlio:  
  
-   Un elemento Banner con le informazioni di intestazione.  
  
-   Un elemento Issue per ogni problema segnalato da **ssbdiagnose**.  
  
## <a name="diagnosticinformation-root-element"></a>Elemento radice DiagnosticInformation  
  
-   [Elemento DiagnosticInformation &#40;ssbdiagnose&#41;](../../tools/ssbdiagnose/diagnosticinformation-element-ssbdiagnose.md)  
  
## <a name="banner-element"></a>Elemento Banner  
  
-   [Elemento Banner &#40;ssbdiagnose&#41;](../../tools/ssbdiagnose/banner-element-ssbdiagnose.md)  
  
## <a name="issue-element"></a>Elemento Issue  
  
-   [Elemento Issue &#40;ssbdiagnose&#41;](../../tools/ssbdiagnose/issue-element-ssbdiagnose.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Utilità ssbdiagnose &#40;Service Broker&#41;](../../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md)  
  
  
