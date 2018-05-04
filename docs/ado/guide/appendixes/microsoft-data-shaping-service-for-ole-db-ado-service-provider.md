---
title: Microsoft servizio Data Shaping per OLE DB (ADO Service Provider) | Documenti Microsoft
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
helpviewer_keywords:
- providers [ADO], data shaping service for OLE DB
- data shaping service for OLE DB [ADO]
ms.assetid: 523009ce-e01b-4e2d-a7df-816d7688aff0
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a3020789835820519e07ac3e465899c3ac93b0ae
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="microsoft-data-shaping-service-for-ole-db-overview"></a>Microsoft servizio Data Shaping per OLE DB Panoramica
> [!IMPORTANT]
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni devono invece utilizzare XML.

 Il servizio Microsoft di Data Shaping per service provider OLE DB supporta la creazione di gerarchici (forma) [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetti da un provider di dati.

## <a name="provider-keyword"></a>Parola chiave del provider
 Per richiamare il servizio Data Shaping per OLE DB, specificare la parola chiave e il valore seguente nella stringa di connessione.

```
"Provider=MSDataShape"
```

## <a name="dynamic-properties"></a>Proprietà dinamiche
 Quando viene richiamato questo provider di servizi, le proprietà dinamiche seguenti vengono aggiunti per il [proprietà](../../../ado/reference/ado-api/properties-collection-ado.md) insieme il[connessione](../../../ado/reference/ado-api/connection-object-ado.md) oggetto.

|Nome della proprietà dinamica|Description|
|---------------------------|-----------------|
|**Nomi univoci nuova forma**|Indica se **Recordset** oggetti con valori duplicati per i relativi **modificare la forma di nome** proprietà sono consentite. Se questa proprietà dinamica è **True** e un nuovo **Recordset** viene creato con lo stesso nome della nuova forma specificato dall'utente di un oggetto esistente **Recordset**, quindi nuovo  **Recordset** Nome nuova forma dell'oggetto viene modificato per renderlo univoco. Se questa proprietà è **False** e un nuovo **Recordset** viene creato con lo stesso nome nuova forma specificato dall'utente esistenti **Recordset**, entrambi **Recordset**  oggetti avranno lo stesso nome della nuova forma. Di conseguenza, nessuno dei due **Recordset** può modificare la forma fino a quando esistono entrambi gli oggetti.<br /><br /> Il valore predefinito della proprietà è **False**.|
|**Provider di dati**|Indica il nome del provider che fornirà le righe da essere modellati. Questo valore può essere NONE se non verrà utilizzato un provider per fornire righe.|

 È anche possibile impostare proprietà dinamiche scrivibili specificando i relativi nomi come parole chiave nella stringa di connessione. Ad esempio, in Microsoft Visual Basic, impostare il **Provider di dati** proprietà dinamica su "MSDASQL", specificando:

```
Dim cn as New ADODB.Connection
cn.Open "Provider=MSDataShape;Data Provider=MSDASQL"
```

 È anche possibile impostare o recuperare una proprietà dinamica specificandone il nome dell'indice per il [proprietà](../../../ado/reference/ado-api/properties-collection-ado.md) proprietà. Ad esempio, l'esempio di codice seguente recupera e stampa il valore corrente del **Provider di dati** proprietà dinamiche, quindi imposta un nuovo valore se cn. DataProvider è stata impostata su "MSDataShape" (direttamente o indirettamente tramite la stringa di connessione) e non è stata aperta la connessione:

```
Debug.Print cn.Properties("Data Provider")
cn.Properties("Data Provider") = "MSDASQL"
```

> [!NOTE]
>  La proprietà dinamica **Provider di dati**, può essere impostato solo su un non aperta **connessione** oggetto. Una volta aperta la connessione, il **Provider di dati** proprietà diventa di sola lettura.

 Per ulteriori informazioni sul data shaping, vedere [il Data Shaping](../../../ado/guide/data/data-shaping-overview.md).

## <a name="see-also"></a>Vedere anche
 [Appendice A: Provider](../../../ado/guide/appendixes/appendix-a-providers.md)
