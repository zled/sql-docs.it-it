---
title: Indici full-text su colonne calcolate non persistenti non sono consentiti | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- full-text indexes
ms.assetid: cba737f7-b187-47d0-8458-23dc18d18aca
caps.latest.revision: 19
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2abb3dba12ec76a4acd5c94998fad69274495203
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37303621"
---
# <a name="full-text-indexes-on-nonpersisted-computed-columns-are-not-allowed"></a>Gli indici full-text su colonne calcolate non persistenti non sono consentiti
  Non è possibile creare indici full-text in colonne calcolate non deterministiche e imprecise. Non è possibile utilizzare tali colonne come colonne tipo o come colonne chiave full-text.  
  
## <a name="description"></a>Description  
 In [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] è possibile creare un indice full-text utilizzando una colonna calcolata non deterministica e imprecisa come colonna tipo o come colonna chiave full-text. Questa funzionalità non è supportata. Quando si esegue l'aggiornamento, gli indici full-text precedenti, incompatibili e non supportati vengono disabilitati.  
  
## <a name="corrective-action"></a>Azione correttiva  
 Per abilitare questi indici full-text, modificare le definizioni di colonna in modo che le colonne siano deterministiche e precise.  
  
## <a name="see-also"></a>Vedere anche  
 [Uso di Preparazione aggiornamento](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
