---
title: Componenti di SQL Server Native Client | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, about SQL Server Native Client ODBC driver
- data access [SQL Server Native Client], components
- components [SQL Server Native Client]
- SQLNCLI, about SQL Server Native Client
ms.assetid: 65f932d5-daa1-4eff-b6df-ee633fcf2a7c
caps.latest.revision: 22
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c1a53fe3338f7b987bdf2b26312d634964f3587e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36064234"
---
# <a name="components-of-sql-server-native-client"></a>Componenti di SQL Server Native Client
  In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client sono inclusi i componenti seguenti:  
  
|Componente|Description|  
|---------------|-----------------|  
|sqlncli11.dll|File della libreria di collegamento dinamico (DLL) che contiene tutte le funzionalità di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Sono inclusi il provider OLE DB di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client e il driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.|  
|sqlnclir11.rll|File di risorse associato per la libreria di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.|  
|s10ch_sqlncli.chm|File della Guida della Creazione guidata origine dati in cui viene illustrato come creare un'origine dati [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilizzando il driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client o il provider OLE DB di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.|  
|sqlncli.h|File di intestazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client che contiene tutte le nuove definizioni necessarie per utilizzare [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Questo file di intestazione sostituisce entrambi i file di intestazione, odbcss.h e sqloledb.h. **Nota:** è possibile fare riferimento a SQLNCLI. h e Odbcss. h nello stesso programma, ma è possibile fare riferimento a SQLNCLI. h e SQLOLEDB. h nello stesso programma, purché venga definito prima SQLOLEDB. h.|  
|sqlncli11.lib|Il file di libreria necessario per chiamare direttamente il **bcp** le funzioni di utilità che fanno parte di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] driver ODBC Native Client. **Nota:** se si fa riferimento al file sqlncli11.lib nel codice di programmazione, è necessario assicurarsi che il file sqlncli11.dll sia nel proprio percorso di sistema e nel percorso di sistema di utenti che utilizzano l'applicazione.|  
  
## <a name="see-also"></a>Vedere anche  
 [Compilazione di applicazioni con SQL Server Native Client](building-applications-with-sql-server-native-client.md)  
  
  