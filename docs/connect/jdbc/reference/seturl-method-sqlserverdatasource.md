---
title: Metodo setURL (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setURL
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: bea70100-ac98-4625-8748-ef7cc0b111ea
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 29e1b67caaf566f04cf01c7c93a5e8d2445c31ef
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47633949"
---
# <a name="seturl-method-sqlserverdatasource"></a>Metodo setURL (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta l'URL utilizzato per la connessione all'origine dati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void setURL(java.lang.String url)  
```  
  
#### <a name="parameters"></a>Parametri  
 *url*  
  
 Valore **String** che contiene l'URL.  
  
## <a name="remarks"></a>Remarks  
 Per motivi di sicurezza, non includere la password nell'URL fornito al metodo setURL. poiché nei server applicazioni Java di terze parti sarà molto spesso visualizzato il set di valori per la proprietà URL nella relativa interfaccia utente di configurazione dell'origine dati. Usare invece il metodo [setPassword](../../../connect/jdbc/reference/setpassword-method-sqlserverdatasource.md) per impostare il valore della password. Nei server applicazioni Java non sarà visualizzata una password che viene impostata nella relativa origine dati nell'interfaccia utente di configurazione.  
  
> [!NOTE]  
>  Se il metodo setURL non viene chiamato prima del metodo [getURL](../../../connect/jdbc/reference/geturl-method-sqlserverdatasource.md), l'oggetto getURL restituisce il valore predefinito "jdbc:sqlserver://".  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
