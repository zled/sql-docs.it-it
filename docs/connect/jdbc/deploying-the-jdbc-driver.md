---
title: Distribuzione del Driver JDBC | Documenti Microsoft
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
ms.assetid: 3ad3508d-d9b1-47fb-a63b-21cdc3ed44e0
caps.latest.revision: "26"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: fdeed91effe8c6619121f6ed392237f710a785d8
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2017
---
# <a name="deploying-the-jdbc-driver"></a>Distribuzione del driver JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Quando si distribuisce un'applicazione che dipende il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], è necessario ridistribuire il driver JDBC insieme all'applicazione. Diversamente da Windows Data Access Components (Windows DAC), che è un componente del sistema operativo Windows, il driver JDBC è considerato un componente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
 Esistono due approcci per la distribuzione del driver JDBC con l'applicazione. Un approccio prevede l'inclusione dei file del driver JDBC come parte del pacchetto di installazione personalizzato. Il secondo approccio prevede mediante il pacchetto di installazione JDBC fornito da Microsoft, è possibile scaricare dal [Microsoft JDBC Driver per SQL Server Developer Center](http://go.microsoft.com/fwlink/?LinkId=70166).  
  
 Nelle sezioni seguenti viene descritto come utilizzare il pacchetto di installazione JDBC in sistemi operativi Windows e UNIX.  
  
> [!NOTE]  
>  Per informazioni generali sulla distribuzione di applicazioni Java, vedere il sito Web Java.  
  
## <a name="deploying-the-jdbc-driver-on-windows-systems"></a>Distribuzione del driver JDBC in sistemi Windows  
 Quando si distribuisce il driver JDBC nei sistemi operativi Windows, è necessario utilizzare la versione del file zip eseguibile del pacchetto di installazione, è in genere denominato `sqljdbc_<version>_<language>.exe`.  
  
 Per l'esecuzione invisibile del file eseguibile zip, è necessario utilizzare il `/auto` opzione della riga di comando nella riga di comando o in un file batch come illustrato di seguito:  
  
 `sqljdbc_<version>_<language>.exe /auto`  
  
> [!NOTE]  
>  Quando si utilizza il `/auto` opzione non è un'installazione realmente invisibile, come una finestra di dialogo di WinZip verrà comunque visualizzata sullo schermo dell'utente. Tuttavia, non è necessario interagire con essa e viene chiusa non appena l'operazione di decompressione è stata completata.  
  
## <a name="deploying-the-driver-on-unix-systems"></a>Distribuzione del driver su sistemi UNIX  
 Quando si distribuisce il driver JDBC in sistemi operativi UNIX, è necessario utilizzare la versione del file gzip del pacchetto di installazione, è in genere denominato `sqljdbc_<version>_<language>.tar.gz`.  
  
 Prima di installare il driver JDBC, assicurarsi che entrambe le utilità GZIP e TAR siano installate nel sistema operativo dell'utente e che le cartelle che contengono i file eseguibili di entrambe le utilità siano state aggiunte alla variabile di ambiente PATH.  
  
 Per decomprimere il file con estensione tar compresso, passare alla directory in cui si desidera decomprimere il driver e digitare il comando seguente:  
  
 `gzip -d sqljdbc_<version>_<language>.tar.gz`  
  
 Per decomprimere il file con estensione tar, spostarlo nella directory in cui si desidera installare il driver e digitare il comando seguente:  
  
 `tar –xf sqljdbc_<version>_<language>.tar`  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica del driver JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
