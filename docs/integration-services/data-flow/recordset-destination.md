---
title: Destinazione recordset | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
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
- sql13.dts.designer.recordsetdest.f1
helpviewer_keywords:
- Recordset destination
- ADO recordsets [Integration Services]
- destinations [Integration Services], Recordset
- in-memory ADO recordsets [Integration Services]
ms.assetid: be973cf1-c4ff-49f8-987e-314c08ef98e4
caps.latest.revision: 47
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 1d13d099c416aa794aa46664248d5554658e46f2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="recordset-destination"></a>recordset - destinazione
  La destinazione recordset crea e popola un recordset ADO in memoria. La forma del recordset è definita dall'input della destinazione recordset in fase di progettazione.  
  
## <a name="configuration-of-the-recordset-destination"></a>Configurazione della destinazione recordset  
 Per configurare la destinazione recordset, è necessario specificare la variabile in cui è memorizzato il recordset ADO.  
  
 In fase di esecuzione, nella variabile di tipo Oggetto, specificata nella proprietà VariableName della destinazione recordset, viene scritto un recordset ADO. La variabile rende quindi disponibile il recordset all'esterno del flusso di dati, dove può essere utilizzato da script e altri elementi del pacchetto.  
  
 Questa origine include un solo input. Non supporta un output degli errori.  
  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] o a livello di codice.  
  
 Nella finestra di dialogo **Editor avanzato** sono disponibili le proprietà che è possibile impostare a livello di codice. Per ulteriori informazioni sulle proprietà che è possibile impostare nella finestra di dialogo **Editor avanzato** o a livello di codice, fare clic su uno degli argomenti seguenti:  
  
-   [Proprietà comuni](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
-   [Proprietà personalizzate della destinazione recordset](../../integration-services/data-flow/recordset-destination-custom-properties.md)  
  
 Per altre informazioni su come impostare le proprietà, vedere [Impostazione delle proprietà di un componente del flusso di dati](../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md).  
  
## <a name="related-tasks"></a>Related Tasks  
 [Utilizzo di una destinazione recordset](../../integration-services/data-flow/use-a-recordset-destination.md)  
  
  
