---
title: Confrontare opzioni per l&quot;archiviazione di BLOB (SQL Server) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-blob
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6038697b-36a9-49e8-a02a-2ad9e2e60e5a
caps.latest.revision: 10
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 98538bd77f81cd6a1f16857b70a866ee3f6d171a
ms.lasthandoff: 04/11/2017

---
# <a name="compare-options-for-storing-blobs-sql-server"></a>Confrontare opzioni per l'archiviazione di BLOB (SQL Server)
  Vengono descritte e confrontate le opzioni disponibili per l'archiviazione di file e documenti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
##  <a name="Expectations"></a> Archiviazione di file nel database: vantaggi e comportamenti previsti  
 Nella realtà un'ampia percentuale di dati aziendali non è strutturata e generalmente viene archiviata come file e documenti in file system. La maggior parte di questi dati viene prodotta, gestita e utilizzata da applicazioni che accedono ai file tramite API Windows. Solitamente le aziende mantengono questi dati nel file system, archiviando i metadati correlati per i file in un database relazionale.  
  
 L'integrazione dei dati non strutturati nel database relazionale offre vantaggi significativi. Tra i vantaggi offerti è incluso quanto segue:  
  
-   Integrazione di archiviazione e funzionalità di gestione dei dati come ad esempio backup.  
  
-   Servizi integrati quali ricerca full-text e ricerca semantica su dati e metadati.  
  
-   Facilità di amministrazione e gestione dei criteri sui dati non strutturati.  
  
 Per la maggior parte, tuttavia, l'archiviazione dei dati non strutturati in un database relazionale non era utile. In precedenza non era possibile eseguire le applicazioni esistenti basate su Windows sulla base di sistemi relazionali. Non è pratico riscrivere applicazioni consolidate (come ad esempio Microsoft Word o Adobe Reader) al fine di eseguirle sulla base delle API del database relazionale. Tali applicazioni semplicemente prevedono l'accessibilità ai dati attraverso le API di Windows. In altri termini, i comportamenti previsti sono i seguenti:  
  
-   Le transazioni di database non sono riconosciute né richieste dalle applicazioni di Windows.  
  
-   Le applicazioni di Windows richiedono compatibilità con le API del file system per i dati di file e directory.  
  
##  <a name="Filestream"></a> FILESTREAM  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dispone già della funzione FILESTREAM, che fornisce funzionalità di archiviazione, gestione e flusso dati efficienti per i dati non strutturati archiviati come file nel file system. Una soluzione FILESTREAM, tuttavia, richiede programmazione personalizzata e non soddisfa i requisiti per la piena compatibilità delle applicazioni Windows descritta sopra.  
  
##  <a name="FileTables"></a> FileTable  
 La caratteristica FileTable si basa sulle funzionalità FILESTREAM esistenti per consentire ai clienti aziendali di archiviare dati di file non strutturati e gerarchie di directory in un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , soddisfacendo i requisiti per l'accesso non transazionale e la compatibilità delle applicazioni Windows per i dati basati su file.  
  
##  <a name="CompareFileTable"></a> Confronto tra FILESTREAM e tabelle FileTable  
  
|Funzionalità|Soluzione file server e database|Soluzione FILESTREAM|Soluzione FileTable|  
|-------------|---------------------------------------|-------------------------|------------------------|  
|**Singola soluzione per le attività di gestione**|No|Sì|**Sì**|  
|**Singolo set di servizi**: ricerca, creazione di report, esecuzione di query e così via|No|Sì|**Sì**|  
|**Modello di sicurezza integrata**|No|Sì|**Sì**|  
|**Aggiornamenti sul posto di dati FILESTREAM**|Sì|No|**Sì**|  
|**Gerarchia di file e directory gestita nel database**|No|No|**Sì**|  
|**Compatibilità delle applicazioni di Windows**|Sì|No|**Sì**|  
|**Accesso relazionale agli attributi dei file**|No|No|**Sì**|  
  
##  <a name="CompareRBS"></a> Confronto tra FILESTREAM e Archivio BLOB remoti (Remote BLOB Store, RBS)  
 Per un confronto tra queste due caratteristiche, vedere il post di blog del team RBS: [Confronto tra le funzionalità Archivio BLOB remoti e FILESTREAM di SQL Server](http://go.microsoft.com/fwlink/?LinkId=210317).  
  
##  <a name="more"></a> Ulteriori informazioni  
 [FILESTREAM &#40;SQL Server&#41;](../../relational-databases/blob/filestream-sql-server.md)  
 [FileTables &#40;SQL Server&#41;](../../relational-databases/blob/filetables-sql-server.md)  
 [Archivio BLOB remoto &#40;RBS&#41; &#40;SQL Server&#41;](../../relational-databases/blob/remote-blob-store-rbs-sql-server.md)  
  
