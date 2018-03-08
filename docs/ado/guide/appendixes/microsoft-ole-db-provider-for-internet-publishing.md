---
title: Provider Microsoft OLE DB per Internet Publishing | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- OLE DB provider for Internet publishing [ADO]
- providers [ADO], OLE DB provider for Internet publishing
- Internet Publishing provider [ADO]
ms.assetid: 66a208d9-b580-4655-a41e-1d36e5b5bfca
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f86280c8c9b01e8482500fa174784d6d752b7d9e
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="microsoft-ole-db-provider-for-internet-publishing-overview"></a>Provider Microsoft OLE DB per Internet Publishing Panoramica
Il Provider Microsoft OLE DB per Internet Publishing consente ADO per accedere alle risorse gestite da Microsoft FrontPage o Microsoft Internet Information Server. Le risorse includono i file di origine web quali file HTML o le cartelle web di Windows 2000.

## <a name="connection-string-parameters"></a>Parametri di stringa di connessione
 Per connettersi a questo provider, impostare il *Provider* argomento del [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) proprietà:

```
MSDAIPP.DSO
```

 Questo valore può essere impostato o utilizzando il [Provider](../../../ado/reference/ado-api/provider-property-ado.md) proprietà.

## <a name="typical-connection-string"></a>Stringa di connessione tipica
 Una stringa di connessione tipica per questo provider è:

```
"Provider=MSDAIPP.DSO;Data Source=ResourceURL;User ID=MyUserID;Password=MyPassword;"
```

 oppure

```
"URL=ResourceURL;User ID=MyUserID;Password=MyPassword;"
```

 La stringa è costituita da queste parole chiave:

|Parola chiave|Description|
|-------------|-----------------|
|**Provider**|Specifica il Provider OLE DB per la pubblicazione su Internet.|
|**Origine dati** - oppure - **URL**|Specifica l'URL di un file o directory pubblicati in una cartella Web.|
|**ID utente**|Specifica il nome utente.|
|**Password**|Specifica la password dell'utente.|

> [!NOTE]
>  Se ci si connette a un provider dell'origine dati che supporta l'autenticazione di Windows, è necessario specificare **Trusted_Connection = yes** o **Integrated Security = SSPI** anziché l'ID utente e password informazioni nella stringa di connessione.

 Se si imposta la *ResourceURL* valore di "URL =" nella stringa di connessione a un valore non valido, per impostazione predefinita Internet Publishing Provider genera una finestra di dialogo per la richiesta di un valore valido. Si tratta di un comportamento indesiderato per un componente nel livello intermedio di un'applicazione, poiché sospende l'esecuzione del programma, fino a quando non viene cancellata la finestra di dialogo e il client sembra bloccarsi perché non ha ricevuto una risposta dal componente.

> [!NOTE]
>  Se MSDAIPP. DSO è specificato in modo esplicito come valore del provider, con la *Provider* parola chiave di stringa di connessione o **Provider** proprietà, è possibile utilizzare "URL =" nella stringa di connessione. In caso contrario, si verificherà un errore. Specificare invece l'URL come illustrato nell'argomento [utilizzo di ADO con il Provider OLE DB per Internet Publishing](../../../ado/guide/data/the-ole-db-provider-for-internet-publishing.md).

## <a name="see-also"></a>Vedere anche
 [Scenario di pubblicazione Internet](../../../ado/guide/data/internet-publishing-scenario.md) [il Provider OLE DB per la pubblicazione su Internet](../../../ado/guide/data/the-ole-db-provider-for-internet-publishing.md)
