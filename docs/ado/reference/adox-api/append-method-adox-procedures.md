---
title: Append (metodo) (procedure ADOX) | Documenti Microsoft
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
- Procedures::Append
- Procedures::raw_Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: 38e3492c-c1e1-42e3-a71a-befdc90204db
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 679f7691a8f93026ce1f6a68ea232d01818e6dc9
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="append-method-adox-procedures"></a>Append (metodo) (ADOX procedure)
Aggiunge un nuovo [procedura](../../../ado/reference/adox-api/procedure-object-adox.md) dell'oggetto per il [procedure](../../../ado/reference/adox-api/procedures-collection-adox.md) insieme.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Procedures.Append Name, Command  
```  
  
#### <a name="parameters"></a>Parametri  
 *Nome*  
 Oggetto **stringa** valore che specifica il nome della procedura per creare e accodare.  
  
 *Command*  
 Un oggetto ADO [comando](../../../ado/reference/ado-api/command-object-ado.md) oggetto che rappresenta la procedura per creare e aggiungere.  
  
## <a name="remarks"></a>Osservazioni  
 Crea una nuova stored procedure nell'origine dati con il nome e gli attributi specificati nel **comando** oggetto.  
  
 Se il testo del comando specificato dall'utente rappresenta una vista piuttosto che una stored procedure, il comportamento è dipende dal provider in uso. **Aggiungere** avrà esito negativo se il provider non supporta i comandi di persistenza.  
  
> [!NOTE]
>  Quando si utilizza il Provider OLE DB per Microsoft Jet, la **procedure** raccolta **Append** metodo consente di specificare un **vista** piuttosto che un  **Procedura** nel *comando* parametro. Il **vista** verrà aggiunto all'origine dati e verrà aggiunto al **procedure** insieme. Dopo il **Append**, se il **procedure** e **viste** raccolte vengono aggiornate, il **visualizzazione** non sarà più possibile nel **Procedure** insieme e verranno visualizzati di **viste** insieme.  
  
## <a name="applies-to"></a>Si applica a  
 [Raccolta di procedure (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Procedure di esempio del metodo Append (VB)](../../../ado/reference/adox-api/procedures-append-method-example-vb.md)   
 [Append (metodo) (ADOX colonne)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append (metodo) (ADOX gruppi)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append (metodo) (ADOX indici)](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Append (metodo) (ADOX chiavi)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Append (metodo) (ADOX tabelle)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Append (metodo) (ADOX utenti)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Append (metodo) (ADOX Views)](../../../ado/reference/adox-api/append-method-adox-views.md)

