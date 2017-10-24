---
title: Scrittura di un gestore personalizzato | Documenti Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataFactory handler in RDS [ADO]
- customized handler in RDS [ADO]
ms.assetid: d447712a-e123-47b5-a3a4-5d366cfe8d72
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 445f0d8d7a870ceda6cf4028b0cebe9264ed8358
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="writing-your-own-customized-handler"></a>Scrittura di un gestore personalizzato
Si consiglia di scrivere un gestore personalizzato se si è un amministratore di server IIS che richiede il supporto RDS predefinito, ma maggiore controllo sulle richieste degli utenti e diritti di accesso.  
  
 Il MSDFMAP. Gestore implementa il **IDataFactoryHandler** interfaccia.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server di servizi desktop remoto non sono più inclusi nel sistema operativo Windows (vedere Windows 8 e [Guida alla compatibilità tra Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) per altri dettagli). Componenti client di servizi desktop remoto verranno rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano servizi desktop remoto devono eseguire la migrazione a [servizio dati WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="idatafactoryhandler-interface"></a>Interfaccia IDataFactoryHandler  
 Questa interfaccia dispone di due metodi, **GetRecordset** e **Riconnetti**. Entrambi i metodi richiedono che il [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) impostata su **adUseClient**.  
  
 Entrambi i metodi accettano gli argomenti visualizzati dopo la prima virgola nel "**gestore =**" parola chiave. Ad esempio, `"Handler=progid,arg1,arg2;"` passerà una stringa dell'argomento `"arg1,arg2"`, e `"Handler=progid"` passa un argomento null.  
  
## <a name="getrecordset-method"></a>Metodo GetRecordset  
 Questo metodo esegue una query origine dati e crea un nuovo [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto utilizzando gli argomenti forniti. Il **Recordset** deve essere aperto con **adLockBatchOptimistic** e non deve essere aperto in modo asincrono.  
  
### <a name="arguments"></a>Argomenti  
 ***Conn*** la stringa di connessione.  
  
 ***args*** gli argomenti per il gestore.  
  
 ***query*** il testo del comando per eseguire una query.  
  
 ***ppRS*** il puntatore in cui il **Recordset** deve essere restituito.  
  
## <a name="reconnect-method"></a>Riconnettersi (metodo)  
 Questo metodo aggiorna l'origine dati. Viene creato un nuovo [connessione](../../../ado/reference/ado-api/connection-object-ado.md) oggetto e associa il determinato **Recordset**.  
  
### <a name="arguments"></a>Argomenti  
 ***Conn*** la stringa di connessione.  
  
 ***args*** gli argomenti per il gestore.  
  
 ***le prenotazioni permanenti*** A **Recordset** oggetto.  
  
## <a name="msdfhdlidl"></a>msdfhdl  
 Questa è la definizione di interfaccia per **IDataFactoryHandler** che compare nella **msdfhdl** file.  
  
```  
[  
  uuid(D80DE8B3-0001-11d1-91E6-00C04FBBBFB3),  
  version(1.0)  
]  
library MSDFHDL  
{  
    importlib("stdole32.tlb");  
    importlib("stdole2.tlb");  
  
    // TLib : Microsoft ActiveX Data Objects 2.0 Library  
    // {00000200-0000-0010-8000-00AA006D2EA4}  
    #ifdef IMPLIB  
    importlib("implib\\x86\\release\\ado\\msado15.dll");  
    #else  
    importlib("msado20.dll");  
    #endif  
  
    [  
      odl,  
      uuid(D80DE8B5-0001-11d1-91E6-00C04FBBBFB3),  
      version(1.0)  
    ]  
    interface IDataFactoryHandler : IUnknown  
    {  
HRESULT _stdcall GetRecordset(  
      [in] BSTR conn,  
      [in] BSTR args,  
      [in] BSTR query,  
      [out, retval] _Recordset **ppRS);  
  
// DataFactory will use the ActiveConnection property  
// on the Recordset after calling Reconnect.  
   HRESULT _stdcall Reconnect(  
      [in] BSTR conn,  
      [in] BSTR args,  
      [in] _Recordset *pRS);  
    };  
};  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Collegare il File di personalizzazione](../../../ado/guide/remote-data-service/customization-file-connect-section.md)   
 [Sezione Log File di personalizzazione](../../../ado/guide/remote-data-service/customization-file-logs-section.md)   
 [Sezione relativa alla personalizzazione File SQL](../../../ado/guide/remote-data-service/customization-file-sql-section.md)   
 [Sezione UserList File di personalizzazione](../../../ado/guide/remote-data-service/customization-file-userlist-section.md)   
 [Personalizzazione di DataFactory](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Impostazioni Client richieste](../../../ado/guide/remote-data-service/required-client-settings.md)   
 [Informazioni sul file di personalizzazione](../../../ado/guide/remote-data-service/understanding-the-customization-file.md)



