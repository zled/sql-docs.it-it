---
title: Raccolta di parametri (ADO) | Documenti Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command15::get_Parameters
- Command15::Parameters
- Command15::GetParameters
helpviewer_keywords:
- Parameters collection [ADO]
ms.assetid: 497cae10-3913-422a-9753-dcbb0a639b1b
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: e6557489b5051a7d92864b662b1822b9e6d0dff4
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="parameters-collection-ado"></a>Raccolta di parametri (ADO)
Contiene tutti i [parametro](../../../ado/reference/ado-api/parameter-object.md) gli oggetti di un [comando](../../../ado/reference/ado-api/command-object-ado.md) oggetto.  
  
## <a name="remarks"></a>Osservazioni  
 Oggetto **comando** oggetto ha un **parametri** raccolta costituita da **parametro** oggetti.  
  
 Utilizzando il [aggiornamento](../../../ado/reference/ado-api/refresh-method-ado.md) metodo su un **comando** dell'oggetto **parametri** insieme recupera informazioni sui parametri di provider per la stored procedure o query con parametri specificato nella **comando** oggetto. Alcuni provider non supporta chiamate di stored procedure o query con parametri. chiamata di **aggiornare** metodo il **parametri** raccolta quando si utilizza un provider di questo tipo verrà restituito un errore.  
  
 Se non è stata definita la propria **parametro** oggetti e si accede di **parametri** raccolta prima di chiamare il **aggiornare** metodo, verrà automaticamente chiamato il metodo e popolare la raccolta per l'utente.  
  
 È possibile ridurre le chiamate al provider per migliorare le prestazioni se si conosce le proprietà dei parametri associati con la stored procedure o query con parametri che si desidera chiamare. Utilizzare il [CreateParameter](../../../ado/reference/ado-api/createparameter-method-ado.md) metodo per creare **parametro** oggetti con le impostazioni di proprietà appropriato e l'utilizzo di [Append](../../../ado/reference/ado-api/append-method-ado.md) metodo per aggiungerli al  **I parametri** insieme. Consente di impostare e restituire i valori dei parametri senza la necessità di chiamare il provider per le informazioni sui parametri. Se si sta scrivendo su un provider che non fornisce informazioni sui parametri, è necessario popolare manualmente le **parametri** insieme utilizzando questo metodo per essere in grado di utilizzare i parametri. Utilizzare il [eliminare](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md) metodo per rimuovere **parametro** oggetti dal **parametri** raccolta, se necessario.  
  
 Gli oggetti il **parametri** raccolta di un **Recordset** andare fuori ambito (pertanto diventi non disponibile) quando il **Recordset** viene chiuso.  
  
 Quando si chiama una stored procedure con **comando**, il parametro di valore restituito/output di una stored procedure viene recuperato come indicato di seguito:  
  
1.  Quando si chiama una stored procedure che non ha alcun parametro, il **aggiornare** metodo il **parametri** raccolta deve essere chiamata prima di chiamare il **Execute** metodo il **Comando** oggetto.  
  
2.  Quando si chiama una stored procedure con parametri e l'aggiunta in modo esplicito un parametro per il **parametri** insieme con **Append**, il parametro di valore restituito/output deve essere aggiunti al **Parametri** insieme. Il valore restituito deve essere aggiunto prima per il **parametri** insieme. Utilizzare **Append** per aggiungere gli altri parametri in di **parametri** insieme nell'ordine di definizione. Ad esempio, la stored procedure SPWithParam include due parametri. Il primo parametro, *InParam*, è un parametro di input definiti come adVarChar (20) e il secondo parametro, *OutParam*, è un parametro di output definito come adVarChar (20). È possibile recuperare il parametro di valore restituito/output con il codice seguente.  
  
    ```  
    ' Open Connection Conn  
    set ccmd = CreateObject("ADODB.Command")  
    ccmd.Activeconnection= Conn  
  
    ccmd.CommandText="SPWithParam"  
    ccmd.commandType = 4 'adCmdStoredProc  
  
    ccmd.parameters.Append ccmd.CreateParameter(, adInteger, adParamReturnValue, , NULL)   ' return value  
    ccmd.parameters.Append ccmd.CreateParameter("InParam", adVarChar, adParamInput, 20, "hello world")   ' input parameter  
    ccmd.parameters.Append ccmd.CreateParameter("OutParam", adVarChar, adParamOuput, 20, NULL)   ' output parameter  
  
    ccmd.execute()  
  
    ' Access ccmd.parameters(0) as return value of this stored procedure  
    ' Access ccmd.parameters("OutParam") as the output parameter of this stored procedure.  
  
    ```  
  
3.  Quando si chiama una stored procedure con parametri e i parametri di configurazione tramite la chiamata di **elemento** metodo il **parametri** raccolta, il parametro di valore restituito/output della stored procedure può essere recuperati i **parametri** insieme. Ad esempio, la stored procedure SPWithParam include due parametri. Il primo parametro, *InParam*, è un parametro di input definiti come adVarChar (20) e il secondo parametro, *OutParam*, è un parametro di output definito come adVarChar (20). È possibile recuperare il parametro di valore restituito/output con il codice seguente.  
  
    ```  
    ' Open Connection Conn  
    set ccmd = CreateObject("ADODB.Command")  
    ccmd.Activeconnection= Conn  
  
    ccmd.CommandText="SPWithParam"  
    ccmd.commandType = 4 'adCmdStoredProc  
  
    ccmd.parameters.Item("InParam").value = "hello world" ' input parameter  
    ccmd.execute()  
  
    ' Access ccmd.parameters(0) as return value of stored procedure  
    ' Access ccmd.parameters(2) or ccmd.parameters("OutParam") as the output parameter.  
    ```  
  
 In questa sezione contiene l'argomento seguente.  
  
-   [Proprietà di raccolta dei parametri, metodi ed eventi](../../../ado/reference/ado-api/parameters-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Append (metodo) (ADO)](../../../ado/reference/ado-api/append-method-ado.md)   
 [Metodo CreateParameter (ADO)](../../../ado/reference/ado-api/createparameter-method-ado.md)   
 [Oggetto Parameter](../../../ado/reference/ado-api/parameter-object.md)
