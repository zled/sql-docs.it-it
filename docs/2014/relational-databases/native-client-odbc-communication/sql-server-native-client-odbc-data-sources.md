---
title: Origini dati SQL Server Native Client ODBC | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
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
caps.latest.revision: 27
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ee13a0180896316e10b20148b2a22a5b0cf4c149
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37408470"
---
# <a name="sql-server-native-client-odbc-data-sources"></a>Origini dati ODBC di SQL Server Native Client
  Un nome di origine dati (DSN, Data Source Name) di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] identifica un'origine dati ODBC che contiene tutte le informazioni necessarie a un'applicazione ODBC per connettersi a un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in un server specifico. Per definire un nome di origine dati ODBC, è possibile procedere in due modi diversi:  
  
-   In un computer client, aprire Strumenti di amministrazione nel Pannello di controllo e fare doppio clic su **origini dati (ODBC)**. Verrà visualizzato Amministratore origine dati ODBC, in cui è possibile creare un nome di origine dati.  
  
-   In un'applicazione ODBC, chiamare [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md).  
  
 Un'origine dati di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contiene gli elementi seguenti:  
  
-   Nome dell'origine dati.  
  
-   Tutte le informazioni necessarie per connettersi a un'istanza specifica di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Database predefinito da utilizzare in un'istanza specifica di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (facoltativo).  
  
-   Impostazioni quali le opzioni ANSI da utilizzare, la registrazione o meno delle statistiche sulle prestazioni e così via (facoltativo).  
  
 Un'applicazione ODBC non è necessaria per connettersi tramite un'origine dati. L'applicazione, tuttavia, deve fornire le stesse informazioni sulla connettività a una funzione di connessione ODBC altrimenti individuate dal driver in un nome di origine dati.  
  
## <a name="see-also"></a>Vedere anche  
 [Comunicazione con SQL Server &#40;ODBC&#41;](communicating-with-sql-server-odbc.md)  
  
  
