---
title: Trasformazione Conteggio righe | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.component: data-flow
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.rowcounttrans.f1
helpviewer_keywords:
- updating variables
- Row Count transformation
- number of rows
- variables [Integration Services], updating
- counting rows
ms.assetid: b68293b9-a68c-40be-9d81-77342da1be29
caps.latest.revision: 43
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0148a0b0844f0977ea89686692ae6a23ecc090e1
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="row-count-transformation"></a>Conteggio righe - trasformazione
  La trasformazione Conteggio righe consente di contare le righe che passano attraverso un flusso di dati e di memorizzare il totale in una variabile.  
  
 Un pacchetto di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] può usare i numeri delle righe per aggiornare le variabili utilizzate in script, espressioni ed espressioni di proprietà. È ad esempio possibile utilizzare la variabile che contiene il numero delle righe per aggiornare il testo di un messaggio di posta elettronica in modo che includa il numero delle righe. La variabile utilizzata dalla trasformazione Conteggio righe deve esistere e trovarsi nell'ambito dell'attività Flusso di dati a cui appartiene il flusso di dati con la trasformazione Conteggio righe.  
  
 La trasformazione archivia nella variabile il valore relativo al numero delle righe solo dopo il passaggio dell'ultima riga attraverso la trasformazione. Il valore della variabile non viene pertanto aggiornato in tempo per essere utilizzato nel flusso di dati che contiene la trasformazione Conteggio righe. È possibile utilizzare la variabile aggiornata in un flusso di dati separato.  
  
 Questa trasformazione include un input e un output. Non supporta un output degli errori.  
  
## <a name="configuration-of-the-row-count-transformation"></a>Configurazione della trasformazione Conteggio righe  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../../includes/ssis-md.md)] o a livello di codice.  
  
 Nella finestra di dialogo **Editor avanzato** sono disponibili le proprietà che è possibile impostare a livello di codice. Per ulteriori informazioni sulle proprietà che è possibile impostare nella finestra di dialogo **Editor avanzato** o a livello di codice, fare clic su uno degli argomenti seguenti:  
  
-   [Proprietà comuni](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
-   [Proprietà personalizzate delle trasformazioni](../../../integration-services/data-flow/transformations/transformation-custom-properties.md)  
  
## <a name="related-tasks"></a>Related Tasks  
 Per informazioni su come impostare le proprietà del componente, vedere [Impostazione delle proprietà di un componente del flusso di dati](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Variabili di Integration Services &#40;SSIS&#41;](../../../integration-services/integration-services-ssis-variables.md)   
 [Flusso di dati](../../../integration-services/data-flow/data-flow.md)   
 [Trasformazioni di Integration Services](../../../integration-services/data-flow/transformations/integration-services-transformations.md)  
  
  
