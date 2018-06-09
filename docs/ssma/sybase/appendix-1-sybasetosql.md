---
title: Appendice - 1 (SybaseToSQL) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Sybase Console,Appendix
ms.assetid: 6dcfd6d5-772c-4876-aa94-a7f43c4b9d59
caps.latest.revision: 9
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 4ab763de65866e714515dfdf1e0058a5cb9872aa
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2018
ms.locfileid: "34778030"
---
# <a name="appendix---1-sybasetosql"></a>Appendice - 1 (SybaseToSQL)
Anteprima della Console di SSMA opzioni riga di comando:  
  
|Sl. No.|Opzione|Obbligatorio?|Passare l'argomento|Valori consentiti|  
|-----------|----------|-------------|-------------------|--------------------|  
|1|-s/script|Sì|scriptfile|Nome del file XML valido.<br /><br />File di definizione di Script di console.|  
|2|variabile o - v|no|variablevaluefile|Nome del file XML valido.<br /><br />Se le variabili vengono utilizzate nel file di script, è necessario specificare questo file.|  
|3|-c/serverconnection|no|serverconnectionfile|Nome del file XML valido.<br /><br />Questo file contiene informazioni sulla connessione server.|  
|4|-x/xmloutput|no|xmloutputfile|Questa opzione indica l'output della console in formato XML. Se questa opzione non è specificata, l'output predefinito è in formato testo.<br /><br />Se non viene specificato xmloutputfile, output XML viene indirizzato a STDOUT.<br /><br />Xmloutputfile è il nome del file in cui viene scritto l'output della console in formato XML.|  
|5|-l o di log|no|logfile|Nome file valido.|  
|6|e-/ projectenvironment|no|projectenvironmentfolder|Nome di cartella valido contenente i file dell'ambiente di progetto SSMA.|  
|7|-p/securepassword|no|-un/Aggiungi {< server_id > [,... n] &#124; tutti i} – c&#124;serverconnection < file di connessione server > [-v&#124;variabile < variabile-valore-file >] [-o/sovrascrivere]<br /><br />o Gestione configurazione<br /><br />-un/Aggiungi {< server_id > [,... n] &#124; tutti i} – s&#124;script < file di script > [-v&#124;variabile < variabile-valore-file >] [-o/sovrascrivere]<br /><br />– r/Rimuovi {< server_id > [,... n] &#124; tutti i}<br /><br />-l/elenco<br /><br />– e/esportazione {< server-id > [,... n] &#124; tutti i} < crittografato della password - file ><br /><br />-i / importazione {< server-id > [,... n] &#124; tutti i} < crittografati-password-file >|Se specificato, è necessario non combinare questa opzione con le altre opzioni.<br /><br />ID del server: specificato un ID univoco per un server {stringa}<br /><br />file di connessione server: file di definizione del server (serverconnectionfile o scriptfile).<br /><br />file di variabile-valore: è un file di definizione della variabile e usato nel file di connessione server.<br /><br />: file di password crittografata: è un file di password server crittografato con una specificata dall'utente-passphrase.|  
|8|-?|no|Non applicabile|Non applicabile|  
  
## <a name="see-also"></a>Vedere anche  
[L'esecuzione la Console SSMA (Sybase)](http://msdn.microsoft.com/en-us/ea8950b7-fabc-4aa4-89f8-9573a2617d70)  
  
