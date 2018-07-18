---
title: Uso delle estensioni di Visual C++ | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Visual C++ [ADO], using VC++ extensions
- ADO, Visual C++
ms.assetid: ff759185-df41-4507-8d12-0921894ffbd9
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a1c832cff45ad5998918c6f5f67927e49bc9d4e9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="visual-c-extensions"></a>Estensioni di Visual C++
## <a name="the-iadorecordbinding-interface"></a>L'interfaccia IADORecordBinding
 Le estensioni di Microsoft Visual C++ per ADO associano, campi di un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto alle variabili di C/C++. Ogni volta che la riga corrente del limite della **Recordset** cambia, tutti i campi associati nel **Recordset** vengono copiate le variabili di C/C++. Se necessario, i dati copiati viene convertiti nel tipo di dati dichiarato della variabile C/C++.

 Il **BindToRecordset** metodo il **IADORecordBinding** interfaccia associa i campi a variabili C/C++. Il **AddNew** metodo aggiunge una nuova riga al limite **Recordset**. Il **aggiornamento** metodo popola i campi in nuove righe del **Recordset**, oppure aggiorna i campi nelle righe esistenti, con il valore delle variabili di C/C++.

 Il **IADORecordBinding** viene implementata mediante il **Recordset** oggetto. Non codificare l'implementazione.

