---
title: Certificato PDW Provisioning (Analitica piattaforma sistema)
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.technology: mpp-data-warehouse
ms.custom: ''
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0a423b7d-c6ea-45c1-80b0-26758170594c
caps.latest.revision: 22
ms.openlocfilehash: a08a739c490f0cbd49f615441f557d5200107443
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2018
---
# <a name="pdw-certificate-provisioning"></a>Provisioning di certificati PDW
Il **Provisioning certificato PDW** pagina del sistema di piattaforma Analitica**Configuration Manager** Importa o rimuove il certificato utilizzato dall'area PDW. Utilizzando, un certificato per crittografare le connessioni consentono comunicazioni protette al nodo di controllo tramite client di SQL Server, gli strumenti che utilizzano il driver SQL Server PDW, il [Console di amministrazione](monitor-the-appliance-by-using-the-admin-console.md), e il caricamento di Integration Services.  
  
## <a name="prerequisites"></a>Prerequisiti  
Prima di installare il certificato, eseguire le operazioni seguenti:  
  
1.  Ottenere un certificato di protezione. Se è necessario ulteriori informazioni su come ottenere un certificato protetto, contattare il supporto Microsoft.  
  
2.  Salvare il certificato al nodo di controllo in un file PFX protetto da password.  
  
## <a name="for-security-reasons-obtain-a-trusted-certificate"></a>Per motivi di sicurezza, ottenere un certificato attendibile  
SQL Server PDW supporta l'utilizzo di un certificato per crittografare le connessioni sul nodo di controllo. incluse le connessioni per il **Console di amministrazione**.  
  
Per impostazione predefinita, il **Console di amministrazione** include un certificato autofirmato che fornisce privacy, ma non l'autenticazione server. Questo può rendere vulnerabile a un attacco man-in-the-middle le comunicazioni. Quando un utente si connette alla Console di amministrazione utilizzando il certificato autofirmato, Internet Explorer viene restituito l'errore: "Si verifica un problema con il certificato di sicurezza del sito Web".  
  
Anche se la connessione tramite il certificato autofirmato crittografa i dati in transito tra il client e il server, la connessione è ancora al rischio di attacchi da.  
  
> [!WARNING]  
> Gli amministratori di accessorio immediatamente devono acquisire un certificato concatenato a un'autorità di certificazione riconosciuta dai client, per avere una connessione protetta e rimuovere l'errore che segnala Internet Explorer.  
  
Il percorso di certificazione deve contenere il nome di dominio completo che viene eseguito il mapping al nodo di controllo indirizzo IP del Cluster (scelta consigliata) o il nome digitato dagli utenti, le barre di indirizzo del browser per accedere il **Console di amministrazione**.  
  
Utilizzare il sistema di piattaforma Analitica**Configuration Manager** per aggiungere o rimuovere il certificato attendibile. Direttamente tramite lo strumento di configurazione certificato Microsoft Windows HTTP Services (**winHttpCertCfg.exe**) per gestire il certificato non è supportata.  
  
## <a name="import-or-remove-the-certificate"></a>Importare o rimuovere il certificato  
Le istruzioni seguenti viene illustrato come importare o rimuovere il certificato del dispositivo.  
  
### <a name="to-import-the-certificate"></a>Per importare il certificato  
  
1.  Avviare il **Configuration Manager**. Per altre informazioni, vedere [avviare Gestione configurazione &#40;Analitica Platform System&#41;](launch-the-configuration-manager.md).  
  
2.  Nel riquadro sinistro della finestra di **Configuration Manager**, espandere **Parallel Data Warehouse topologia**e quindi fare clic su **certificati**.  
  
3.  Selezionare **importare un certificato e configurare il dispositivo per usarlo**, quindi fare clic su **Sfoglia** per individuare e selezionare il file del certificato.  
  
4.  Immettere la password per il certificato di **Password** campo.  
  
5.  Fare clic su **applica** per configurare il certificato per l'applicazione.  
  
SQL Server PDW, non crittograferà connessione corrente utilizzando il certificato importato, ma utilizzerà il certificato per le nuove connessioni.  
  
### <a name="to-remove-the-previously-imported-certificate"></a>Per rimuovere il certificato importato in precedenza  
  
1.  Avviare il **Configuration Manager**. Per altre informazioni, vedere [avviare Gestione configurazione &#40;Analitica Platform System&#41;](launch-the-configuration-manager.md).  
  
2.  Nel riquadro sinistro della finestra di **Configuration Manager**, espandere **Parallel Data Warehouse topologia**e quindi fare clic su **certificati**.  
  
3.  Selezionare **rimuovere qualsiasi certificato di provisioning nel dispositivo**.  
  
4.  Fare clic su **applica** per rimuovere il certificato importato in precedenza dal dispositivo.  
  
SQL Server PDW continuerà a crittografare le connessioni correnti, ma non utilizzerà la rimozione del certificato per le nuove connessioni.  
  
![Certificato PDW strumento DWConfig](./media/pdw-certificate-provisioning/SQL_Server_PDW_DWConfig_ApplPDWCert.png "SQL_Server_PDW_DWConfig_ApplPDWCert")  
  
## <a name="see-also"></a>Vedere anche  
[Avviare Gestione configurazione &#40;Analitica Platform System&#41;](launch-the-configuration-manager.md)  
<!-- MISSING LINKS [HDInsight Certificate Provisioning &#40;Analytics Platform System&#41;](hdinsight-certificate-provisioning.md)  -->  
  
