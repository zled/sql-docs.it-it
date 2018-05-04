---
title: InvokeService (RDS) | Documenti Microsoft
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
- InvokeService [RDS]
ms.assetid: ad45c676-ec7e-4a3a-9a6b-a54f75eb3012
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a78c815f75b5e30713e0b7f9e5b7ec83c4c3eb6d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="invokeservice-rds"></a>InvokeService (RDS)
Restituisce un puntatore all'interfaccia richiesta in una versione più in grado di oggetto.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
object.InvokeService(REFID riid, IUknown* punkNotSoFunctionalInterface, IUknown** ppunkMoreFunctionalInterface) As HRESULT  
```  
  
#### <a name="parameters"></a>Parametri  
 *riid*  
  
 [in] Identificatore dell'interfaccia richiesta.  
  
 *punkNotSoFunctionalInterface*  
  
 [in] Oggetto in grado di supportare meno di origine.  
  
 *ppunkMoreFunctionalInterface*  
  
 [out] L'indirizzo della variabile del puntatore che riceve il puntatore di interfaccia richiesto *riid*. Dopo la restituzione ha esito positivo, il *ppunkMoreFunctionalInterface* parametro contiene il puntatore dell'interfaccia richiesta per l'oggetto. Se l'oggetto non supporta l'interfaccia specificata *riid*, *ppunkMoreFunctionalInterface* è impostato su NULL.  
  
## <a name="return-value"></a>Valore restituito  
 Valore HRESULT che indica se la chiamata al **InvokeService** metodo ha avuto esito positivo.  
  
## <a name="remarks"></a>Osservazioni  
 L'implementazione di motore del cursore di servizi desktop remoto di **InvokeService** accetta il set di righe di input (o più oggetti risultati), consente di popolare il motore del cursore dal set di righe di input e quindi restituisce un puntatore in se stesso.  
  
## <a name="applies-to"></a>Si applica a  
 [Interfaccia IRDSService (Servizi Desktop remoto)](../../../ado/reference/rds-api/irdsservice-interface-rds.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di Servizi Desktop remoto](../../../ado/reference/rds-api/rds-methods.md)


