---
title: "Proprietà CommandText (ADO) | Documenti Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords: Command15::CommandText
helpviewer_keywords: CommandText property [ADO]
ms.assetid: 4dd7e82a-8da5-4a4e-b439-11a29286fa0e
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e67ea9d0a7d34477a73c09c99689e0c953f4b905
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="commandtext-property-ado"></a>Proprietà CommandText (ADO)
Indica il testo di un comando per essere eseguito in base a un provider.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Ottiene o imposta un **stringa** valore che contiene un comando del provider, ad esempio un'istruzione SQL, un nome di tabella, un URL relativo o chiamata di stored procedure. Il valore predefinito è una stringa vuota ("").  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il **CommandText** proprietà per impostare o restituire il testo di un comando rappresentato da un [comando](../../../ado/reference/ado-api/command-object-ado.md) oggetto. In genere questo sarà un'istruzione SQL, ma può anche essere di qualsiasi altro tipo di istruzione di comando riconosciuto dal provider, ad esempio una chiamata di stored procedure. Un'istruzione SQL deve essere del sottolinguaggio specifico o una versione supportata dal processore di query del provider.  
  
 Se il [Prepared](../../../ado/reference/ado-api/prepared-property-ado.md) proprietà del **comando** oggetto è impostato su **True** e **comando** oggetto è associato a una connessione aperta quando si imposta il **CommandText** proprietà ADO prepara la query (ovvero, un modulo compilato della query che vengono archiviati dal provider) quando si chiama il [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md) o [aprire](../../../ado/reference/ado-api/open-method-ado-connection.md)metodi.  
  
 A seconda di [CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md) , impostazione della proprietà ADO può modificare il **CommandText** proprietà. È possibile leggere il **CommandText** proprietà in qualsiasi momento per visualizzare il testo del comando effettivo che ADO verrà utilizzata durante l'esecuzione.  
  
 Utilizzare il **CommandText** proprietà per impostare o restituire un URL relativo che specifica una risorsa, ad esempio un file o directory. La risorsa è relativo alla posizione specificata in modo esplicito da un URL assoluto o in modo implicito da open [connessione](../../../ado/reference/ado-api/connection-object-ado.md) oggetto.  
  
> [!NOTE]
>  Gli URL che utilizzano lo schema http richiamerà automaticamente il [il Provider Microsoft OLE DB per Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Per ulteriori informazioni, vedere [URL assoluti e relativi](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà direzione (VB), CommandText, CommandTimeout, CommandType, dimensioni e ActiveConnection](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [Esempio di proprietà direzione (VC + +), CommandText, CommandTimeout, CommandType, dimensioni e ActiveConnection](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [Requery (metodo)](../../../ado/reference/ado-api/requery-method.md)   
 [ActiveConnection, CommandText, CommandTimeout, CommandType, dimensioni e direzione proprietà esempio (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)
