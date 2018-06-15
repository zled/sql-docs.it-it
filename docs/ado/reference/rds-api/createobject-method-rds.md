---
title: CreateObject (metodo) (RDS) | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- CreateObject method [ADO]
ms.assetid: dec96be6-0b31-4953-9c9a-e962b5afcd18
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0307edbf2e9b5a6495dd84c45c8dc647fe5bdefd
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35287570"
---
# <a name="createobject-method-rds"></a>CreateObject (metodo) (RDS)
Crea il proxy per l'oggetto business di destinazione e restituisce un puntatore a esso. I pacchetti ed esegue il marshalling dei dati proxy allo stub sul lato server per le comunicazioni con l'oggetto business per l'invio di richieste e dei dati tramite Internet. Per gli oggetti di componente in-process, non vengono utilizzati proxy, viene fornito solo un puntatore all'oggetto.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Sintassi  
 Remote Data Service supporta i seguenti protocolli: HTTP, HTTPS (HTTP over Secure Socket Layer), DCOM e in-process.  
  
|Protocollo|Sintassi|  
|--------------|------------|  
|HTTP|Oggetto set = DataSpace.CreateObject ("ProgId", "http://awebsrvr")|  
|HTTPS|Oggetto set = DataSpace.CreateObject ("ProgId", "https://awebsrvr")|  
|DCOM|Set object = DataSpace.CreateObject("ProgId", "computername")|  
|In-Process|Set object = DataSpace.CreateObject("ProgId", "")|  
  
## <a name="parameters"></a>Parametri  
 *Oggetto*  
 Una variabile oggetto che restituisce un oggetto che rappresenta il tipo specificato in *ProgID*.  
  
 *DataSpace*  
 Una variabile oggetto che rappresenta un [RDS. DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md) oggetto utilizzato per creare un'istanza del nuovo oggetto.  
  
 *ProgID*  
 Oggetto **stringa** valore che contiene l'identificatore a livello di codice che specifica un oggetto business sul lato server che implementa le regole di business dell'applicazione.  
  
 *awebsrvr* o *computername*  
 Oggetto **stringa** valore che rappresenta un URL di identificazione del server Web Internet Information Services (IIS) in cui viene creata un'istanza dell'oggetto business di server.  
  
## <a name="remarks"></a>Remarks  
 Il *protocollo HTTP* è il protocollo Web standard; *HTTPS* è un protocollo Web sicuro. Utilizzare il *protocollo DCOM* durante l'esecuzione di una rete locale senza HTTP. Il *in-process* protocollo è una libreria di collegamento dinamico (DLL) locale, non utilizza una rete.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto DataSpace (Servizi Desktop remoto)](../../../ado/reference/rds-api/dataspace-object-rds.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto DataFactory, metodo di Query ed esempio CreateObject (metodo) (VBScript)](../../../ado/reference/rds-api/datafactory-object-query-method-and-createobject-method-example-vbscript.md)   
 [Oggetto DataSpace e metodo CreateObject (VBScript)](../../../ado/reference/rds-api/dataspace-object-and-createobject-method-example-vbscript.md)   
 [Metodo CreateRecordset (Servizi Desktop remoto)](../../../ado/reference/rds-api/createrecordset-method-rds.md)


