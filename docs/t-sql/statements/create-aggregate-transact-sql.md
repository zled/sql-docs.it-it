---
title: CREATE AGGREGATE (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE_AGGREGATE_TSQL
- CREATE AGGREGATE
- AGGREGATE_TSQL
- AGGREGATE
dev_langs:
- TSQL
helpviewer_keywords:
- CREATE AGGREGATE statement
- aggregate functions [SQL Server], user-defined
- user-defined functions [CLR integration]
ms.assetid: 62eebc19-9f15-4245-94fa-b3fcd64a9d42
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 07509e36b76aad995297cfae0147df7e8db41c20
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="create-aggregate-transact-sql"></a>CREATE AGGREGATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Crea una funzione di aggregazione definita dall'utente la cui implementazione è definita in una classe di un assembly in [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]. Affinché in [!INCLUDE[ssDE](../../includes/ssde-md.md)] la funzione di aggregazione venga associata alla relativa implementazione, l'assembly [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] che include l'implementazione deve innanzitutto essere caricato in un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tramite un'istruzione CREATE ASSEMBLY.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
CREATE AGGREGATE [ schema_name . ] aggregate_name  
        (@param_name <input_sqltype>   
        [ ,...n ] )  
RETURNS <return_sqltype>  
EXTERNAL NAME assembly_name [ .class_name ]  
  
<input_sqltype> ::=  
        system_scalar_type | { [ udt_schema_name. ] udt_type_name }  
  
<return_sqltype> ::=  
        system_scalar_type | { [ udt_schema_name. ] udt_type_name }  
  
```  
  
## <a name="arguments"></a>Argomenti  
 *schema_name*  
 Nome dello schema a cui appartiene la funzione di aggregazione definita dall'utente.  
  
 *aggregate_name*  
 Nome della funzione di aggregazione che si desidera creare.  
  
 **@***nome_parametro*  
 Uno o più parametri della funzione di aggregazione definita dall'utente. Il valore di un parametro deve essere fornito dall'utente quando la funzione di aggregazione viene eseguita. Specificare un nome di parametro con un simbolo "at" (**@**) come primo carattere. Il nome del parametro deve essere conforme alle regole per [identificatori](../../relational-databases/databases/database-identifiers.md). I parametri sono locali rispetto alla funzione.  
  
 *system_scalar_type*  
 Qualsiasi tipo di dati scalare di sistema di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per la memorizzazione del valore del parametro di input o del valore restituito. Tutti i tipi di dati scalare utilizzabile come parametro per una funzione di aggregazione definita dall'utente, ad eccezione di **testo**, **ntext**, e **immagine**. Tipi di dati non scalari, ad esempio **cursore** e **tabella**, non può essere specificato.  
  
 *udt_schema_name*  
 Nome dello schema a cui appartiene il tipo CLR definito dall'utente. Se non specificato, il [!INCLUDE[ssDE](../../includes/ssde-md.md)] riferimenti *udt_type_name* nell'ordine seguente:  
  
-   Spazio dei nomi del tipo SQL nativo.  
  
-   Schema predefinito dell'utente corrente nel database corrente.  
  
-   Schema **dbo** nel database corrente.  
  
 *udt_type_name*  
 Nome di un tipo CLR definito dall'utente già creato nel database corrente. Se *udt_schema_name* non viene specificato, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] si presuppone che il tipo appartenga allo schema dell'utente corrente.  
  
 *nome_assembly* [**. * * * class_name* ]  
 Specifica l'assembly da associare alla funzione di aggregazione definita dall'utente e, facoltativamente, il nome dello schema a cui l'assembly appartiene e il nome della classe nell'assembly che implementa la funzione di aggregazione definita dall'utente. È necessario che l'assembly sia già stato creato nel database tramite un'istruzione CREATE ASSEMBLY. *CLASS_NAME* deve essere un valore valido [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] identificatore e corrispondere al nome di una classe esistente nell'assembly. *CLASS_NAME* può essere un nome completo dello spazio dei nomi se il linguaggio di programmazione utilizzato per scrivere la classe utilizza spazi dei nomi, ad esempio c#. Se *class_name* non viene specificato, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] si presuppone che sia identico *aggregate_name*.  
  
## <a name="remarks"></a>Osservazioni  
 Per impostazione predefinita, la capacità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di eseguire il codice CLR è disattivata. È possibile creare, modificare e rilasciare gli oggetti di database che fanno riferimento a moduli di codice gestito, ma il codice in questi moduli non verrà eseguito in un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , a meno che il [opzione clr enabled](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md) abilitata utilizzando [sp _ configurare](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md).  
  
 La classe dell'assembly a cui fa riferimento *nome_assembly* e i relativi metodi devono soddisfare tutti i requisiti per l'implementazione di una funzione di aggregazione definita dall'utente in un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per ulteriori informazioni, vedere [aggregazioni CLR definite dall'utente](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md).  
  
## <a name="permissions"></a>Autorizzazioni  
 È necessario disporre dell'autorizzazione CREATE AGGREGATE e anche dell'autorizzazione REFERENCES per l'assembly specificato nella clausola EXTERNAL NAME.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente si presuppone che sia stata compilata l'applicazione di esempio StringUtilities.csproj. Per ulteriori informazioni, vedere [esempio funzioni di stringa dell'utilità](http://msdn.microsoft.com/library/9623013f-15f1-4614-8dac-1155e57c880c).  
  
 Nell'esempio viene creata la funzione di aggregazione `Concatenate`, ma prima che venga effettivamente creata la funzione di aggregazione, l'assembly `StringUtilities.dll` viene registrato nel database locale.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @SamplesPath nvarchar(1024)  
-- You may have to modify the value of the this variable if you have  
--installed the sample some location other than the default location.  
  
SELECT @SamplesPath = REPLACE(physical_name, 'Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\DATA\master.mdf', 'Microsoft SQL Server\130\Samples\Engine\Programmability\CLR\')   
     FROM master.sys.database_files   
     WHERE name = 'master';  
  
CREATE ASSEMBLY StringUtilities FROM @SamplesPath + 'StringUtilities\CS\StringUtilities\bin\debug\StringUtilities.dll'  
WITH PERMISSION_SET=SAFE;  
GO  
  
CREATE AGGREGATE Concatenate(@input nvarchar(4000))  
RETURNS nvarchar(4000)  
EXTERNAL NAME [StringUtilities].[Microsoft.Samples.SqlServer.Concatenate];  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [DROP AGGREGATE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-aggregate-transact-sql.md)  
  
  
