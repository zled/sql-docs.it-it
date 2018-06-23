---
title: Destinazione DataReader | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.datareaderdest.f1
helpviewer_keywords:
- DataReader destination
- destinations [Integration Services], DataReader
ms.assetid: 56fcc4bf-c901-42c3-a71d-110039293431
caps.latest.revision: 30
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: faef5d51b7a0b84781879ab3b7f413a49915a126
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36055067"
---
# <a name="datareader-destination"></a>DataReader - destinazione
  La destinazione DataReader espone i dati in un flusso di dati utilizzando l'interfaccia `DataReader` di ADO.NET. I dati possono essere quindi utilizzati da altre applicazioni. È ad esempio possibile configurare l'origine dati di un report di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in modo da usare i risultati dell'esecuzione di un pacchetto di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . A tale scopo è necessario creare un flusso di dati che implementa la destinazione DataReader.  
  
 Per informazioni sull'accesso e la lettura di valori nella destinazione DataReader a livello di programmazione, vedere [Caricamento dell'output di un pacchetto locale](../run-manage-packages-programmatically/loading-the-output-of-a-local-package.md).  
  
## <a name="configuration-of-the-datareader-destination"></a>Configurazione della destinazione DataReader  
 È possibile specificare un valore di timeout per la destinazione DataReader e indicare se tale destinazione genera errori in caso di timeout. Si verifica un timeout se l'applicazione non richiede dati entro l'intervallo di tempo specificato.  
  
 La destinazione DataReader include un input. Non supporta un output degli errori.  
  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] o a livello di codice.  
  
 Per ulteriori informazioni sulle proprietà che è possibile impostare nella finestra di dialogo **Editor avanzato** o a livello di codice, fare clic su uno degli argomenti seguenti:  
  
-   [Proprietà comuni](../common-properties.md)  
  
-   [Proprietà personalizzate della destinazione DataReader](datareader-destination-custom-properties.md)  
  
 Per altre informazioni su come impostare le proprietà, vedere [Impostazione delle proprietà di un componente flusso di dati](set-the-properties-of-a-data-flow-component.md).  
  
  