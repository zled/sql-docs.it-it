---
title: Proprietà Connect (RDS) | Documenti Microsoft
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
apitype: COM
helpviewer_keywords:
- Connect property [ADO]
ms.assetid: dbad5e77-b213-4eb8-aecf-d60f203fdb59
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b517d0d6a04d74901c51e43bce4b8c45b61280e4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="connect-property-rds"></a>Proprietà Connect (RDS)
Indica il nome del database da cui vengono eseguite le operazioni di aggiornamento e di query.  
  
 È possibile impostare il **Connetti** proprietà in fase di progettazione nel [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) tag OBJECT dell'oggetto, o in fase di esecuzione nel codice (ad esempio, VBScript) di script.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Design time: <PARAM NAME="Connect" VALUE="ConnectionString">  
Run time: DataControl.Connect = "ConnectionString"  
```  
  
#### <a name="parameters"></a>Parametri  
 *connectionString*  
 Una stringa di connessione valido. Per ulteriori informazioni generali sulle stringhe di connessione, vedere il [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) proprietà o la documentazione del provider.  
  
> [!NOTE]
>  Specifica MS Remote come provider per il **RDS. DataControl** verrà creato uno scenario con quattro livelli. Scenari a più di tre livelli non sono stati testati e non sono necessari.  
  
 *DataControl*  
 Una variabile oggetto che rappresenta un **RDS. DataControl** oggetto.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto DataControl (Servizi Desktop remoto)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Vedere anche  
 [La connessione di esempio di proprietà (VBScript)](../../../ado/reference/rds-api/connect-property-example-vbscript.md)   
 [Metodo query (RDS)](../../../ado/reference/rds-api/query-method-rds.md)   
 [Metodo Refresh (RDS)](../../../ado/reference/rds-api/refresh-method-rds.md)   
 [Metodo SubmitChanges (Servizi Desktop remoto)](../../../ado/reference/rds-api/submitchanges-method-rds.md)


