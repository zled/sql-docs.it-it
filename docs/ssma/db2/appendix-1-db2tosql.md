---
title: Appendice - 1 (DB2ToSQL) | Documenti Microsoft
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-db2
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: c6a30367-d56f-4fcc-8920-c6a6b0335a67
caps.latest.revision: 6
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 38a0f497b44f1914ff904fd54d7bea433e6de5c7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="appendix---1-db2tosql"></a>Appendice - 1 (DB2ToSQL)
Anteprima della Console di SSMA opzioni riga di comando:  
  
|Sl. No.|Opzione|Obbligatorio?|Passare l'argomento|Valori consentiti|  
|-----------|----------|-------------|-------------------|--------------------|  
|1|-s/script|Sì|scriptfile|Nome del file XML valido.<br /><br />File di definizione di Script di console.|  
|2|variabile o - v|no|variablevaluefile|Nome del file XML valido.<br /><br />Se le variabili vengono utilizzate nel file di script, è necessario specificare questo file.|  
|3|-c/serverconnection|no|serverconnectionfile|Nome del file XML valido.<br /><br />Questo file contiene informazioni sulla connessione server.|  
|4|-x/xmloutput|no|xmloutputfile|Questa opzione indica l'output della console in formato XML. Se questa opzione non è specificata, l'output predefinito è in formato testo.<br /><br />Se non viene specificato xmloutputfile, output XML viene indirizzato a STDOUT.<br /><br />Xmloutputfile è il nome del file in cui viene scritto l'output della console in formato XML.|  
|5|-l o di log|no|logfile|Nome file valido.|  
|6|e-/ projectenvironment|no|projectenvironmentfolder|Nome di cartella valido contenente i file dell'ambiente di progetto SSMA.|  
|7|-p/securepassword|no|-un/Aggiungi {< server_id > [,... n] &#124; tutti i} – c&#124;serverconnection < file di connessione server > [-v&#124;variabile < variabile-valore-file >] [-o/sovrascrivere]<br /><br />o<br /><br />-un/Aggiungi {< server_id > [,... n] &#124; tutti i} – s&#124;script < file di script > [-v&#124;variabile < variabile-valore-file >] [-o/sovrascrivere]<br /><br />– r/Rimuovi {< server_id > [,... n] &#124; tutti i}<br /><br />-l/elenco<br /><br />– e/esportazione {< server-id > [,... n] &#124; tutti i} < crittografato della password - file ><br /><br />-i / importazione {< server-id > [,... n] &#124; tutti i} < crittografati-password-file >|Se specificato, è necessario non combinare questa opzione con le altre opzioni.<br /><br />ID del server: specificato un ID univoco per un server {stringa}<br /><br />file di connessione server: file di definizione del server (serverconnectionfile o scriptfile).<br /><br />file di variabile-valore: è un file di definizione della variabile e usato nel file di connessione server.<br /><br />: file di password crittografata: è un file di password server crittografato con una specificata dall'utente-passphrase.|  
|8|-?|no|Non applicabile|Non applicabile|  
  
## <a name="see-also"></a>Vedere anche  
[Esecuzione della console SSMA](http://msdn.microsoft.com/en-us/ce63f633-067d-4f04-b8e9-e1abd7ec740b)  
  
