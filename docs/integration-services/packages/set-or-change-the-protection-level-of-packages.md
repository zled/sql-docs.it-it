---
title: "Impostazione o modifica del livello di protezione dei pacchetti | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "password [Integration Services]"
  - "pacchetti [Integration Services], sicurezza"
  - "sicurezza [Integration Services], livelli di protezione"
  - "livello di protezione dei pacchetti [Integration Services]"
ms.assetid: 904a5580-82ba-4a26-b0c5-d1c989975f61
caps.latest.revision: 10
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 10
---
# Impostazione o modifica del livello di protezione dei pacchetti
  Per controllare l'accesso al contenuto dei pacchetti e ai valori sensibili contenuti, ad esempio password, impostare il valore della proprietà **ProtectionLevel**. Per poter compilare il progetto, ai pacchetti contenuti in un progetto deve essere assegnato lo stesso livello di protezione del progetto. Se si modifica l'impostazione della proprietà **ProtectionLevel** nel progetto, è necessario aggiornare manualmente l'impostazione delle proprietà per i pacchetti.  
  
 Per informazioni su come determinare le impostazioni di **ProtectionLevel** appropriate per i pacchetti in relazione alle varie fasi del ciclo di vita, vedere [Controllo dell'accesso per dati sensibili nei pacchetti](../../integration-services/packages/access-control-for-sensitive-data-in-packages.md). Per informazioni generali sulle funzionalità di sicurezza in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], vedere [Panoramica della sicurezza &#40;Integration Services&#41;](../../integration-services/security/security-overview-integration-services.md).  
  
 Le procedure presenti in questo argomento descrivono come usare [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] o l'utilità della riga di comando dtutil per modificare la proprietà **ProtectionLevel**.  
  
> [!NOTE]  
>  Oltre alle procedure di questo argomento, è in genere possibile impostare o modificare la proprietà **ProtectionLevel** di un pacchetto quando si importa o esporta il pacchetto. È anche possibile modificare la proprietà **ProtectionLevel** di un pacchetto quando si usa l'Importazione/Esportazione guidata [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per salvare un pacchetto.  
  
### Per impostare o modificare il livello di protezione di un pacchetto in SQL Server Data Tools  
  
1.  Controllare i valori disponibili per la proprietà **ProtectionLevel** nell'argomento [Impostazione del livello di protezione dei pacchetti](../../integration-services/packages/access-control-for-sensitive-data-in-packages.md) e determinare il valore appropriato per il pacchetto.  
  
2.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] aprire il progetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] contenente il pacchetto.  
  
3.  Aprire il pacchetto nella finestra di progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)].  
  
4.  Se nella finestra Proprietà non sono riportate le proprietà del pacchetto, fare clic sull'area di progettazione.  
  
5.  Selezionare il valore adatto per la proprietà **ProtectionLevel** nel gruppo **Sicurezza** della finestra Proprietà.  
  
     Se si seleziona un livello di protezione che richiede una password, immettere la password come valore della proprietà **PackagePassword**.  
  
6.  Per salvare il pacchetto modificato, scegliere **Salva elementi selezionati** dal menu **File**.  
  
### Per impostare o modificare il livello di protezione dei pacchetti dal prompt dei comandi  
  
1.  Controllare i valori disponibili per la proprietà **ProtectionLevel** nell'argomento [Impostazione del livello di protezione dei pacchetti](../../integration-services/packages/access-control-for-sensitive-data-in-packages.md) e determinare il valore appropriato per il pacchetto.  
  
2.  Controllare i mapping per l'opzione **Encrypt** nell'argomento [Utilità dtutil](../../integration-services/dtutil-utility.md) e determinare il valore intero appropriato da usare come valore della proprietà **ProtectionLevel** selezionata.  
  
3.  Aprire la finestra del prompt dei comandi.  
  
4.  Al prompt dei comandi, passare alla cartella contenente il pacchetto o i pacchetti per cui si vuole impostare la proprietà **ProtectionLevel**.  
  
     Negli esempi di sintassi illustrati nel passaggio seguente si presuppone che questa cartella sia la cartella corrente.  
  
5.  Impostare o modificare il livello di protezione del pacchetto o dei pacchetti utilizzando un comando simile a quello degli esempi seguenti:  
  
    -   Il comando seguente imposta la proprietà **ProtectionLevel** di un pacchetto singolo nel file system sul livello 2, "Crittografa tutti i dati sensibili con una password", con la password "strongpassword":  
  
         `dtutil.exe /file "C:\Package.dtsx" /encrypt file;"C:\Package.dtsx";2;strongpassword`  
  
    -   Il comando seguente imposta la proprietà **ProtectionLevel** di tutti i pacchetti in una particolare cartella nel file system sul livello 2, "Crittografa tutti i dati sensibili con una password", con la password "strongpassword":  
  
         `for %f in (*.dtsx) do dtutil.exe /file %f /encrypt file;%f;2;strongpassword`  
  
         Se si utilizza un comando simile in un file batch, immettere il segnaposto del file "% f" come "%% f" nel file batch.  
  
## Vedere anche  
 [Utilità dtutil](../../integration-services/dtutil-utility.md)  
  
  