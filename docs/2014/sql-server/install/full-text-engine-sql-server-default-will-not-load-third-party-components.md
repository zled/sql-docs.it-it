---
title: Il motore Full-Text Microsoft per SQL Server non caricherà i componenti di terze parti non firmati per impostazione predefinita | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Full-Text Engine for SQL service
- MSFTESQL service
ms.assetid: 029f9895-7232-4149-9362-3ab1a4133d21
caps.latest.revision: 20
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8c66544657e97ed8efcf2ed0dc46dfe21702787a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36069532"
---
# <a name="the-microsoft-full-text-engine-for-sql-server-will-not-load-unsigned-third-party-components-by-default"></a>Per impostazione predefinita, il motore di ricerca full-text Microsoft per SQL Server non carica componenti di terze parti non firmato
  Per impostazione predefinita, il motore di ricerca full-text [!INCLUDE[msCoName](../../includes/msconame-md.md)] per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non carica componenti non firmati da [!INCLUDE[msCoName](../../includes/msconame-md.md)].  
  
## <a name="component"></a>Componente  
 Ricerca full-text  
  
## <a name="description"></a>Description  
 Per impostazione predefinita, dopo l'aggiornamento, un filtro di terze parti, ad esempio un filtro PDF, attualmente installato nel server non viene caricato nel motore di ricerca full-text [!INCLUDE[msCoName](../../includes/msconame-md.md)] per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="corrective-action"></a>Azione correttiva  
 Per caricare un filtro di terze parti, è necessario impostare *load_os_resource* e disattivare *verify_signature* su quell'istanza.  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo di preparazione aggiornamento](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  