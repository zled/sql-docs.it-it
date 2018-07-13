---
title: Proprietà server (pagina Esecuzione) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.serverproperties.execution.f1
ms.assetid: 53b77db1-b013-4dac-82dd-30c0de276639
caps.latest.revision: 31
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: d15a9184c61163d59fbe0d23ecf98d018e6fd7a0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37276357"
---
# <a name="server-properties-execution-page"></a>Proprietà server (pagina Esecuzione)
  Utilizzare questa pagina per impostare un valore di timeout per l'esecuzione dei report. Questo valore si applica a tutti i report elaborati dall'istanza del server di report corrente, ma è possibile modificarlo a livello di singolo report. Il valore specificato deve essere appropriato per tutte le elaborazioni dei report nel server di report, nonché per l'elaborazione delle query nel server di database quando il server di report recupera i dati utilizzati nel report.  
  
 Per aprire questa pagina, avviare [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connettersi a un'istanza del server di report, fare clic con il pulsante destro del mouse sul nome del server di report e scegliere **Proprietà**. Fare clic su **Esecuzione** per aprire la pagina.  
  
## <a name="options"></a>Opzioni  
 **Nessun timeout per l'esecuzione del report**  
 Consente a un server di report di completare l'elaborazione del report senza alcun limite di tempo.  
  
 **La durata dell'esecuzione del report non può superare il numero di secondi seguente**  
 Imposta un vincolo di tempo per l'esecuzione del report. Il periodo di tempo viene calcolato dal momento della richiesta del report. Se il tempo scade prima del completamento dell'elaborazione del report, il processo e ogni query in-process verranno annullati nelle origini dei dati esterne.  
  
## <a name="see-also"></a>Vedere anche  
 [Impostare le proprietà di un server di report &#40;Management Studio&#41;](set-report-server-properties-management-studio.md)   
 [Eseguire la connessione a un server di report in Management Studio](connect-to-a-report-server-in-management-studio.md)   
 [Impostare le proprietà di elaborazione dei Report](../report-server/set-report-processing-properties.md)   
 [Impostazione dei valori di timeout per l'elaborazione di report e di set di dati condivisi &#40;SSRS&#41;](../report-server/setting-time-out-values-for-report-and-shared-dataset-processing-ssrs.md)   
 [Guida sensibile al contesto del server di report in Management Studio](report-server-in-management-studio-f1-help.md)  
  
  
