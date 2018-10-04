---
title: L'aggiornamento causerà la ricerca Full-Text da utilizzare a livello di istanza, non globali, word breaker e filtri per impostazione predefinita | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- filters [Full-Text Search]
- word breakers [Full-Text Search]
ms.assetid: 93ee8fcb-d11c-49fa-8fac-51ed31a8f008
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d1974d81e36842f8c8d2c8ae70eceec26acb2dfe
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48175681"
---
# <a name="upgrading-will-cause-full-text-search-to-use-instance-level-not-global-word-breakers-and-filters-by-default"></a>A seguito dell'aggiornamento, per la ricerca full-text verranno utilizzati per impostazione predefinita word breaker e filtri a livello di istanza, non globali
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consente la registrazione a livello di istanza per i nuovi word breaker e i nuovi filtri.  
  
## <a name="component"></a>Componente  
 Ricerca full-text  
  
## <a name="description"></a>Description  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consente la registrazione a livello di istanza per i nuovi word breaker e i nuovi filtri. La registrazione a livello di istanza garantisce un isolamento funzionale e la sicurezza delle istanze.  
  
## <a name="corrective-action"></a>Azione correttiva  
 Dopo l'aggiornamento, utilizzare `sp_fulltext_service` per impostare la proprietà del servizio e `load_os_resources` che consente il caricamento dei componenti. È necessario eseguire quanto segue:  
  
 `sp_fulltext_service 'load_os_resources', 1`  
  
## <a name="see-also"></a>Vedere anche  
 [Uso di Preparazione aggiornamento](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
