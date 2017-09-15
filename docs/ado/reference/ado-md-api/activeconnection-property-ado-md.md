---
title: "Proprietà ActiveConnection (ADO MD) | Documenti Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- ActiveConnection
- Cellset::ActiveConnection
- Catalog::ActiveConnection
helpviewer_keywords:
- ActiveConnection property [ADO MD]
ms.assetid: 2509b32c-a995-4364-9152-d8c83129bdd8
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ae0ad910a0535599d7e134d3314030537068ab25
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="activeconnection-property-ado-md"></a>Proprietà ActiveConnection (ADO MD)
Indica a quale ADO [connessione](../../../ado/reference/ado-api/connection-object-ado.md) set di celle corrente dell'oggetto o catalogo a cui appartiene attualmente.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Restituisce o imposta un **Variant** che contiene una stringa che definisce una connessione o **connessione** oggetto. Il valore predefinito è vuoto.  
  
## <a name="remarks"></a>Osservazioni  
 È possibile impostare questa proprietà per un oggetto valido ADO **connessione** oggetto o a una stringa di connessione valida. Quando questa proprietà è impostata su una stringa di connessione, il provider crea un nuovo **connessione** utilizzando questa definizione dell'oggetto e viene aperta la connessione.  
  
 Se si utilizza il *ActiveConnection* argomento del [aprire](../../../ado/reference/ado-md-api/open-method-ado-md.md) per aprire un [set di celle](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) oggetto, il **ActiveConnection** proprietà ereditare il valore dell'argomento.  
  
 Impostazione di **ActiveConnection** proprietà di un [catalogo](../../../ado/reference/ado-md-api/catalog-object-ado-md.md) oggetto **nulla** rilascia i dati associati, inclusi i dati nel [CubeDefs](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md) raccolta e i relativi [dimensione](../../../ado/reference/ado-md-api/dimension-object-ado-md.md), [gerarchia](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md), [livello](../../../ado/reference/ado-md-api/level-object-ado-md.md), e [membro](../../../ado/reference/ado-md-api/member-object-ado-md.md) oggetti. La chiusura di un **connessione** oggetto utilizzato per aprire un **catalogo** ha lo stesso effetto dell'impostazione di **ActiveConnection** proprietà **nulla**.  
  
 Modifica il database predefinito della connessione a cui fa riferimento il **ActiveConnection** proprietà di un **catalogo** oggetto invalida il contenuto del **catalogo**.  
  
 Si verificherà un errore se si tenta di modificare il **ActiveConnection** proprietà per un oggetto aperto **set di celle** oggetto.  
  
> [!NOTE]
>  In Visual Basic, è necessario utilizzare il **impostare** (parola chiave) durante l'impostazione di **ActiveConnection** proprietà per un **connessione** oggetto. Se si omette il **impostare** (parola chiave), che sarà effettivamente impostato il **ActiveConnection** proprietà è uguale al **connessione** proprietà predefinita dell'oggetto, ** ConnectionString**. Il codice ne risulti; Tuttavia, si creerà una connessione aggiuntiva all'origine dati, che può avere implicazioni negative sulle prestazioni.  
  
 Quando si utilizza il provider di dati MSOLAP, impostare l'origine dati in una stringa di connessione a un nome di server e il catalogo iniziale per il nome di un catalogo dall'origine dati. Per connettersi a un file di cubo è disconnesso da un server, impostare il percorso per il percorso completo di. File CUB. In entrambi i casi, impostare il provider per il nome del provider. Ad esempio, la stringa seguente utilizza il Provider MSOLAP per la connessione a un catalogo denominato NomeComputer Video Store su un server denominato **Servername**:  
  
```  
"Data Source=Servername;Initial Catalog=Bobs Video Store;Provider=msolap"  
```  
  
 La stringa seguente si connette a un file di cubo locale nella posizione C:\MSDASDK\samples\oledb\olap\data\bobsvid.cub:  
  
```  
"Location=C:\MSDASDK\samples\oledb\olap\data\bobsvid.cub;Provider=msolap"  
```  
  
## <a name="applies-to"></a>Si applica a  
  
|||  
|-|-|  
|[Oggetto del catalogo (ADO MD)](../../../ado/reference/ado-md-api/catalog-object-ado-md.md)|[Oggetto Cellset (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di set di celle (VB)](../../../ado/reference/ado-md-api/cellset-example-vb.md)   
 [Oggetto di connessione (ADO.NET)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Open (metodo) (ADO MD)](../../../ado/reference/ado-md-api/open-method-ado-md.md)
