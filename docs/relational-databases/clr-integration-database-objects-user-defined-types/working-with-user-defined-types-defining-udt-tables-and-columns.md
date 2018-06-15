---
title: Definizione di tabelle e colonne UDT | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: clr
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
dev_langs:
- TSQL
helpviewer_keywords:
- user-defined types [CLR integration], columns
- UDTs [CLR integration], columns
- columns [CLR integration]
- user-defined types [CLR integration], tables
- tables [CLR integration]
- UDTs [CLR integration], tables
- UDTs [CLR integration], indexes
- user-defined types [CLR integration], indexes
- indexes [CLR integration]
ms.assetid: aea495f4-ce26-4952-b019-38f012625f3f
caps.latest.revision: 11
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 7fb463a9cf7cde943357ae7b1f3da8ed1dbfb253
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32919226"
---
# <a name="working-with-user-defined-types---defining-udt-tables-and-columns"></a>Utilizzo di tipi definiti dall'utente - definizione delle colonne e tabelle di tipo definito dall'utente
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Una volta che l'assembly contenente il tipo definito dall'utente (UDT) è stata registrata nella definizione di un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database, può essere utilizzato in una definizione di colonna.  
  
## <a name="creating-tables-with-udts"></a>Creazione di tabelle con tipo definito dall'utente  
 Per la creazione di una colonna con tipo definito dall'utente in una tabella non è necessaria una sintassi speciale. È possibile utilizzare il nome del tipo definito dall'utente in una definizione di colonna come se fosse uno dei tipi di dati intrinseci di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. CREATE TABLE seguente [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzione crea una tabella denominata **punti**, con una colonna denominata **ID,** definito come un **int** colonna identity e chiave primaria per la tabella. La seconda colonna è denominata **PointValue**, con un tipo di dati **punto**. Il nome dello schema utilizzato in questo esempio è **dbo**. Si noti che per specificare un nome di schema è necessario disporre delle autorizzazioni appropriate. Se si omette il nome dello schema, viene utilizzato lo schema predefinito per l'utente del database.  
  
```  
CREATE TABLE dbo.Points   
(ID int IDENTITY(1,1) PRIMARY KEY, PointValue Point)  
```  
  
## <a name="creating-indexes-on-udt-columns"></a>Creazione di indici in colonne con tipo definito dall'utente  
 Per indicizzare una colonna con tipo definito dall'utente, sono disponibili due opzioni:  
  
-   Indicizzare il valore completo. In questo caso, se il tipo definito dall'utente ha ordinamento binario, è possibile creare un indice sull'intera colonna con tipo definito dall'utente utilizzando l'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE INDEX.  
  
-   Indicizzare espressioni dei tipi definiti dall'utente. È possibile creare indici in colonne calcolate persistenti su espressioni dei tipi definiti dall'utente. L'espressione del tipo definito dall'utente può essere un campo, un metodo o una proprietà di un tipo definito dall'utente. L'espressione deve essere deterministica e non deve eseguire accesso ai dati.  
  
 Per ulteriori informazioni, vedere [tipi CLR definiti dall'utente](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md) e [CREATE INDEX & #40; Transact-SQL & #41; ](../../t-sql/statements/create-index-transact-sql.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo di tipi definiti dall'utente in SQL Server](../../relational-databases/clr-integration-database-objects-user-defined-types/working-with-user-defined-types-in-sql-server.md)  
  
  
