---
title: Rimuovere i tipi definiti dall'utente&#39;s nominate a tipi di dati data e ora riservati | Documenti Microsoft
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
- time data type [SQL Server], UDTs
- date data type [SQL Server], UDTs
ms.assetid: 48f109af-b1d1-4f03-a7e3-8a0b05ed94e8
caps.latest.revision: 6
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 71576529890a7cbc6da28e9a04566991d4e91b50
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36158134"
---
# <a name="remove-udt39s-named-after-the-reserved-date-and-time-data-types"></a>Rimuovere i tipi definiti dall'utente&#39;s nominate a tipi di dati data e ora riservati
  È stato rilevato un tipo definito dall'utente denominato in base a un termine riservato per i tipi di dati `date` o `time`.  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Non è consigliabile utilizzare i termini utilizzati per i tipi di dati come nomi per Common Language Runtime (CLR) o per tipi di dati definiti dall'utente alias.  
  
## <a name="corrective-action"></a>Azione correttiva  
 Rimuovere il tipo definito dall'utente denominato in base al tipo di dati e ricreare il tipo con un nome non riservato.  
  
  