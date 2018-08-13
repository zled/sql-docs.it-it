---
title: Utilizzo di tipi di dati | Documenti di Microsoft
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: smo
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- DataType object
- SQL Server Management Objects, data types
- data types [SMO]
- SMO [SQL Server], data types
ms.assetid: 1e0e736a-c709-4d89-aeb2-b32dcfd641fa
caps.latest.revision: 45
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: b5523a2c6f0c05337eba4d6d0c4d27e7f6db58a4
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/06/2018
ms.locfileid: "39561571"
---
# <a name="working-with-data-types"></a>Utilizzo dei tipi di dati
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  I dati sono disponibili in diversi tipi e dimensioni, ad esempio una stringa con una lunghezza definita, un numero con una accuratezza specifica o un tipo di dati definito dall'utente che rappresenta un altro oggetto con un set di regole specifico. Il <xref:Microsoft.SqlServer.Management.Smo.DataType> oggetto classifica il tipo di dati in modo che possa essere gestito correttamente dal [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. L'oggetto <xref:Microsoft.SqlServer.Management.Smo.DataType> è associato a oggetti che accettano dati. Nell'esempio [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] oggetti Management Objects (SMO) accettano i dati che devono essere definiti da un <xref:Microsoft.SqlServer.Management.Smo.DataType> proprietà dell'oggetto:  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Column>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunctionParameter>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.StoredProcedureParameter>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunctionParameter>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.UserDefinedAggregateParameter>  
  
 La proprietà **DataType** per oggetti che accettano dati può essere impostata in diversi modi.  
  
-   Utilizzare il costruttore predefinito e specificare <xref:Microsoft.SqlServer.Management.Smo.DataType> proprietà dell'oggetto in modo esplicito  
  
-   Utilizzare un costruttore di overload e specificare la <xref:Microsoft.SqlServer.Management.Smo.DataType> proprietà come parametri.  
  
-   Specificare il <xref:Microsoft.SqlServer.Management.Smo.DataType> inline nel costruttore dell'oggetto.  
  
-   Usare uno dei membri statici della <xref:Microsoft.SqlServer.Management.Smo.DataType> classe, ad esempio **Int**. In questo modo verrà restituita un'istanza di un oggetto <xref:Microsoft.SqlServer.Management.Smo.DataType>.  
  
 L'oggetto <xref:Microsoft.SqlServer.Management.Smo.DataType> include diverse proprietà che definiscono il tipo di dati. La proprietà <xref:Microsoft.SqlServer.Management.Smo.SqlDataType> specifica, ad esempio, il tipo di dati [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Valori costanti che rappresentano [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sono elencati i tipi di dati di <xref:Microsoft.SqlServer.Management.Smo.SqlDataType> dell'enumerazione. Tale enumerazione si riferisce a tipi di dati quali **varchar**, **nchar**, **currency**, **integer**, **float**e **datetime**.  
  
 Quando viene stabilito il tipo di dati, è necessario impostare proprietà specifiche per i dati. Se, ad esempio, i dati sono di tipo **nchar** , è necessario impostare la lunghezza dei dati di stringa nella proprietà **Length** . La stessa operazione è richiesta anche nel caso dei valori numerici, per i quali è necessario specificare la precisione e la scala.  
  
 I tipi di dati <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType> e <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType> fanno riferimento agli oggetti contenenti la definizione de tipo di dati fornita dall'utente. <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType> si basa sui tipi di dati [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dell'enumerazione <xref:Microsoft.SqlServer.Management.Smo.SqlDataType>. Il <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType> si basa su [!INCLUDE[msCoName](../../../includes/msconame-md.md)] tipi di dati .NET. In genere, rappresentano dati di un tipo specifico riutilizzati di frequente dal database in base a regole business definite dall'organizzazione. Un tipo di dati che consente, ad esempio, di archiviare un importo e un denominatore di valuta risulterebbe utile in una società che gestisce più valute.  
  
 Il <xref:Microsoft.SqlServer.Management.Smo.SqlDataType> l'enumerazione contiene un elenco di tutti i [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-tipi di dati supportati.  
  
