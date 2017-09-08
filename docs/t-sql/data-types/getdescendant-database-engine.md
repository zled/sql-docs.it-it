---
title: GetDescendant (motore di Database) | Documenti Microsoft
ms.custom: 
ms.date: 07/22/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- GetDescendant_TSQL
- GetDescendant
dev_langs:
- TSQL
helpviewer_keywords:
- GetDescendant [Database Engine]
ms.assetid: f5f39596-033e-4243-acbc-caa188b45b03
caps.latest.revision: 23
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ced4a5518ce7d58785a1d2954c4f131b66a5ddb0
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="getdescendant-database-engine"></a>GetDescendant (Motore di database)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Restituisce il nodo figlio di un nodo padre.
  
## <a name="syntax"></a>Sintassi  
  
```sql
-- Transact-SQL syntax  
parent.GetDescendant ( child1 , child2 )   
```  
  
```sql
-- CLR syntax  
SqlHierarchyId GetDescendant ( SqlHierarchyId child1 , SqlHierarchyId child2 )   
```  
  
## <a name="arguments"></a>Argomenti  
*child1*  
NULL o **hierarchyid** di un elemento figlio del nodo corrente.
  
*Child2*  
NULL o **hierarchyid** di un elemento figlio del nodo corrente.
  
## <a name="return-types"></a>Tipi restituiti  
**Tipo: hierarchyid restituito SQL Server**
  
**Tipo CLR restituito: SqlHierarchyId**
  
## <a name="remarks"></a>Osservazioni  
Restituisce un nodo figlio discendente del padre.
-   Se il padre è Null, restituisce Null.  
-   Se il padre è diverso da Null e child1 e child2 sono Null, restituisce un figlio del padre.  
-   Se il padre e child1 sono diversi da Null e child2 è NULL, restituisce un figlio del padre maggiore di child1.  
-   Se il padre e child2 sono diversi da Null e child1 è Null, restituisce un figlio del padre minore di child2.  
-   Se il padre, child1 e child2 sono diversi da Null, restituisce un figlio del padre maggiore di child1 e minore di child2.  
-   Se child1 è diverso da Null, ma non è un figlio del padre, viene generata un'eccezione.  
-   Se child2 è diverso da Null, ma non è un figlio del padre, viene generata un'eccezione.  
-   Se child1 >= child2, viene generata un'eccezione.  
  
GetDescendant è deterministica. Pertanto, se GetDescendant viene chiamato con gli stessi input, verrà sempre generato lo stesso output. L'identità esatta del figlio restituito può tuttavia variare in base alla relazione con gli altri nodi, come dimostrato nell'esempio C.
  
## <a name="examples"></a>Esempi  
  
### <a name="a-inserting-a-row-as-the-least-descendant-node"></a>A. Inserimento di una riga come ultimo nodo discendente  
Viene assunto un nuovo dipendente, messo in relazione con un dipendente esistente nel nodo `/3/1/`. Eseguire il codice seguente per inserire una nuova riga utilizzando il metodo GetDescendant senza argomenti per specificare il nuovo nodo di righe come `/3/1/1/`:
  
```sql
DECLARE @Manager hierarchyid;   
SET @Manager = CAST('/3/1/' AS hierarchyid);  
  
INSERT HumanResources.EmployeeDemo (OrgNode, LoginID, Title, HireDate)  
VALUES  
(@Manager.GetDescendant(NULL, NULL),  
'adventure-works\FirstNewEmployee', 'Application Intern', '3/11/07') ;  
```  
  
### <a name="b-inserting-a-row-as-a-greater-descendant-node"></a>B. Inserimento di una riga come nodo discendente maggiore  
Viene assunto un altro nuovo dipendente, creazione di report per lo stesso responsabile dell'esempio A. eseguire il codice seguente per inserire una nuova riga utilizzando il metodo GetDescendant utilizzando l'argomento child1 per specificare che il nodo della nuova riga seguirà il nodo dell'esempio , diventando `/3/1/2/`:
  
