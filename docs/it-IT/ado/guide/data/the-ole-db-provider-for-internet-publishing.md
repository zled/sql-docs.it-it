---
title: Il Provider OLE DB per la pubblicazione su Internet | Documenti Microsoft
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
helpviewer_keywords:
- OLE DB provider for Internet publishing [ADO]
- ADO, Internet publishing
- publishing to Internet [ADO]
- Internet publishing [ADO]
- providers [ADO], OLE DB provider for Internet publishing
ms.assetid: 4869aafa-7401-4ce1-93ce-45406a60274f
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 908160d594df0c24b45960e30a1d50cbebed6416
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="the-ole-db-provider-for-internet-publishing"></a>Il Provider OLE DB per la pubblicazione su Internet
ADO [Record](../../../ado/reference/ado-api/record-object-ado.md) e [flusso](../../../ado/reference/ado-api/stream-object-ado.md) oggetti sono utilizzabile con il Provider Microsoft OLE DB per Internet Publishing (Internet Publishing Provider) per accedere e modificare le risorse, ad esempio file o cartelle Web servite da Microsoft FrontPage. Con ADO, è possibile specificare l'origine di un **Record**, **flusso**, o [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) da un URL. È possibile caricare, scaricare, spostare, copiare ed eliminare le risorse o modificare direttamente le proprietà delle risorse.  
  
 Ad esempio di codice che usa **record** e **flussi** con Internet Publishing Provider, vedere il [Scenario pubblicazione Internet](../../../ado/guide/data/internet-publishing-scenario.md).  
  
 Internet Publishing Provider viene installato con Microsoft Windows 2000. Le versioni precedenti di Internet Publishing Provider sono disponibili anche con Microsoft Office 2000 e Microsoft Internet Explorer 5.0.  
  
 Esistono tre modi per la connessione di ADO per Internet Publishing Provider:  
  
-   Specificare "URL =" nella stringa di connessione. Esempio:  
  
    ```  
    objConn.Open "URL=http://servername"  
    ```  
  
-   Specificare Msdaipp. DSO per il *Provider* parola chiave della stringa di connessione. Esempio:  
  
    ```  
    objConn.Open "provider=MSDAIPP.DSO;data source=http://servername"  
    ```  
  
-   Specificare Msdaipp. DSO per il [Provider](../../../ado/reference/ado-api/provider-property-ado.md) proprietà del [connessione](../../../ado/reference/ado-api/connection-object-ado.md) oggetto. Esempio:  
  
    ```  
    objConn.Provider = "MSDAIPP.DSO"  
    objConn.Open "http://servername"  
    ```  
  
> [!NOTE]
>  Se Msdaipp. DSO è specificato in modo esplicito come valore del provider, con la *Provider* parola chiave di stringa di connessione o **Provider** proprietà, è possibile utilizzare "URL =" nella stringa di connessione. In caso contrario, si verificherà un errore. In alternativa, è sufficiente specificare l'URL come illustrato in precedenza.  
  
 Per informazioni più specifiche su Internet Publishing Provider, vedere [il Provider Microsoft OLE DB per Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md), o la documentazione del provider fornita con l'applicazione di origine con cui il Provider OLE DB per È stato installato Internet Publishing: Windows 2000, Office 2000 o Internet Explorer 5.0.
