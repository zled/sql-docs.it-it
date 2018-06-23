---
title: Autorizzazioni server per il ruolo public | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 9a276caa-ea38-473d-92bc-26302bfcf660
caps.latest.revision: 11
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a0b125841e2d3c9f03b7ba46519f80af9293a1cd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36068014"
---
# <a name="server-public-permissions"></a>Autorizzazioni server per il ruolo public
  Questa regola consente di determinare se il ruolo del server public dispone di autorizzazioni server. Ogni account di accesso creato nel server è un membro del ruolo del server public. Se questa condizione viene soddisfatta, ogni account di accesso nel server disporrà di autorizzazioni server.  
  
## <a name="best-practices-recommendations"></a>Procedure consigliate  
 Non concedere autorizzazioni server al ruolo del server public.  
  
> [!IMPORTANT]  
>  Al termine dell'installazione il **pubblico** ruolo dispone `CONNECT` l'autorizzazione per tutti gli endpoint ad eccezione di **connessione amministrativa dedicata**. Questa situazione è normale e, generalmente, non deve essere modificata (L'accesso viene controllato tramite la `CONNECT SQL` autorizzazione che viene concessa automaticamente quando vengono creati nuovi account di accesso.)  
  
### <a name="for-more-information"></a>Per ulteriori informazioni  
 [Sicurezza di SQL Server](../security/securing-sql-server.md)  
  
  