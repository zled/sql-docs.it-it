---
title: MSSQLSERVER_107 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 107 (Database Engine error)
ms.assetid: f33f514c-56aa-42e2-841b-e91244da90e2
caps.latest.revision: 9
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ca9315dd71e1232fb76fa1102ab1c833f414ade1
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver107"></a>MSSQLSERVER_107
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|107|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|P_NOCORRMATCH|  
|Testo del messaggio|Il prefisso di colonna '%.* ls' non corrisponde a un alias o nome di tabella utilizzato nella query.|  
  
## <a name="explanation"></a>Spiegazione  
L'elenco di selezione della query contiene un asterisco (*) qualificato erroneamente con un prefisso della colonna. Questo errore può essere restituito nelle condizioni seguenti:  
  
-   Il prefisso di colonna non corrisponde ad alcun alias o nome di tabella utilizzato nella query. Nell'istruzione seguente viene utilizzato ad esempio un nome di alias (`T1`) come prefisso di colonna, ma l'alias non è definito nella clausola FROM.  
  
    ```  
    SELECT T1.* FROM dbo.ErrorLog;  
    ```  
  
-   Un nome di tabella viene specificato come un prefisso di colonna quando nella clausola FROM viene specificato un alias per la tabella. Nell'istruzione seguente, ad esempio, viene utilizzato il nome di tabella `ErrorLog`, ma per la tabella è stato specificato l'alias `T1` nella clausola FROM.  
  
    ```  
    SELECT ErrorLog.* FROM dbo.ErrorLog AS T1;  
    ```  
  
    Se nella clausola FROM è stato specificato un alias per il nome di tabella, è possibile utilizzare solo tale alias come prefisso per le colonne della tabella.  
  
## <a name="user-action"></a>Azione dell'utente  
Mettere in corrispondenza i prefissi di colonna con in nomi di tabella o gli alias specificati nella clausola FROM della query. L'istruzione precedente, ad esempio, può essere corretta nel modo indicato di seguito:  
  
```  
SELECT T1.* FROM dbo.ErrorLog AS T1;  
```  
  
o Gestione configurazione  
  
```  
SELECT ErrorLog.* FROM dbo.ErrorLog;  
```  
  
## <a name="see-also"></a>Vedere anche  
[MSSQLSERVER_4104](~/relational-databases/errors-events/mssqlserver-4104-database-engine-error.md)  
  
