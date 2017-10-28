---
title: Appendice - 1 (AccessToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 00665e16-2990-4bfc-8e17-d97ca9fb4999
caps.latest.revision: 9
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 4885ae2592285cdd1e948810de7c1e786afb9134
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="appendix---1-accesstosql"></a>Appendice - 1 (AccessToSQL)
Anteprima della Console di SSMA opzioni riga di comando:  
  
|SL. No.|Opzione|Obbligatorio?|Passare l'argomento|Valori consentiti|  
|-----------|----------|-------------|-------------------|--------------------|  
|1|-s/script|Sì|scriptfile|Nome del file XML valido.<br /><br />File di definizione di Script di console.|  
|2|variabile o - v|No|variablevaluefile|Nome del file XML valido. Se le variabili vengono utilizzate nel file di script, è necessario specificare questo file.|  
|3|-c/serverconnection|No|serverconnectionfile|Nome del file XML valido. Questo file contiene informazioni sulla connessione server.|  
|4|-x / xmloutput|No|xmloutputfile|Questa opzione indica l'output della console in formato XML. Se questa opzione non è specificata, l'output predefinito è in formato testo.<br /><br />Se non viene specificato xmloutputfile, output XML viene indirizzato a STDOUT.<br /><br />Xmloutputfile è il nome del file in cui viene scritto l'output della console in formato XML.|  
|5|-l o di log|No|logfile|Nome file valido.|  
|6|e-/ projectenvironment|No|projectenvironmentfolder|Nome di cartella valido contenente i file dell'ambiente di progetto SSMA.|  
|7|-p/securepassword|No|-/ Aggiunge {< server_id > [,... n] &#124; tutti} – c &#124; serverconnection < file di connessione server > [-v &#124; variabile < variabile-valore-file >] [-o/sovrascrivere]<br /><br />o<br /><br />-/ Aggiunge {< server_id > [,... n] &#124; tutti} – s &#124; lo script < file di script > [-v &#124; variabile < variabile-valore-file >] [-o/sovrascrivere]<br /><br />– r/Rimuovi {< server_id > [,... n] &#124; tutti}<br /><br />-l/elenco<br /><br />e – / esportazione {< id-server > [,... n] &#124; tutti} < password crittografate - file ><br /><br />-i / importazione {< id-server > [,... n] &#124; tutti} < crittografati password-file >|Se specificato, è necessario non combinare questa opzione con le altre opzioni.<br /><br />ID del server: specificato un ID univoco per un server {stringa}<br /><br />file di connessione server: file di definizione del server (serverconnectionfile o scriptfile).<br /><br />file di variabile-valore: è un file di definizione della variabile e usato nel file di connessione server.<br /><br />: file di password crittografata: è un file di password server crittografato con una specificata dall'utente-passphrase.|  
|8|-?|No|Non applicabile|Non applicabile|  
  
## <a name="see-also"></a>Vedere anche  
[L'esecuzione la Console SSMA (accesso)](http://msdn.microsoft.com/en-us/aa1bf665-8dc0-4259-b36f-46ae67197a43)  
  

