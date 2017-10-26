---
title: Microsoft JDBC Driver per SQL Server Support Matrix | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c5769e67-99f7-4bc1-a4fa-8941dad33d35
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 35747cff6a18c79a828e5269d7085c710338bf18
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="microsoft-jdbc-driver-for-sql-server-support-matrix"></a>Matrice di supporto di Microsoft JDBC Driver per SQL Server
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Questa pagina contiene i criteri relativi al ciclo di vita e alla matrice del supporto di Microsoft JDBC Driver per SQL Server.  
  
## <a name="microsoft-jdbc-driver-support-lifecycle-matrix-and-policy"></a>Criteri relativi alla matrice e al ciclo di vita del supporto di Microsoft JDBC Driver  
 I criteri relativi al ciclo di vita del supporto Microsoft (MSL) forniscono informazioni trasparenti e prevedibili riguardanti il ciclo di vita del supporto dei prodotti Microsoft. Le versioni del driver JDBC 3.0 e 4.x offrono fino a cinque anni di supporto "Mainstream" della data di rilascio del driver. Il supporto "Mainstream" viene definito nel sito Web del ciclo di vita del supporto Microsoft.  
  
 Le opzioni di supporto esteso e personalizzato non sono disponibili per Microsoft JDBC Driver.  
    
 I seguenti driver Microsoft JDBC Driver sono supportati fino alla data di fine del supporto indicata.  
  
|Nome del driver|Versione del pacchetto driver|JAR(s) applicabile|Fine del supporto Mainstream|
|-|-|-|-|  
|Microsoft JDBC Driver 6.2 per SQL Server|6.2|MSSQL-jdbc-6.2.1.jre8.jar<br> MSSQL-jdbc-6.2.1.jre7.jar|30 giugno 2022|    
|Microsoft JDBC Driver 6.0 per SQL Server|6.0|sqljdbc42.jar<br>sqljdbc41.jar|14 luglio 2021|    
|Microsoft JDBC Driver 4.2 per SQL Server|4.2|sqljdbc42.jar<br>sqljdbc41.jar|24 agosto 2020|  
|Microsoft JDBC Driver 4.1 per SQL Server|4.1|sqljdbc41.jar|12 dicembre 2019|  
  
 I seguenti driver Microsoft JDBC Driver non sono più supportati.  
 
|Nome del driver|Versione del pacchetto driver|Fine del supporto Mainstream|  
|-|-|-|
|Microsoft JDBC Driver 4.0 per SQL Server|4.0|6 marzo 2017|  
|Driver JDBC 3.0 per Microsoft SQL Server|3.0|23 aprile 2015|  
|Microsoft SQL Server JDBC Driver 2.0|2.0|31 dicembre 2012|  
|Driver JDBC 1.2 per Microsoft SQL Server 2005|1.2|25 giugno 2011|  
|Microsoft SQL Server 2005 JDBC Driver 1.1|1.1|25 giugno 2011|  
|Microsoft SQL Server 2005 JDBC Driver 1.0|1,0|25 giugno 2011|  
|Microsoft SQL Server 2000 JDBC Driver|2000|9 luglio 2010|  
  
## <a name="sql-version-compatibility"></a>Compatibilità tra versioni SQL  
  
