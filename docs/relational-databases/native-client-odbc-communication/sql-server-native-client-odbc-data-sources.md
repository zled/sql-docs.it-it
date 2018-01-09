---
title: Origini dati ODBC di SQL Server Native Client | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-communication
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- ODBC data sources, about data sources
- ODBC data sources, names
- data sources [SQL Server Native Client]
- names [ODBC]
- ODBC applications, data sources
- SQL Server Native Client ODBC driver, data sources
- ODBC data sources
ms.assetid: a6a50fd0-d439-43fd-b76f-16ec02f478c5
caps.latest.revision: "28"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: accb9601bff5406e0bbb2ff3f0b2e92291aa76a5
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="sql-server-native-client-odbc-data-sources"></a>Origini dati ODBC di SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Un nome di origine dati (DSN, Data Source Name) di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] identifica un'origine dati ODBC che contiene tutte le informazioni necessarie a un'applicazione ODBC per connettersi a un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in un server specifico. Per definire un nome di origine dati ODBC, è possibile procedere in due modi diversi:  
  
-   In un computer client, aprire Strumenti di amministrazione nel Pannello di controllo e fare doppio clic su **origini dati (ODBC)**. Verrà visualizzato Amministratore origine dati ODBC, in cui è possibile creare un nome di origine dati.  
  
-   In un'applicazione ODBC, chiamare [SQLConfigDataSource](../../relational-databases/native-client-odbc-api/sqlconfigdatasource.md).  
  
 Un'origine dati di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contiene gli elementi seguenti:  
  
-   Nome dell'origine dati.  
  
-   Tutte le informazioni necessarie per connettersi a un'istanza specifica di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Database predefinito da utilizzare in un'istanza specifica di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (facoltativo).  
  
-   Impostazioni quali le opzioni ANSI da utilizzare, la registrazione o meno delle statistiche sulle prestazioni e così via (facoltativo).  
  
 Un'applicazione ODBC non è necessaria per connettersi tramite un'origine dati. L'applicazione, tuttavia, deve fornire le stesse informazioni sulla connettività a una funzione di connessione ODBC altrimenti individuate dal driver in un nome di origine dati.  
  
## <a name="see-also"></a>Vedere anche  
 [La comunicazione con SQL Server &#40; ODBC &#41;](../../relational-databases/native-client-odbc-communication/communicating-with-sql-server-odbc.md)  
  
  