## <a name="examples"></a>Esempi  
Per usare qualsiasi esempio di codice fornito, è necessario scegliere l'ambiente di programmazione, il modello di programmazione e il linguaggio di programmazione per la creazione dell'applicazione. Per altre informazioni, vedere [creare un Visual C&#35; progetto SMO in Visual Studio .NET](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
  
## <a name="constructing-a-datatype-object-with-the-specification-in-the-constructor-in-visual-basic"></a>Costruzione di un oggetto DataType con la specifica nel costruttore di Visual Basic  
 Questo esempio di codice viene illustrato come utilizzare il costruttore per creare istanze di tipi di dati che si basano su diverse [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] i tipi di dati.  
  
> [!NOTE]  
>  I tipi <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>, <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType> e XML richiedono tutti un nome per identificare l'oggetto.  
  
```VBNET
'Declare a DataType object variable and define the data type in the constructor.
Dim dt As DataType
'For the decimal data type the following two arguements specify precision, and scale.
dt = New DataType(SqlDataType.Decimal, 10, 2)
``` 
  
## <a name="constructing-a-datatype-object-with-the-specification-in-the-constructor-in-visual-c"></a>Costruzione di un oggetto DataType con la specifica nel costruttore di Visual C#  
 Questo esempio di codice viene illustrato come utilizzare il costruttore per creare istanze di tipi di dati che si basano su diverse [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] i tipi di dati.  
  
> [!NOTE]  
>  I tipi <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>, <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType> e XML richiedono tutti un nome per identificare l'oggetto.  
  
```csharp  
{   
//Declare a DataType object variable and define the data type in the constructor.   
DataType dt;   
//For the decimal data type the following two arguements specify precision, and scale.   
dt = new DataType(SqlDataType.Decimal, 10, 2);   
}  
```  
  
## <a name="constructing-a-datatype-object-by-using-the-default-constructor-in-visual-basic"></a>Costruzione di un oggetto DataType mediante il costruttore predefinito di Visual Basic  
 Questo esempio di codice viene illustrato come utilizzare il costruttore predefinito per creare istanze di tipi di dati che si basano su diverse [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] i tipi di dati. Successivamente vengono utilizzate le proprietà per specificare il tipo di dati.  
  
 **Nota** di <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>, <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType>, e tutti i tipi XML richiedono un valore di nome per identificare l'oggetto.  
  
```VBNET
'Declare and create a DataType object variable.
Dim dt As DataType
dt = New DataType
'Define the data type by setting the SqlDataType property.
dt.SqlDataType = SqlDataType.VarChar
'The VarChar data type requires a value for the MaximumLength property.
dt.MaximumLength = 100
```
  
## <a name="constructing-a-datatype-object-by-using-the-default-constructor-in-visual-c"></a>Costruzione di un oggetto DataType mediante il costruttore predefinito di Visual C#  
 Questo esempio di codice viene illustrato come utilizzare il costruttore predefinito per creare istanze di tipi di dati che si basano su diverse [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] i tipi di dati. Successivamente vengono utilizzate le proprietà per specificare il tipo di dati.  
  
 **Nota** di <xref:Microsoft.SqlServer.Management.Smo.UserDefinedType>, <xref:Microsoft.SqlServer.Management.Smo.UserDefinedDataType>, e tutti i tipi XML richiedono un valore di nome per identificare l'oggetto.  
  
```csharp  
{   
//Declare and create a DataType object variable.   
DataType dt;   
dt = new DataType();   
//Define the data type by setting the SqlDataType property.   
dt.SqlDataType = SqlDataType.VarChar;   
//The VarChar data type requires a value for the MaximumLength property.   
dt.MaximumLength = 100;   
}  
```  
  
  
