---
title: La gestione delle password (AccessToSQL) | Documenti Microsoft
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
ms.assetid: b099d0f9-dd37-4c87-8b6f-ed0177881ea4
caps.latest.revision: 13
author: sabotta
ms.author: carlasab
manager: lonnyb
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 036fcb15ce20a2e0370913b4548e02531e665190
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="managing-passwords-accesstosql"></a>La gestione delle password (AccessToSQL)
In questa sezione riguarda la protezione delle password di database e le procedure per importare o esportare tali tra server:  
  
1.  Protezione delle Password  
  
2.  L'esportazione o importazione di Password crittografata  
  
## <a name="securing-password"></a>Protezione delle Password  
SSMA consente di proteggere la password di un database.  
  
Per implementare una connessione sicura, usare la procedura seguente:  
  
Specificare una password valida utilizzando uno dei tre metodi seguenti:  
  
1.  **Testo non crittografato:** digitare la password del database dell'attributo value del nodo 'password'. Si trovi sotto il nodo della definizione di server nella sezione Server di file di script o file di connessione del server.  
  
    Le password in testo non crittografato non sono protette. Pertanto, si verificherà il seguente messaggio di avviso nell'output della console: *"Server &lt;id server&gt; password viene fornito in formato testo non crittografato non protetta, l'applicazione Console SSMA fornisce un'opzione per proteggere la password mediante crittografia, vedere l'opzione – securepassword SSMA file della Guida per ulteriori informazioni."*  
  
    **Le password crittografate:** la password specificata, in questo caso, è archiviata in formato crittografato nel computer locale in ProtectedStorage.ssma.  
  
    -   **Protezione delle password**  
  
        -   Eseguire il `SSMAforAccessConsole.exe` con il `–securepassword` e aggiungere l'opzione nella riga di comando passando il server di connessione o file script contenente il nodo password nella sezione di definizione di server.  
  
        -   Al prompt dei comandi, verrà chiesto di immettere la password del database e confermarla.  
  
            Gli ID di definizione di server e la password crittografata corrispondenti vengono archiviate in un file nel computer locale  
  
            Esempio 1:
            
                Specify password
                
                C:\SSMA\SSMAforAccessConsole.EXE –securepassword –add all –s "D:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\AssessmentReportGenerationSample.xml" –v "D:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ VariableValueFileSample.xml"
                
                Enter password for server_id 'XXX_1': xxxxxxx
                
                Re-enter password for server_id 'XXX_1': xxxxxxx  
            
            Esempio 2:
            
                C:\SSMA\SSMAforAccessConsole.EXE –securepassword –add "source_1,target_1" –c "D:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ServersConnectionFileSample.xml" – v "D:\Program Files\Microsoft SQL Server Migration Assistant for Access\Sample Console Scripts\ VariableValueFileSample.xml" -o
                
                Enter password for server_id 'source_1': xxxxxxx
                
                Re-enter password for server_id 'source_1': xxxxxxx
                
                Enter password for server_id 'target_1': xxxxxxx
                
                Re-enter password for server_id 'target _1': xxxxxxx  
  
    -   **Rimuovere le password crittografate**  
  
        Eseguire il `SSMAforAccessConsole.exe` con il`–securepassword` e `–remove` passa alla riga di comando passando l'ID del server, per rimuovere le password crittografate dal file di archiviazione protetto presentano nel computer locale.  
  
            C:\SSMA\SSMAforAccessConsole.EXE –securepassword –remove all
            C:\SSMA\SSMAforAccessConsole.EXE –securepassword –remove "source_1,target_1"  
  
    -   **Elenco di ID Server le cui password vengono crittografate**  
  
        Eseguire il SSMAforAccessConsole.exe con il `–securepassword` e `–list` passa alla riga di comando per elencare tutti gli ID server le cui password crittografate.  
  
            C:\SSMA\SSMAforAccessConsole.EXE –securepassword –list  
  
    > [!NOTE]  
    > 1.  La password in testo non crittografato indicato nel file di connessione di script o un server ha la precedenza sulla password crittografata nel file protetto.  
    > 2.  Quando è presente alcuna password nella sezione del file di connessione del server o del file di script server o se non è stato protetto nel computer locale, la console viene richiesto di immettere la password.  
  
## <a name="exporting-or-importing-encrypted-passwords"></a>L'esportazione o importazione di password crittografate  
L'applicazione Console di SSMA consente di esportare le password crittografate database presente in un file nel computer locale in un file protetto e viceversa. Consente di rendere la macchina password crittografate indipendenti. Funzionalità di esportazione legge l'id del server e la password da locale spazio di archiviazione protetto e Salva le informazioni in un file crittografato. L'utente viene richiesto di immettere la password per il file protetto. Verificare che la password immessa è di 8 caratteri o più. Il file protetto può essere trasferito in computer diversi. Funzionalità di importazione legge il server le informazioni di id e la password dal file protetto. L'utente viene richiesto di immettere la password per il file protetto e aggiunge le informazioni nell'archivio locale protetto.  


    Export password
    
    Enter password for protecting the exported file
    
    C:\SSMA\SSMAforAccessConsole.EXE –securepassword –export all "machine1passwords.file"
    
    Enter password for protecting the exported file: xxxxxxxx
    
    Please confirm password: xxxxxxxx
    
    C:\SSMA\SSMAforAccessConsole.EXE –p –e "AccessDB_1_1,Sql_1" "machine2passwords.file"
    
    Enter password for protecting the exported file: xxxxxxxx
    
    Please confirm password: xxxxxxxx  


    Import an encrypted password
    
    Enter password for protecting the imported file
    
    C:\SSMA\SSMAforAccessConsole.EXE –securepassword –import all "machine1passwords.file"
    
    Enter password to import the servers from encrypted file: xxxxxxxx
    
    Please confirm password: xxxxxxxx
    
    C:\SSMA\SSMAforAccessConsole.EXE –p –i "AccessDB_1,Sql_1" "machine2passwords.file"
    
    Enter password to import the servers from encrypted file: xxxxxxxx
    
    Please confirm password: xxxxxxxx  
  
## <a name="see-also"></a>Vedere anche  
[L'esecuzione la Console SSMA (accesso)](http://msdn.microsoft.com/en-us/aa1bf665-8dc0-4259-b36f-46ae67197a43)  
  

