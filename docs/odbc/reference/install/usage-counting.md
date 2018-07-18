---
title: Il conteggio di utilizzo | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- usage counts [ODBC]
- file usage counts [ODBC]
- installing ODBC components [ODBC], usage counts
- subkeys [ODBC], usage counts
ms.assetid: 0678aee9-8256-463c-89dd-77b1a0dfdd60
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 51d1acca922245a4b57ecd30428e0b4079327e29
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32916551"
---
# <a name="usage-counting"></a>Il conteggio di utilizzo
> [!NOTE]  
>  A partire da Windows XP e Windows Server 2003, ODBC è incluso nel sistema operativo Windows. Solo nelle versioni precedenti di Windows è necessario installare ODBC in modo esplicito.  
  
 Due tipi di conteggi dell'utilizzo vengono mantenuti nel Registro di sistema per ogni componente: un conteggio di utilizzo del componente e uno o più conteggi dell'utilizzo di file facoltativo. Il conteggio di utilizzo del componente consente l'installazione DLL mantenere le voci del Registro di sistema. Viene archiviato nel valore UsageCount in ODBC Core, driver e le sottochiavi di funzione di conversione. Per il formato del valore di UsageCount e ulteriori informazioni su queste sottochiavi, vedere [le voci del Registro di sistema per i componenti ODBC](../../../odbc/reference/install/registry-entries-for-odbc-components.md).  
  
 Alla prima installazione di un componente, il programma di installazione DLL crea una sottochiave per tale e imposta i dati per il valore UsageCount nella sottochiave su 1. Quando il componente verrà installato nuovamente, il programma di installazione DLL incrementa il conteggio di utilizzo. Quando il componente viene rimosso, il programma di installazione DLL decrementa l'utilizzo di conteggio di. Se il conteggio di utilizzo scende a 0, il programma di installazione DLL rimuove la sottochiave per il componente.  
  
> [!CAUTION]  
>  Un'applicazione non rimuovere fisicamente i file di Driver Manager quando il conteggio di utilizzo del componente e il conteggio di utilizzo file raggiunge zero.  
  
 Utilizzo di file determinare conteggi debba effettivamente essere copiato o di un file eliminato come anziché aumentando o diminuendo il conteggio di utilizzo. Questo è importante poiché componenti ODBC e pertanto i file nei componenti ODBC, vengono condivisi e possono essere installati o rimosso da una varietà di applicazioni. L'applicazione è possibile eliminare i file di driver e i traduttori se il conteggio di utilizzo del componente e il conteggio di utilizzo file raggiunge zero. File di Gestione driver non dovrebbe, eliminare quando sia il conteggio di utilizzo del componente e il conteggio di utilizzo di file hanno raggiunto lo zero, perché questi file possono essere utilizzati da altre applicazioni che non hanno incrementato il conteggio di utilizzo di file.  
  
> [!NOTE]  
>  Conteggi dell'utilizzo di file sono facoltativi in Microsoft® WindowsNT®/Windows 2000.  
  
 Conteggi dell'utilizzo di file vengono gestiti dal programma di installazione dopo avere chiamato **SQLInstallDriverManager**, **SQLInstallDriverEx**, **SQLInstallTranslatorEx**, **SQLRemoveDriverManager**, **SQLRemoveDriver**, o **SQLRemoveTranslator**.  
  
 Alla prima installazione di un componente, il programma di installazione o un programma di installazione DLL crea un valore nella chiave seguente per ogni file in tale componente che non sia già nel sistema:  
  
> [!NOTE]  
>  HKEY_LOCAL_MACHINE  
>   
>  SOFTWARE  
>   
>  Microsoft  
>   
>  Windows  
>   
>  CurrentVersion  
>   
>  SharedDlls  
  
 Imposta i dati per i valori su 1 e copia il file del sistema. Quando il componente verrà installato nuovamente, il programma di installazione o un programma di installazione DLL incrementa il conteggio di utilizzo. Quando viene rimosso il componente, decrementa DLL del programma di installazione o del programma di installazione il conteggio di utilizzo. Se qualsiasi numero di utilizzi scende a 0, il programma di installazione o un programma di installazione DLL rimuove il valore per il file e, se il componente è un driver o una funzione di conversione, Elimina il file. File di Gestione driver non devono essere eliminati.  
  
 Nella tabella seguente è riportato il formato del valore del conteggio di utilizzo di file.  
  
|Nome|Tipo di dati|data|  
|----------|---------------|----------|  
|*percorso completo*|REG_DWORD|*count*|  
  
 Ad esempio, si supponga che un driver per Informix utilizza i file Infrmx32.dll e Infrmx32.hlp e si supponga che questo driver è stato installato due volte. I valori nella sottochiave SharedDlls per il driver Informix sarà come segue:  
  
```  
C:\WINDOWS\SYSTEM32\INFRMX32.DLL : REG_DWORD : 0x2  
C:\WINDOWS\SYSTEM32\INFRMX32.HLP : REG_DWORD : 0x2  
```
