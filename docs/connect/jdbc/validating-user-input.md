---
title: Convalida dell'Input utente | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8aa867b0-e6f0-49eb-93d3-817ae2ed8f77
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9f46806c35bffcc9cacd77483f6a4cfe01153d5a
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="validating-user-input"></a>Convalida dell'input utente
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Quando si costruisce un'applicazione che accede ai dati, è necessario presupporre che ogni input utente possa essere dannoso fino a quando non viene dimostrato il contrario. In caso contrario, l'applicazione può essere vulnerabile agli attacchi. Uno tipo di attacco che può verificarsi è detto attacchi SQL injection, in cui il codice dannoso viene aggiunto in stringhe successivamente passate a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] per essere analizzate ed eseguite. Per evitare questo tipo di attacco, è necessario utilizzare stored procedure con parametri, dove possibile, e convalidare sempre l'input utente.  
  
 La convalida dell'input utente nel codice client è importante per evitare di eseguire round trip al server non necessari. È altrettanto importante convalidare i parametri delle stored procedure nel server per intercettare l'input non valido e che ignora la convalida sul lato client.  
  
 Per ulteriori informazioni su SQL injection e su come evitarlo, vedere "SQL Injection" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] documentazione in linea. Per ulteriori informazioni sulla convalida dei parametri di stored procedure, vedere "Stored procedure ([!INCLUDE[ssDE](../../includes/ssde_md.md)])" e gli argomenti subordinati nella [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] documentazione in linea.  
  
## <a name="see-also"></a>Vedere anche  
 [Protezione di applicazioni del Driver JDBC](../../connect/jdbc/securing-jdbc-driver-applications.md)  
  
  

