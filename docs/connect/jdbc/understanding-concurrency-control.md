---
title: Informazioni sul controllo della concorrenza | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 98b7dabe-9b12-4e1d-adeb-e5b5cb0c96f3
caps.latest.revision: 24
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 52c954cb3acc87753f9ede5a0fc786bd9ed9b755
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="understanding-concurrency-control"></a>Informazioni sul controllo della concorrenza
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Per controllo della concorrenza si intendono le diverse tecniche utilizzate per mantenere l'integrità del database quando più utenti aggiornano le righe contemporaneamente. Una concorrenza non corretta può causare problemi come letture dirty, letture fantasma e letture non ripetibili. Il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] fornisce interfacce per tutte le tecniche di concorrenza utilizzate da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] per risolvere questi problemi.  
  
> [!NOTE]  
>  Per ulteriori informazioni su [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] concorrenza, vedere "Gestione di accesso ai dati simultaneo" nella [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] documentazione in linea.  
  
## <a name="remarks"></a>Osservazioni  
 Il driver JDBC supporta i tipi di concorrenza seguenti:  
  
|Tipo di concorrenza|Caratteristiche|Blocchi di riga|Description|  
|----------------------|---------------------|---------------|-----------------|  
|CONCUR_READ_ONLY|Read Only|No|Gli aggiornamenti eseguiti tramite il cursore non sono consentiti e sulle righe del set di risultati non viene mantenuto attivo alcun blocco.|  
|CONCUR_UPDATABLE|Ottimistica di lettura e scrittura|No|Si presuppone che le contese tra le righe nel database siano improbabili, ma possibili. L'integrità delle righe viene verificata tramite confronto del timestamp.|  
|CONCUR_SS_SCROLL_LOCKS|Pessimistica di lettura e scrittura|Sì|Si presuppone che le contese tra le righe nel database siano probabili. L'integrità delle righe viene assicurata tramite i blocchi di riga.|  
|CONCUR_SS_OPTIMISTIC_CC|Ottimistica di lettura e scrittura|No|Si presuppone che le contese tra le righe nel database siano improbabili, ma possibili. L'integrità delle righe viene verificata tramite confronto del timestamp.<br /><br /> Per [!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)] e versioni successive, il server modifica questa impostazione in CONCUR_SS_OPTIMISTIC_CCVAL se nella tabella non contiene una colonna timestamp.<br /><br /> Per [!INCLUDE[ssVersion2000](../../includes/ssversion2000_md.md)], se la tabella sottostante contiene una colonna timestamp, viene utilizzato OPTIMISTIC WITH ROW VERSIONING anche se viene specificato l'opzione OPTIMISTIC WITH VALUES. Se si specifica l'opzione OPTIMISTIC WITH ROW VERSIONING e nella tabella non sono incluse colonne timestamp, viene utilizzata l'opzione OPTIMISTIC WITH VALUES.|  
|CONCUR_SS_OPTIMISTIC_CCVAL|Ottimistica di lettura e scrittura|No|Si presuppone che le contese tra le righe nel database siano improbabili, ma possibili. L'integrità delle righe viene verificata tramite confronto dei dati della riga.|  
  
## <a name="result-sets-that-are-not-updateable"></a>Set di risultati non aggiornabili  
 Un set di risultati aggiornabile è un set di risultati in cui è possibile inserire, aggiornare ed eliminare righe. Nei casi seguenti, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] non è possibile creare un cursore aggiornabile. e viene generata l'eccezione "Il set di risultati non è aggiornabile".  
  
|Causa|Description|Rimedio|  
|-----------|-----------------|------------|  
|L'istruzione non viene creata utilizzando la sintassi JDBC 2.0 (o versioni successive)|In JDBC 2.0 sono stati introdotti nuovi metodi per la creazione di istruzioni. Se viene utilizzata la sintassi JDBC 1.0, il set di risultati per impostazione predefinita è di sola lettura.|Specificare il tipo di set di risultati e la concorrenza in fase di creazione dell'istruzione.|  
|L'istruzione viene creata utilizzando TYPE_SCROLL_INSENSITIVE|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]Crea un cursore snapshot statico. Il cursore è disconnesso dalle righe della tabella sottostante per proteggerlo dagli aggiornamenti apportati alle righe da altri utenti.|Utilizzare TYPE_SCROLL_SENSITIVE, TYPE_SS_SCROLL_KEYSET, TYPE_SS_SCROLL_DYNAMIC o TYPE_FORWARD_ONLY con CONCUR_UPDATABLE per evitare di creare un cursore statico.|  
|La struttura della tabella non consente un cursore di tipo KEYSET o DYNAMIC|La tabella sottostante non dispone di chiavi univoche per consentire [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] per identificare in modo univoco una riga.|Aggiungere chiavi univoche alla tabella per consentire l'identificazione univoca di ogni riga.|  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione dei risultati set con il Driver JDBC](../../connect/jdbc/managing-result-sets-with-the-jdbc-driver.md)  
  
  
