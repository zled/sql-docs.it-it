---
title: Sviluppo di un'interfaccia utente per un provider di log personalizzato | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- custom user interface [Integration Services], custom log providers
- custom log providers [Integration Services], developing custom user interface
ms.assetid: 6fd2d269-d87a-4134-82a1-40a09b3b5453
caps.latest.revision: 18
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 7d4173c215200f0b5cb17f68001dfcf21d4f42d9
ms.sourcegitcommit: de5e726db2f287bb32b7910831a0c4649ccf3c4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2018
ms.locfileid: "35331315"
---
# <a name="developing-a-user-interface-for-a-custom-log-provider"></a>Sviluppo di un'interfaccia utente per un provider di log personalizzato
  Molti provider di log di [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] hanno un'interfaccia utente personalizzata che implementa <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsLogProviderUI> e sostituisce la casella di testo **Configurazione** nella finestra di dialogo **Configura log SSIS** con un elenco a discesa filtrato di gestioni connessioni disponibili. Tuttavia, le interfacce utente personalizzate per i provider di log personalizzati non sono implementate in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un provider di log personalizzato](../../../integration-services/extending-packages-custom-objects/log-provider/creating-a-custom-log-provider.md)   
 [Scrittura del codice di un provider di log personalizzato](../../../integration-services/extending-packages-custom-objects/log-provider/coding-a-custom-log-provider.md)  
  
  
