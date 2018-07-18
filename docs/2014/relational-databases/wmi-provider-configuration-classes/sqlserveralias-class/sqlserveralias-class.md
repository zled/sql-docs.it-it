---
title: Classe SqlServerAlias | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- SqlServerAlias Class
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SqlServerAlias class
ms.assetid: 475662b9-6985-45bf-b1e9-b0f26ef50443
caps.latest.revision: 33
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 68976bc9c8683554ac58a0744196ecfa5bc7e689
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37274277"
---
# <a name="sqlserveralias-class"></a>Classe SqlServerAlias
  La [classe SqlServerAlias](sqlserveralias-class.md) rappresenta un alias di connessione al server.  
  
 È necessario un alias di connessione al server quando si verificano le seguenti condizioni:  
  
-   Il client si connette a un'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] su un trasporto di rete diverso da quello predefinito.  
  
-   L'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] a cui è connesso il client è in attesa su una named pipe alternativa.  
  
 **Nota:** il [classe SqlServerAlias](sqlserveralias-class.md) eredita il `Put` metodo dalla classe Provider. Tuttavia, non viene restituito alcun risultato come indicato dal metodo `Provider::Put`. Per ulteriori informazioni, vedere la documentazione di WMI.  
  
## <a name="see-also"></a>Vedere anche  
 [Configurazione di protocolli client](http://technet.microsoft.com/library/ms181035.aspx)  
  
  
