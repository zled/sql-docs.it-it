---
title: Connettersi a un'origine dati (SSAS) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.bidtoolset.conndatasource.f1
ms.assetid: 1e2b17e9-092b-4af1-8a58-c52b8fe10ff1
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: f33af08d91f2c8e739c9295daed0ae47563ede51
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36067091"
---
# <a name="connect-to-a-data-source-ssas"></a>Connessione a un'origine dati (SSAS)
  Questa pagina dell' **Importazione guidata tabella** consente di creare una nuova connessione a diverse origini dati, ad esempio database relazionali, feed di dati e file. Per accedere alla procedura guidata da [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], dal menu **Modello** selezionare **Importa da origine dati**.  
  
 Per connettersi a un'origine dati, è necessario che nel computer sia installato il provider appropriato. È necessario che sia installato anche il provider appropriato sul server di database dell'area di lavoro. Per i server a 32 bit (x86), devono essere installati provider a 32 bit. Per i server a 64 bit (x64), devono essere installati provider a 64 bit.  
  
 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] sempre in esecuzione in un processo a 32 bit, indipendentemente dall'architettura. Quando si esegue [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] su un computer a 64 bit, è necessario tenere presente quanto indicato di seguito in caso di installazione di provider di dati:  
  
-   Per provider che supportano l'installazione side-by-side di provider a 32 e a 64 bit, è necessario installare entrambi i provider.  
  
-   Per il provider ACE, è necessario installare la versione a 64 bit del provider. Poiché tramite Office viene installato automaticamente il provider ACE, non è necessario eseguire una versione a 32 bit di Microsoft Office su un computer a 64 bit in cui viene ospitato il server di database dell'area di lavoro.  
  
     Il provider ACE viene utilizzato per importazioni da file di testo, di Excel e di Access. Se il supporto per queste origini dati non è necessario, è possibile eseguire quindi una versione a 32 bit di Microsoft Office su un computer che esegue un server di database dell'area di lavoro a 64 bit.  
  
-   Per altri provider che non supportano l'installazione side-by-side di provider a 32 e a 64 bit, è necessario installare il provider a 32 bit. Se sono disponibili solo computer a 64 bit, è necessario utilizzare un computer remoto con un provider a 64 bit installato come server di database dell'area di lavoro.  
  
  