---
title: Utilizzo di ADO per Internet Publishing | Documenti Microsoft
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
helpviewer_keywords:
- ADO, Internet publishing
- publishing to Internet [ADO]
- Internet publishing [ADO]
- urls [ADO]
ms.assetid: d399fce4-b70b-418f-8110-3deb3448863c
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 97b94feddfa95a954294ba27a66dd02632c9a24a
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="using-ado-for-internet-publishing"></a>Utilizzo di ADO per la pubblicazione su Internet
[Il Provider OLE DB per Internet Publishing](../../../ado/guide/data/the-ole-db-provider-for-internet-publishing.md) illustra un esempio specifico di accesso ai dati eterogenei con ADO. Sebbene gli esempi in questa sezione sarà specifici per l'uso di Provider di pubblicazione, i principi illustrati dovrebbero essere simili l'utilizzo di ADO con altri provider di dati eterogenei, ad esempio un provider a un archivio di posta elettronica.  
  
## <a name="urls"></a>URL  
 Uniform Resource Locator (URL) è utilizzabile come alternativa alle stringhe di connessione e il testo del comando per specificare le origini dati e il percorso del file e directory. È possibile utilizzare l'URL con esistente [connessione](../../../ado/reference/ado-api/connection-object-ado.md) e **Recordset** oggetti e con il **Record** e **flusso** oggetti.  
  
 Per ulteriori informazioni su come usare gli URL, vedere [URL assoluti e relativi](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="record-fields"></a>I campi di record  
 La differenza tra dati eterogenei e dati omogenei essenziale è che per il primo, ogni riga di dati, o **Record**, può avere un set diverso di colonne, o **campi**. Per i dati omogenei, ogni riga ha lo stesso set di colonne. Per ulteriori informazioni sui campi specifici del Provider di pubblicazione Internet, vedere [record e campi specificati dal provider](../../../ado/guide/data/records-and-provider-supplied-fields.md).  
  
### <a name="appending-new-fields"></a>Aggiunta di nuovi campi  
 Sono stati migliorati numerosi oggetti ADO per lavorare con **Record** e **flusso** oggetti.  
  
-   Il [campi](../../../ado/reference/ado-api/fields-collection-ado.md) raccolta [Append](../../../ado/reference/ado-api/append-method-ado.md) (metodo), che crea e aggiunge un [campo](../../../ado/reference/ado-api/field-object.md) oggetto alla raccolta, può anche specificare il valore del **campo**.  
  
-   Il [aggiornamento](../../../ado/reference/ado-api/update-method.md) metodo completa l'aggiunta o eliminazione di campi alla raccolta.  
  
-   Come alternativa alla scelta rapida e il **Append** metodo, è possibile creare campi assegnando un valore a un campo non definito o eliminato in precedenza.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Provider OLE DB per Internet Publishing](../../../ado/guide/data/the-ole-db-provider-for-internet-publishing.md)  
  
-   [Scenario di Internet Publishing](../../../ado/guide/data/internet-publishing-scenario.md)  
  
-   [URL relativi e assoluti](../../../ado/guide/data/absolute-and-relative-urls.md)  
  
-   [Record e campi specificati dal provider](../../../ado/guide/data/records-and-provider-supplied-fields.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto di record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)   
 [Oggetto di flusso (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)   
 [Cronologia di ADO](../../../ado/guide/ado-history.md)
