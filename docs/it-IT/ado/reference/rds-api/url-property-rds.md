---
title: Proprietà URL (RDS) | Documenti Microsoft
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.prod: sql
ms.prod_service: drivers
ms.component: reference
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- URL property [ADO]
ms.assetid: 8c56b233-1be8-442c-8d0e-a4c96465bc99
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 438f0cc9a0d17adea2ded5afde43c33b4bb315d9
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="url-property-rds"></a>Proprietà URL (RDS)
Indica una stringa contenente un URL relativo o assoluto.  
  
 È possibile impostare il **URL** proprietà in fase di progettazione nel [DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) dell'oggetto tag o in fase di esecuzione nel codice di script.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Design time: <PARAM NAME="URL" VALUE="Server">  
Run time: DataControl.URL="Server"  
```  
  
#### <a name="parameters"></a>Parametri  
 *Server*  
 Oggetto **stringa** valore che contiene un URL valido.  
  
 *DataControl*  
 Una variabile oggetto che rappresenta un **DataControl** oggetto.  
  
## <a name="remarks"></a>Osservazioni  
 In genere, l'URL identifica un file Active Server Page (ASP) che può generare e restituire un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md). Pertanto, l'utente può ottenere un **Recordset** senza dover richiamare il lato server [DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) dell'oggetto o un oggetto di business personalizzata del programma.  
  
 Se il **URL** proprietà è stata impostata, [SubmitChanges](../../../ado/reference/rds-api/submitchanges-method-rds.md) invierà le modifiche nel percorso specificato dall'URL.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto DataControl (Servizi Desktop remoto)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà URL (VBScript)](../../../ado/reference/rds-api/url-property-example-vbscript.md)


