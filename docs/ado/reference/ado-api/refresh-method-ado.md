---
title: Metodo Refresh (ADO) | Documenti Microsoft
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
- _Collection::Refresh
- Parameters::Refresh
- Properties::Refresh
helpviewer_keywords:
- Refresh method [ADO]
ms.assetid: 089b7ca7-684f-4259-8032-5bd1ecc54426
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 00a739b4bf90651f1e38402a8309482bf8217680
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="refresh-method-ado"></a>Metodo Refresh (ADO)
Aggiorna gli oggetti in una raccolta in modo da riflettere gli oggetti disponibili e specifiche del provider.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
collection.Refresh  
```  
  
## <a name="remarks"></a>Osservazioni  
 Il **aggiornamento** metodo esegue attività diverse a seconda della raccolta da cui è possibile chiamare.  
  
### <a name="parameters"></a>Parametri  
 Utilizzando il **aggiornamento** metodo il [parametri](../../../ado/reference/ado-api/parameters-collection-ado.md) raccolta di un [comando](../../../ado/reference/ado-api/command-object-ado.md) oggetto recupera le informazioni di parametro lato provider per la stored procedure o query con parametri specificata nel **comando** oggetto. La raccolta sarà vuota per i provider che non supportano chiamate di stored procedure o query con parametri.  
  
 È necessario impostare il [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) proprietà del **comando** oggetto su un valore valido [connessione](../../../ado/reference/ado-api/connection-object-ado.md) oggetto, il [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) proprietà per un comando valido e [CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md) proprietà **adCmdStoredProc** prima di chiamare il **aggiornare** metodo.  
  
 Se si accede di **parametri** raccolta prima di chiamare il **aggiornamento** metodo ADO chiamare il metodo e popolare la raccolta per l'utente automaticamente.  
  
> [!NOTE]
>  Se si utilizza il **aggiornamento** per ottenere informazioni sui parametri da e il provider restituisce uno o più tipi di dati a lunghezza variabile [parametro](../../../ado/reference/ado-api/parameter-object.md) gli oggetti ADO potrebbe allocare memoria per i parametri di base alle relative dimensioni massime possibili, che verrà generato un errore durante l'esecuzione. È necessario impostare in modo esplicito il [dimensioni](../../../ado/reference/ado-api/size-property-ado-parameter.md) proprietà per tali parametri prima di chiamare il [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md) metodo per evitare errori.  
  
### <a name="fields"></a>Campi  
 Utilizzando il **aggiornamento** metodo il [campi](../../../ado/reference/ado-api/fields-collection-ado.md) raccolta non ha alcun effetto visibile. Per recuperare le modifiche dalla struttura di database sottostante, è necessario utilizzare il [Requery](../../../ado/reference/ado-api/requery-method.md) metodo oppure, se il [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto non supporta i segnalibri, il [MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)metodo.  
  
### <a name="properties"></a>Proprietà  
 Utilizzando il **aggiornamento** metodo su un **proprietà** insieme di alcuni oggetti popola la raccolta con le proprietà dinamiche esposte dal provider. Queste proprietà forniscono informazioni sulle funzionalità specifiche per il provider, oltre a ADO supporta le proprietà predefinite.  
  
## <a name="applies-to"></a>Si applica a  
  
||||  
|-|-|-|  
|[Raccolta di assi](../../../ado/reference/ado-md-api/axes-collection-ado-md.md)|[Raccolta di colonne](../../../ado/reference/adox-api/columns-collection-adox.md)|[Insieme CubeDefs](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md)|  
|[Raccolta di dimensioni](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md)|[Raccolta di errori](../../../ado/reference/ado-api/errors-collection-ado.md)|[Raccolta di campi](../../../ado/reference/ado-api/fields-collection-ado.md)|  
|[Raccolta di gruppi](../../../ado/reference/adox-api/groups-collection-adox.md)|[Raccolta di gerarchie](../../../ado/reference/ado-md-api/hierarchies-collection-ado-md.md)|[Raccolta di indici](../../../ado/reference/adox-api/indexes-collection-adox.md)|  
|[Raccolta di chiavi](../../../ado/reference/adox-api/keys-collection-adox.md)|[Raccolta di livelli](../../../ado/reference/ado-md-api/levels-collection-ado-md.md)|[Raccolta di membri](../../../ado/reference/ado-md-api/members-collection-ado-md.md)|  
|[Raccolta di parametri](../../../ado/reference/ado-api/parameters-collection-ado.md)|[Raccolta di posizioni](../../../ado/reference/ado-md-api/positions-collection-ado-md.md)|[Raccolta di procedure](../../../ado/reference/adox-api/procedures-collection-adox.md)|  
|[Raccolta delle proprietà](../../../ado/reference/ado-api/properties-collection-ado.md)|[Raccolta di tabelle](../../../ado/reference/adox-api/tables-collection-adox.md)|[Raccolta di utenti](../../../ado/reference/adox-api/users-collection-adox.md)|  
|[Raccolta di viste](../../../ado/reference/adox-api/views-collection-adox.md)|||  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio del metodo Refresh (VB)](../../../ado/reference/ado-api/refresh-method-example-vb.md)   
 [Esempio del metodo Refresh (VC + +)](../../../ado/reference/ado-api/refresh-method-example-vc.md)   
 [Proprietà Count (ADO)](../../../ado/reference/ado-api/count-property-ado.md)   
 [Metodo Refresh (RDS)](../../../ado/reference/rds-api/refresh-method-rds.md)

