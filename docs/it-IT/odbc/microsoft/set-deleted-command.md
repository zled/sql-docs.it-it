---
title: Comando DELETED SET | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SET DELETED command [ODBC]
ms.assetid: 6b5e0086-156d-471d-8e7f-6c5fa9686cd5
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e05a05b27be43423dd526efccf28e6c2f686f205
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="set-deleted-command"></a>Comando DELETED SET
Specifica se vengono elaborati i record contrassegnati per l'eliminazione e se sono disponibili per altri comandi.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SET DELETED ON | OFF  
```  
  
## <a name="arguments"></a>Argomenti  
 ON  
 (Impostazione predefinita per il driver; il valore predefinito di Visual FoxPro è impostata su OFF). Specifica che i comandi che agiscono su record, compresi i record nelle tabelle correlate, in base all'ambito di ignorare i record contrassegnati per l'eliminazione.  
  
 OFF  
 Specifica che i record contrassegnati per l'eliminazione è possibile accedere tramite i comandi che operano sui record, compresi i record nelle tabelle correlate, in base all'ambito.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare DELETED () per verificare lo stato dei record può essere ottimizzati con la tecnologia di Visual FoxPro Rushmore se la tabella sia indicizzata () eliminato una query.  
  
> [!IMPORTANT]  
>  IMPOSTARE eliminato viene ignorato se l'ambito predefinito per il comando è il record corrente o se si include un ambito di un singolo record. INDICE sempre Ignora impostare eliminato e gli indici di tutti i record nella tabella.  
  
## <a name="see-also"></a>Vedere anche  
 [DELETE (comando SQL)](../../odbc/microsoft/delete-sql-command.md)
