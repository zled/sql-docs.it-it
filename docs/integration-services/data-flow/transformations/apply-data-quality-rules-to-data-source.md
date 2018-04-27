---
title: Applicare le regole relative alla qualità dei dati all'origine dati | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: data-flow
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a965e8f2-004d-4ccc-8523-a185b35b26e2
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fd68d943722d3448b3ed157282bd3beb4a2f63e4
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="apply-data-quality-rules-to-data-source"></a>Applicazione delle regole relative alla qualità dei dati all'origine dati
  È possibile utilizzare Data Quality Services (DQS) per correggere i dati nel flusso di dati del pacchetto connettendo la trasformazione DQS Cleansing all'origine dati. Per altre informazioni su DQS, vedere [Concetti di Data Quality Services](../../../data-quality-services/data-quality-services-concepts.md). Per altre informazioni sulla trasformazione, vedere [Trasformazione DQS Cleansing](../../../integration-services/data-flow/transformations/dqs-cleansing-transformation.md).  
  
 Quando si elaborano i dati con la trasformazione DQS Cleansing, viene creato un progetto Data Quality nel server Data Quality. È possibile utilizzare il client Data Quality per gestire il progetto. Per altre informazioni, vedere [Aprire, sbloccare, rinominare ed eliminare un progetto Data Quality](../../../data-quality-services/open-unlock-rename-and-delete-a-data-quality-project.md).  
  
### <a name="to-correct-data-in-the-data-flow"></a>Per correggere i dati nel flusso di dati  
  
1.  Creare un pacchetto.  
  
2.  Aggiungere e configurare la trasformazione DQS Cleansing. Per altre informazioni, vedere [Finestra di dialogo Editor trasformazione DQS Cleansing](../../../integration-services/data-flow/transformations/dqs-cleansing-transformation-editor-dialog-box.md).  
  
3.  Connettere la trasformazione DQS Cleansing a un'origine dati.  
  
  
