---
title: Convalida dell'Input utente | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8aa867b0-e6f0-49eb-93d3-817ae2ed8f77
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a00eafc9f72910f05c1850b25bba5e91a4e276a6
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2017
---
# <a name="validating-user-input"></a>Convalida dell'input utente
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Quando si costruisce un'applicazione che accede ai dati, è necessario presupporre che ogni input utente possa essere dannoso fino a quando non viene dimostrato il contrario. In caso contrario, l'applicazione può essere vulnerabile agli attacchi. Uno tipo di attacco che può verificarsi è detto attacchi SQL injection, in cui il codice dannoso viene aggiunto in stringhe successivamente passate a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] per essere analizzate ed eseguite. Per evitare questo tipo di attacco, è necessario utilizzare stored procedure con parametri, dove possibile, e convalidare sempre l'input utente.  
  
 La convalida dell'input utente nel codice client è importante per evitare di eseguire round trip al server non necessari. È altrettanto importante convalidare i parametri delle stored procedure nel server per intercettare l'input non valido e che ignora la convalida sul lato client.  
  
 Per ulteriori informazioni su SQL injection e su come evitarlo, vedere "SQL Injection" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] documentazione in linea. Per ulteriori informazioni sulla convalida dei parametri di stored procedure, vedere "Stored procedure ([!INCLUDE[ssDE](../../includes/ssde_md.md)])" e gli argomenti subordinati nella [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] documentazione in linea.  
  
## <a name="see-also"></a>Vedere anche  
 [Protezione delle applicazioni del driver JDBC](../../connect/jdbc/securing-jdbc-driver-applications.md)  
  
  
