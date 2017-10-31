---
title: MSSQLSERVER_9524 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 9524 (Database Engine error)
ms.assetid: 12da7931-e124-4466-889c-046f1b7b7bfd
caps.latest.revision: 10
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 5896357fde2c8930544bd435884701a7a406ee34
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver9524"></a>MSSQLSERVER_9524
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|9254|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|XMLERR_INVALID_COLUMNSET_XML|  
|Testo del messaggio|Il contenuto XML fornito non è conforme al formato XML richiesto per i set di colonne di tipo sparse.|  
  
## <a name="explanation"></a>Spiegazione  
È stato eseguito il tentativo di modificare un set di colonne. Il contenuto XML di un set di colonne deve soddisfare le restrizioni del formato relativo. Il formato generale di un set di colonne è il seguente:  
  
`<column_name_1>value1</column_name_1><column_name_2>value2</column_name_2>...`  
  
Per ulteriori informazioni sui set di colonne, vedere l'argomento "Utilizzo di set di colonne" nella documentazione online di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="user-action"></a>Azione dell'utente  
Correggere il formato del codice XML per il set di colonne nell'istruzione.  
  

