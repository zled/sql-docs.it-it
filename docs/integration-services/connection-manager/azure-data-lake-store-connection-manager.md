---
title: "Gestione connessioni di Azure Data Lake Store | Microsoft Docs"
ms.custom: ""
ms.date: "03/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SQL13.DTS.DESIGNER.AFPADLSCM.F1"
  - "sql14.dts.designer.afpadlscm.f1"
ms.assetid: f4c44553-0f08-4731-ac47-7534990b8c8d
caps.latest.revision: 7
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 5
---
# Gestione connessioni di Azure Data Lake Store
  La **Gestione connessioni di Azure Data Lake Store** consente a un pacchetto SSIS di connettersi a un servizio di Azure Data Lake Store tramite due tipi di autenticazione: identità utente Azure AD e identità del servizio di Azure Active Directory.  
  
 La **Gestione connessioni di Azure Data Lake Store** è un componente del Feature Pack di SQL Server Integration Services (SSIS) per Azure per SQL Server 2016. Scaricare il Feature Pack [qui](http://go.microsoft.com/fwlink/?LinkID=626967).  

>   [!NOTE] Per assicurarsi che la Gestione connessioni di Azure Data Lake Store e che i componenti che la usano, cioè l'origine e la destinazione di Azure Data Lake Store, possano connettersi ai servizi, scaricare la versione del Feature Pack di Azure più recente da [qui](https://www.microsoft.com/download/details.aspx?id=49492). 
 
## <a name="configure-the-azure-data-lake-store-connection-manager"></a>Configurare la Gestione connessioni di Azure Data Lake Store

 
1.  Nella finestra di dialogo **Aggiungi gestione connessione SSIS** selezionare **AzureDataLake** e fare clic su **Aggiungi**.  
  
2.  Nella finestra di dialogo dell'editor della Gestione connessioni di Azure Data Lake Store digitare l'URL host di Azure Data Lake Store nel campo **ADLS Host** (Host ADLS). Ad esempio: https://test.azuredatalakestore.net o test.azuredatalakestore.net.
  
3.  Scegliere il tipo di autenticazione corrispondente per accedere ai dati di Azure Data Lake Store.

    1.  Se si seleziona l'opzione di autenticazione **Identità utente Azure AD**, eseguire le operazioni seguenti:
        1. Specificare i valori per i campi **Nome utente** e **Password**. 
    
        2. Fare clic su **Test connessione** per testare la connessione. Se l'utente e l'amministratore tenant non hanno mai consentito prima a SSIS di accedere ai dati di Azure Data Lake Store, è necessario fare clic sul pulsante **Accetta** per consentire a SSIS di accedere ai dati di Azure Data Lake Store nella finestra di pop up separata. Per altre informazioni su questa esperienza di consenso, vedere [Integrazione di applicazioni con Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-integrating-applications#updating-an-application).
    
        >   [!NOTE] Per l'opzione di autenticazione Identità utente Azure AD, l'autenticazione a più fattori e account Microsoft NON è supportata.
    
    2. Se si seleziona l'opzione di autenticazione **Identità del servizio di Azure AD**, eseguire le operazioni seguenti:
        1. Creare un'applicazione e un'entità servizio di AAD che possano accedere alle risorse di Azure Data Lake.
    
        2. Assegnare le autorizzazioni corrispondenti all'applicazione AAD per accedere alle risorse di Azure Data Lake. Per altre informazioni su questa opzione di autenticazione, vedere [Use portal to create Active Directory application and service principal that can access resources](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-create-service-principal-portal) (Usare il portale per creare applicazioni ed entità servizio di Active Directory che possano accedere alle risorse).
    
        3. Specificare i valori per **ID client**, **Chiave privata** e **Nome del tenant**.
    
        4. Fare clic su **Test connessione** per testare la connessione.  
  
6.  Scegliere **OK** per chiudere la finestra di dialogo.  
  
    È possibile visualizzare le proprietà del componente Gestione connessione create nella finestra **Proprietà** .  
  
  