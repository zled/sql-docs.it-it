---
title: Caratteristiche internazionali del Driver JDBC | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbb74a1d-9278-401f-9530-7b5f45aa79de
caps.latest.revision: 40
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8b319e0fe0972b236c03694899c5d4361dbcc473
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="international-features-of-the-jdbc-driver"></a>Caratteristiche internazionali del driver JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Le funzionalità di internazionalizzazione del [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] includono quanto segue:  
  
-   Supporto per un'esperienza completamente localizzata nelle stesse lingue di[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]  
  
-   Supporto per le conversioni di linguaggio Java per dipendenti dalle impostazioni locali [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] dati  
  
-   Supporto per lingue internazionali, indipendentemente dal sistema operativo  
  
-   Supporto per nomi IDN (a partire da Microsoft JDBC Driver 6.0 per SQL Server)  
  
## <a name="handling-of-character-data"></a>Gestione dei dati di tipo carattere  
 Dati di tipo carattere in Java vengono gestiti come Unicode per impostazione predefinita. il linguaggio **stringa** oggetto rappresenta dati di tipo carattere Unicode. Nel driver JDBC l'unica eccezione a questa regola è costituita dai metodi per il richiamo e l'impostazione dei flussi ASCII, che rappresentano casi speciali poiché utilizzano flussi di byte con il presupposto implicito di singole tabelle codici conosciute (ASCII).  
  
 Inoltre, il driver JDBC fornisce il **sendStringParametersAsUnicode** proprietà della stringa di connessione. che può essere utilizzata per specificare che i parametri preparati per i dati di tipo carattere verranno inviati in formato ASCII or MBCS (Multi-byte Character Set) anziché Unicode. Per ulteriori informazioni sul **sendStringParametersAsUnicode** proprietà di stringa di connessione, vedere [impostando le proprietà di connessione](../../connect/jdbc/setting-the-connection-properties.md).  
  
### <a name="driver-incoming-conversions"></a>Conversioni in ingresso nel driver  
 I dati di tipo text Unicode provenienti dal server non devono essere convertiti. Vengono passati direttamente in formato Unicode. I dati non Unicode provenienti dal server vengono convertiti dalla tabella codici, a livello di database o di colonna, a Unicode. Per eseguire queste conversioni vengono utilizzate le routine di conversione JVM (Java Virtual Machine). Le conversioni vengono eseguite su tutti metodi per il richiamo di flussi String e Character tipizzati.  
  
 Se in JVM non è disponibile il supporto di tabella codici appropriato per i dati del database, verrà generata un'eccezione "La tabella codici XXX non è supportata dall'ambiente Java". Per risolvere il problema, è necessario installare il supporto completo per caratteri internazionali richiesto per tale JVM. Per un esempio, vedere la documentazione relative alle codifiche supportate nel sito Web Sun Microsystems.  
  
### <a name="driver-outgoing-conversions"></a>Conversioni in uscita dal driver  
 I dati di tipo carattere che passano dal driver al server possono essere ASCII o Unicode. Ad esempio, i nuovo JDBC 4.0 caratteri nazionali metodi, ad esempio metodi setNString, setNCharacterStream e setNClob di [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) e [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) classi, Invia sempre i valori dei parametri per il server in formato Unicode.  
  
 D'altra parte, i metodi dell'API caratteri non nazionali, ad esempio metodi setString, setCharacterStream e setClob di [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) e [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) classi inviare i relativi valori per il server in formato Unicode solo quando il **sendStringParametersAsUnicode** è impostata su "true", ovvero il valore predefinito.  
  
## <a name="non-unicode-parameters"></a>Parametri non Unicode  
 Per prestazioni ottimali con **CHAR**, **VARCHAR** o **LONGVARCHAR** tipo di parametri non Unicode, impostare il **sendStringParametersAsUnicode** proprietà su "false" stringa di connessione e utilizzare i metodi per caratteri non nazionali.  
  
## <a name="formatting-issues"></a>Problemi di formattazione  
 Per data, ora e valuta, tutta la formattazione con i dati localizzati vengono eseguite a livello di linguaggio Java utilizzando l'oggetto delle impostazioni locali. e i vari metodi di formattazione per **data**, **calendario**, e **numero** tipi di dati. Nei rari casi in cui il driver JDBC deve passare dati dipendenti dalle impostazioni locali in un formato localizzato, viene utilizzato il formattatore appropriato con le impostazioni locali JVM predefinite.  
  
## <a name="collation-support"></a>Supporto delle regole di confronto  
 Il Driver JDBC 3.0 supporta tutte le regole di confronto supportate da [!INCLUDE[ssVersion2000](../../includes/ssversion2000_md.md)], [!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)]e le nuove regole di confronto o le nuove versioni di Windows, i nomi delle regole di confronto introdotte in [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)].  
  
 Per ulteriori informazioni sulle regole di confronto, vedere [Collation and Unicode Support](http://go.microsoft.com/fwlink/?LinkId=131366) e [windows_collation_name (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=131367) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] documentazione in linea.  
  
## <a name="using-international-domain-names-idn"></a>Utilizzo di International Domain Names (IDN)  
 JDBC Driver 6.0 per SQL Server supporta l'uso di Internationalized Domain Names (IDN) e può convertire un serverName Unicode in codifica compatibile con ASCII (Punycode) quando richiesto durante una connessione.  Se i nomi IDN vengono archiviati in Domain Name System (DNS) come stringhe ASCII in formato Punycode (specificato dal RFC 3490), abilitare la conversione del nome del server Unicode impostando la proprietà serverNameAsACE su true.  In caso contrario, se il servizio DNS è configurato per consentire l'utilizzo di caratteri Unicode, impostare la proprietà serverNameAsACE su false (impostazione predefinita).  Per le versioni precedenti del driver JDBC, è inoltre possibile convertire serverName in Punycode utilizzando [. ToAscii Java IDN](http://docs.oracle.com/javase/8/docs/api/java/net/IDN.html) metodi prima di impostare tale proprietà per una connessione.  
  
> [!NOTE]  
>  La maggior parte dei software resolver scritti per piattaforme non Windows si basano sugli standard Internet DSN ed è pertanto più facile utilizzare il formato Punycode per nomi IDN, mentre un Server DNS basato su Windows in una rete privata può essere configurato per consentire l'utilizzo di caratteri UTF-8 in base a ciascun server.  Per ulteriori informazioni, vedere [supporto dei caratteri Unicode](https://technet.microsoft.com/library/cc738403(v=ws.10).aspx).  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica del Driver JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  