|Versione driver|SQL Server 2008|SQL Server 2008 R2|SQL Server 2012|Database SQL di Azure|PDW 2008R2 AU3<sup>4</sup>|SQL Server 2014|SQL Server 2016|  
|-|-|-|-|-|-|-|-| 
|6.2|S|S|S|S|S|S|S|  
|6.1|S|S|S|S|S|S|S|  
|6.0|S|S|S|S|S|S|S|  
|4.2|S|S|S|S|S|S|S|  
|4.1|S|S|S|S|S|S|S|  
|4.0|S|S|S|S|S|S|S|  
|3.0|S|S|Y<sup>1</sup>|Y<sup>2</sup>|N|Y<sup>5</sup>|N|  
|2.0|Y<sup>3</sup>|Y<sup>3</sup>|N|N|N|N|N|  
|1.2|Y<sup>3</sup>|N|N|N|N|N|N|  
|1.1|N|N|N|N|N|N|N|  
|1,0|N|N|N|N|N|N|N|  
|2000|N|N|N|N|N|N|N|  
  
 <sup>1</sup>Microsoft SQL Server JDBC Driver versione 3.0 può connettersi a SQL Server 2012 come un client di livello inferiore.  
  
 <sup>2</sup>supporto per Database SQL di Azure è stato introdotto nel driver 3.0 driver come hotfix. Si consiglia ai clienti del database SQL di Azure di usare la versione del driver più recente disponibile.  
  
 <sup>3</sup>Microsoft SQL Server JDBC Driver versione 2.0 e Microsoft SQL Server 2005 JDBC Driver versione 1.2 possono connettersi a SQL Server 2008 come client di livello inferiore. Quando sono consentite le conversioni di livello inferiore, le applicazioni possono eseguire query e aggiornamenti nei nuovi tipi di dati di SQL Server 2008, ad esempio time, date, datetime2, datetimeoffset e FILESTREAM. Per altre informazioni su come usare questi nuovi tipi di dati con il driver JDBC, vedere i post di blog relativi all'  [uso dei tipi di dati per data/ora di SQL Server 2008 con il driver JDBC](http://go.microsoft.com/fwlink/?LinkId=145198) e all'  [uso di SQL Server 2008 FileStream con il driver JDBC](http://go.microsoft.com/fwlink/?LinkId=145199). Per altre informazioni sulla compatibilità di livello inferiore di questi nuovi tipi di dati, vedere gli argomenti  [Utilizzo di dati relativi a data e ora](http://go.microsoft.com/fwlink/?LinkId=145211)e  [Supporto FILESTREAM](http://go.microsoft.com/fwlink/?LinkId=145212) nella documentazione online di SQL Server.  
  
 <sup>4</sup>supporto per le connessioni tra il Microsoft JDBC Driver e Parallel Data Warehouse è stata introdotta in Microsoft JDBC Driver 4.0 per SQL Server e Microsoft SQL Server 2008 R2 Parallel Data Warehouse Appliance Update 3.  
  
 <sup>5</sup>Microsoft SQL Server JDBC Driver versione 3.0 può connettersi a SQL Server 2014 come client di livello inferiore.  
  
## <a name="java-and-jdbc-specification-support"></a>Supporto per le specifiche Java e JDBC  
  
|Versione driver JDBC|Versioni JRE|Versioni API JDBC| 
|-|-|-|  
|6.2|1.7, 1.8|4.1, 4.2|  
|6.1|1.7, 1.8|4.1, 4.2|  
|6.0|1.7, 1.8|4.1, 4.2|  
|4.2|1.7, 1.8|4.1, 4.2|  
|4.1|1.7|4.0|  
|4.0|1.5, 1.6, 1.7|3.0, 4.0|  
|3.0|1.5, 1.6,|3.0, 4.0|  
|2.0|1.5, 1.6|3.0, 4.0|  
|1.2|1.4, 1.5, 1.6|3.0|  
|1.1|1.4|3.0|  
|1,0|1.4|3.0|  
|2000|1.4|3.0|  
  
## <a name="supported-operating-systems"></a>Sistemi operativi supportati  
 Microsoft JDBC Driver è stato sviluppato per essere usato in qualsiasi sistema operativo che supporti l'utilizzo di Java Virtual Machine (JVM). Alcune delle piattaforme usate di frequente sono: Windows 10, Windows 8.1, Windows 8, Windows 7, Windows Server 2008 R2, Windows Vista, Linux, Unix, AIX, MacOS e altre.  
  
 Il team del prodotto JDBC testa il driver in Windows, Sun Solaris, SUSE Linux e RedHat Linux.  Il Supporto tecnico è disponibile per i clienti di tutte le piattaforme, tuttavia è possibile che venga richiesto di riprodurre il problema in una piattaforma come Windows.  
  
## <a name="application-server-support"></a>Supporto per server applicazioni  
 Microsoft JDBC Driver per SQL Server viene testato con diversi server applicazioni.  Rivolgersi al fornitore del server applicazioni per altre informazioni sulla versione del driver compatibile con il prodotto fornito.  
  
  