```sql
DECLARE @Manager hierarchyid, @Child1 hierarchyid;  
  
SET @Manager = CAST('/3/1/' AS hierarchyid);  
SET @Child1 = CAST('/3/1/1/' AS hierarchyid);  
  
INSERT HumanResources.EmployeeDemo (OrgNode, LoginID, Title, HireDate)  
VALUES  
(@Manager.GetDescendant(@Child1, NULL),  
'adventure-works\SecondNewEmployee', 'Application Intern', '3/11/07') ;  
```  
  
### <a name="c-inserting-a-row-between-two-existing-nodes"></a>C. Inserimento di una riga tra due nodi esistenti  
Viene assunto un terzo dipendente, lo stesso responsabile dell'esempio A. creazione di report Questo esempio viene inserita la nuova riga in un nodo maggiore di `FirstNewEmployee` dell'esempio A e minore di `SecondNewEmployee` nell'esempio B. esecuzione di codice seguente tramite il metodo GetDescendant. Utilizzare sia l'argomento child1 che l'argomento child2 per specificare che il nodo della nuova riga diventerà il nodo `/3/1/1.1/`:
  
```sql
DECLARE @Manager hierarchyid, @Child1 hierarchyid, @Child2 hierarchyid;  
  
SET @Manager = CAST('/3/1/' AS hierarchyid);  
SET @Child1 = CAST('/3/1/1/' AS hierarchyid);  
SET @Child2 = CAST('/3/1/2/' AS hierarchyid);  
  
INSERT HumanResources.EmployeeDemo (OrgNode, LoginID, Title, HireDate)  
VALUES  
(@Manager.GetDescendant(@Child1, @Child2),  
'adventure-works\ThirdNewEmployee', 'Application Intern', '3/11/07') ;  
  
```  
  
Dopo aver completato gli esempi A, B e C, i nodi aggiunti alla tabella sarà peer con il codice seguente **hierarchyid** valori:
  
`/3/1/1/`
  
`/3/1/1.1/`
  
`/3/1/2/`
  
Il nodo `/3/1/1.1/` è maggiore del nodo `/3/1/1/`, ma si trova allo stesso livello della gerarchia.
  
### <a name="d-scalar-examples"></a>D. Esempi scalari  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]supporta eliminazioni di qualsiasi e inserimenti arbitrari **hierarchyid** nodi. Utilizzando GetDescendant (), è sempre possibile generare un nodo tra due **hierarchyid** nodi. Eseguire il codice seguente per generare nodi di esempio utilizzando `GetDescendant`:
  
```sql
DECLARE @h hierarchyid = hierarchyid::GetRoot();  
DECLARE @c hierarchyid = @h.GetDescendant(NULL, NULL);  
SELECT @c.ToString();  
DECLARE @c2 hierarchyid = @h.GetDescendant(@c, NULL);  
SELECT @c2.ToString();  
SET @c2 = @h.GetDescendant(@c, @c2);  
SELECT @c2.ToString();  
SET @c = @h.GetDescendant(@c, @c2);  
SELECT @c.ToString();  
SET @c2 = @h.GetDescendant(@c, @c2);  
SELECT @c2.ToString();  
```  
  
### <a name="e-clr-example"></a>E. Esempio CLR  
Nel frammento di codice seguente viene chiamato il metodo `GetDescendant()`.
  
```sql
SqlHierarchyId parent, child1, child2;  
parent = SqlHierarchyId.GetRoot();  
child1 = parent.GetDescendant(SqlHierarchyId.Null, SqlHierarchyId.Null);  
child2 = parent.GetDescendant(child1, SqlHierarchyId.Null);  
Console.Write(parent.GetDescendant(child1, child2).ToString());  
```  
  
## <a name="see-also"></a>Vedere anche
[Guida di riferimento ai metodi per il tipo di dati hierarchyid](http://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)  
[Dati gerarchici &#40;SQL Server&#41;](../../relational-databases/hierarchical-data-sql-server.md)  
[hierarchyid &#40;Transact-SQL&#41;](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)
  
  

