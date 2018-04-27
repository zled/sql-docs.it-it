---
title: Destinazione DataReader | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
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
f1_keywords:
- sql13.dts.designer.datareaderdest.f1
helpviewer_keywords:
- DataReader destination
- destinations [Integration Services], DataReader
ms.assetid: 56fcc4bf-c901-42c3-a71d-110039293431
caps.latest.revision: 30
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bd361b6ca3f287c6874f734a1d3b6f4f3365b450
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="datareader-destination"></a>DataReader - destinazione
  La destinazione DataReader espone i dati in un flusso di dati usando l'interfaccia **DataReader** di ADO.NET. I dati possono essere quindi utilizzati da altre applicazioni. È ad esempio possibile configurare l'origine dati di un report di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in modo da usare i risultati dell'esecuzione di un pacchetto di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . A tale scopo è necessario creare un flusso di dati che implementa la destinazione DataReader.  
  
 Per informazioni sull'accesso e la lettura di valori nella destinazione DataReader a livello di programmazione, vedere [Caricamento dell'output di un pacchetto locale](../../integration-services/run-manage-packages-programmatically/loading-the-output-of-a-local-package.md).  
  
## <a name="configuration-of-the-datareader-destination"></a>Configurazione della destinazione DataReader  
 È possibile specificare un valore di timeout per la destinazione DataReader e indicare se tale destinazione genera errori in caso di timeout. Si verifica un timeout se l'applicazione non richiede dati entro l'intervallo di tempo specificato.  
  
 La destinazione DataReader include un input. Non supporta un output degli errori.  
  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] o a livello di codice.  
  
 Per ulteriori informazioni sulle proprietà che è possibile impostare nella finestra di dialogo **Editor avanzato** o a livello di codice, fare clic su uno degli argomenti seguenti:  
  
-   [Proprietà comuni](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
-   [Proprietà personalizzate della destinazione DataReader](../../integration-services/data-flow/datareader-destination-custom-properties.md)  
  
 Per altre informazioni su come impostare le proprietà, vedere [Impostare le proprietà di un componente del flusso di dati](../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md).  
  
  
