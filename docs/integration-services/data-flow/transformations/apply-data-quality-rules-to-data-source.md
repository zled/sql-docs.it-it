---
title: "Applicare regole relative alla qualità dei dati all'origine dati | Documenti Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a965e8f2-004d-4ccc-8523-a185b35b26e2
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: aab3d6859df95dff080fe93aa686ee70b3c5c13a
ms.contentlocale: it-it
ms.lasthandoff: 09/27/2017

---
# <a name="apply-data-quality-rules-to-data-source"></a>Applicazione delle regole relative alla qualità dei dati all'origine dati
  È possibile utilizzare Data Quality Services (DQS) per correggere i dati nel flusso di dati del pacchetto connettendo la trasformazione DQS Cleansing all'origine dati. Per altre informazioni su DQS, vedere [Concetti di Data Quality Services](../../../data-quality-services/data-quality-services-concepts.md). Per altre informazioni sulla trasformazione, vedere [Trasformazione DQS Cleansing](../../../integration-services/data-flow/transformations/dqs-cleansing-transformation.md).  
  
 Quando si elaborano i dati con la trasformazione DQS Cleansing, viene creato un progetto Data Quality nel server Data Quality. È possibile utilizzare il client Data Quality per gestire il progetto. Per altre informazioni, vedere [Aprire, sbloccare, rinominare ed eliminare un progetto Data Quality](../../../data-quality-services/open-unlock-rename-and-delete-a-data-quality-project.md).  
  
### <a name="to-correct-data-in-the-data-flow"></a>Per correggere i dati nel flusso di dati  
  
1.  Creare un pacchetto.  
  
2.  Aggiungere e configurare la trasformazione DQS Cleansing. Per altre informazioni, vedere [Finestra di dialogo Editor trasformazione DQS Cleansing](../../../integration-services/data-flow/transformations/dqs-cleansing-transformation-editor-dialog-box.md).  
  
3.  Connettere la trasformazione DQS Cleansing a un'origine dati.  
  
  