## <a name="binding-entries"></a>Voci di associazione
 Estensioni di Visual C++ per ADO mappano i campi di un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto alle variabili di C/C++. La definizione di un mapping tra un campo e una variabile viene chiamata un *associazione voce*. Le macro includono voci di associazione per i dati numerici, a lunghezza fissa e a lunghezza variabile. Voci di associazione e le variabili di C/C++ vengono dichiarate in una classe derivata dalla classe di estensioni di Visual C++, **CADORecordBinding**. Il **CADORecordBinding** classe viene definita internamente dalle macro delle voci di associazione.

 ADO esegue il mapping internamente i parametri in queste macro per OLE DB **DBBINDING** struttura e crea OLE DB **della funzione di accesso** oggetto per gestire lo spostamento e la conversione dei dati tra campi e variabili. OLE DB definisce i dati come composti da tre parti: un *buffer* in cui sono archiviati i dati; un *stato* che indica se un campo è stato correttamente archiviato nel buffer o come la variabile deve essere ripristinata il campo. e *lunghezza* dei dati. (Vedere [Guida e l'impostazione dei dati (OLE DB)](http://msdn.microsoft.com/en-us/4369708b-c9fb-4d48-a321-bf949b41a369)in riferimento OLE DB Programmer, per ulteriori informazioni.)

## <a name="header-file"></a>File di intestazione
 Nell'applicazione per utilizzare le estensioni di Visual C++ per ADO, includere il file seguente:

```
#include <icrsint.h>
```

## <a name="binding-recordset-fields"></a>Campi del Recordset associazione

#### <a name="to-bind-recordset-fields-to-cc-variables"></a>Per associare i campi del Recordset a variabili di C/C++

1.  Creare una classe derivata dal **CADORecordBinding** classe.

2.  Specificare le voci di associazione e le variabili di C/C++ corrispondente nella classe derivata. Le voci di associazione tra parentesi **le macro BEGIN_ADO_BINDING** e **END_ADO_BINDING** macro. Non terminare le macro con virgole o punti e virgola. Delimitatori appropriati vengono specificati automaticamente per ogni macro.

     Specificare una voce di associazione per ogni campo di cui eseguire il mapping a una variabile di C/C++. Un membro appropriato da utilizzare il **ADO_FIXED_LENGTH_ENTRY**, **ADO_NUMERIC_ENTRY**, o **ADO_VARIABLE_LENGTH_ENTRY** famiglia di macro.

3.  Nell'applicazione, creare un'istanza della classe derivata da **CADORecordBinding**. Ottenere il **IADORecordBinding** interfaccia dal **Recordset**. Chiamare quindi il **BindToRecordset** metodo a cui associare il **Recordset** i campi per le variabili di C/C++.

 Per ulteriori informazioni, vedere il [esempio di estensioni di Visual C++](../../../ado/guide/appendixes/visual-c-extensions-example.md).

## <a name="interface-methods"></a>Metodi di interfaccia
 Il **IADORecordBinding** interfaccia dispone di tre metodi: **BindToRecordset**, **AddNew**, e **aggiornamento**. L'unico argomento per ogni metodo è un puntatore a un'istanza della classe derivata da **CADORecordBinding**. Pertanto, il **AddNew** e **aggiornamento** metodi non possono specificare i parametri dei relativi omonimi ADO.

## <a name="syntax"></a>Sintassi
 Il **BindToRecordset** metodo associa la **Recordset** campi con le variabili di C/C++.

```
BindToRecordset(CADORecordBinding *binding)
```

 Il **AddNew** metodo richiama il relativo omonimo, ADO [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md) metodo per aggiungere una nuova riga per il **Recordset**.

```
AddNew(CADORecordBinding *binding)
```

 Il **aggiornare** metodo richiama il relativo omonimo, ADO [aggiornare](../../../ado/reference/ado-api/update-method.md) (metodo), per aggiornare il **Recordset**.

```
Update(CADORecordBinding *binding)
```

## <a name="binding-entry-macros"></a>Macro di voci di associazione
 Macro di voci di associazione definiscono un'associazione di un **Recordset** campo e una variabile. Una macro di inizio e fine delimita il set di voci di associazione.

 Le famiglie di macro sono disponibili per i dati a lunghezza fissa, ad esempio **adDate** o **adBoolean**; numerico dati, ad esempio **adTinyInt**, **tutti**, o **adDouble**; e i dati a lunghezza variabile, ad esempio **famiglia**, **adVarChar** o **adVarBinary**. Tutti i tipi numerici, ad eccezione di **adVarNumeric**, sono anche tipi a lunghezza fissa. Ogni gruppo include set diversi di parametri in modo che sia possibile escludere le informazioni di associazione di alcun interesse.

 Per ulteriori informazioni, vedere [appendice a: tipi di dati](http://msdn.microsoft.com/en-us/e3a0533a-2196-4eb0-a31e-92fe9556ada6), di riferimento di OLE DB Programmer.

### <a name="begin-binding-entries"></a>Voci di associazione iniziali
 **Le macro BEGIN_ADO_BINDING**(*classe*)

### <a name="fixed-length-data"></a>Dati a lunghezza fissa
 **ADO_FIXED_LENGTH_ENTRY**(*ordinale, tipo di dati, Buffer, stato, modificare*)

 **ADO_FIXED_LENGTH_ENTRY2**(*ordinale, tipo di dati, del Buffer, modificare*)

### <a name="numeric-data"></a>Dati numerici
 **ADO_NUMERIC_ENTRY**(*ordinale, tipo di dati, Buffer, precisione, scala, stato, modificare*)

 **ADO_NUMERIC_ENTRY2**(*ordinale, tipo di dati, Buffer, precisione, scala, modificare*)

### <a name="variable-length-data"></a>Dati a lunghezza variabile
 **ADO_VARIABLE_LENGTH_ENTRY**(*ordinale, tipo di dati, Buffer, le dimensioni, lo stato, lunghezza, modificare*)

 **ADO_VARIABLE_LENGTH_ENTRY2**(*ordinale, tipo di dati, Buffer, le dimensioni, lo stato, modificare*)

 **ADO_VARIABLE_LENGTH_ENTRY3**(*ordinale, tipo di dati, Buffer, le dimensioni, lunghezza, modificare*)

 **ADO_VARIABLE_LENGTH_ENTRY4**(*ordinale, tipo di dati, Buffer, dimensioni, modificare*)

### <a name="end-binding-entries"></a>Associazione di voci finali
 **END_ADO_BINDING**()

|Parametro|Description|
|---------------|-----------------|
|*Classe*|Classe in cui vengono definite voci di associazione e le variabili di C/C++.|
|*Ordinal*|Numero ordinale, a partire da uno, del **Recordset** campo corrispondente alla variabile di C/C++.|
|*DataType*|Tipo di dati ADO equivalente della variabile C/C++ (vedere [DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md) per un elenco di tipi di dati validi). Il valore di **Recordset** campo verrà convertito in questo tipo di dati se necessario.|
|*Buffer*|Nome della variabile C/C++ in cui il **Recordset** campo verrà archiviato.|
|*Dimensione*|Dimensione massima in byte di *Buffer*. Se *Buffer* conterrà una stringa di lunghezza variabile, consentire spazio per un terminazione zero.|
|*Stato*|Nome di una variabile che indica se il contenuto di *Buffer* validi e se la conversione del campo da *DataType* ha avuto esito positivo.<br /><br /> I due valori più importanti per questa variabile sono **adFldOK**, ovvero la conversione ha avuto esito positivo; e **adFldNull**, ovvero il valore del campo è una variante del tipo VT_NULL e non semplicemente vuoto.<br /><br /> I valori possibili per *stato* sono elencati nella tabella seguente, "Valori di Status".|
|*Modificare*|Flag booleano. Se TRUE, indica ad ADO è consentito aggiornare corrispondente **Recordset** campo con il valore contenuto in *Buffer*.<br /><br /> Impostare il valore booleano *modificare* parametro su TRUE per abilitare ADO aggiornare il campo associato e FALSE se si desidera esaminare il campo, ma non modificarlo.|
|*Precisione*|Numero di cifre che può essere rappresentato in una variabile numerica.|
|*Scala*|Numero di posizioni decimali in una variabile numerica.|
|*Length*|Nome di una variabile a quattro byte che contiene la lunghezza effettiva dei dati in *Buffer*.|

## <a name="status-values"></a>Valori di stato
 Il valore di *stato* variabile indica se un campo è stato copiato correttamente a una variabile.

 Durante l'impostazione di dati, *stato* può essere impostata su **adFldNull** per indicare il **Recordset** campo deve essere impostato su null.

|Costante|Value|Description|
|--------------|-----------|-----------------|
|**adFldOK**|0|È stato restituito un valore di campo non null.|
|**adFldBadAccessor**|1|Associazione non è valida.|
|**adFldCantConvertValue**|2|Valore non è stato convertito per ragioni diverse da overflow di dati o non corrispondenza del segno.|
|**adFldNull**|3|Quando si recupera un campo, indica che è stato restituito un valore null.<br /><br /> Quando si imposta un campo, indica il campo deve essere impostato su **NULL** quando il campo è possibile codificare **NULL** stesso (ad esempio, una matrice di caratteri o un numero intero).|
|**adFldTruncated**|4|Dati a lunghezza variabile o valori numerici sono stati troncati.|
|**adFldSignMismatch**|5|Valore viene firmato e il tipo di dati della variabile è senza segno.|
|**adFldDataOverFlow**|6|Il valore è maggiore di può essere archiviata nel tipo di dati della variabile.|
|**adFldCantCreate**|7|Tipo di colonna sconosciuto e il campo è già aperta.|
|**adFldUnavailable**|8|Valore di campo non può essere determinato, ad esempio, in un nuovo campo non assegnato non prevede alcun valore predefinito.|
|**adFldPermissionDenied**|9|Durante l'aggiornamento, nessuna autorizzazione per scrivere i dati.|
|**adFldIntegrityViolation**|10|Durante l'aggiornamento, il valore del campo violerebbe integrità della colonna.|
|**adFldSchemaViolation**|11|Durante l'aggiornamento, il valore del campo violerebbe schema di colonne.|
|**adFldBadStatus**|12|Durante l'aggiornamento, il parametro di stato non valido.|
|**adFldDefault**|13|Durante l'aggiornamento, è stato usato un valore predefinito.|

## <a name="see-also"></a>Vedere anche
 [Esempio di estensioni di Visual C++](../../../ado/guide/appendixes/visual-c-extensions-example.md) [intestazione delle estensioni di Visual C++](../../../ado/guide/appendixes/visual-c-extensions-header.md)
