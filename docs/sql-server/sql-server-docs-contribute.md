---
title: Come contribuire alla documentazione di SQL Server | Microsoft Docs
ms.date: 04/12/2018
ms.prod: sql
ms.prod_service: sql
ms.component: sql-non-specified
ms.reviewer: ''
ms.suite: sql
ms.custom: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: rothja
ms.author: jroth
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 41bdbc55a67865e195ea06a10610af8224edf06b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-contribute-to-sql-server-documentation"></a>Come contribuire alla documentazione di SQL Server

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md.md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Chiunque può contribuire alla documentazione di SQL Server. Si può contribuire, ad esempio, correggendo gli errori tipografici, suggerendo spiegazioni più chiare e migliorando la precisione dal punto di vista tecnico. Questo articolo illustra come iniziare a contribuire al contenuto e come funziona il processo.

Si può contribuire alla documentazione usando due flussi di lavoro principali:

|||
|---|---|
| [Apportare modifiche nel browser](#githubui) | Adatto per piccole e rapide modifiche degli articoli. |
| [Apportare modifiche a livello locale con gli strumenti](#tools) | Adatto per modifiche più complesse, modifiche che interessano più articoli e contributi frequenti a docs.microsoft.com. |

## <a id="githubui"></a> Apportare modifiche nel browser

I passaggi descritti di seguito consentono di apportare semplici modifiche al contenuto di SQL Server nel browser. L'intera procedura è documentata nell'articolo [Flusso di lavoro per i contributi a GitHub per modifiche minime o non frequenti](https://docs.microsoft.com/contribute/light-workflow).

1. Ogni articolo, incluso il presente, ha un pulsante **Modifica** a destra. Individuare un articolo da modificare e fare clic sul pulsante **Modifica** per iniziare.

   ![Pulsante Modifica per l'articolo SQL](./media/sql-server-docs-contribute/edit-sql-server-docs.png)

   Tutto il contenuto su docs.microsoft.com è gestito in vari repository GitHub. Quando si fa clic sul pulsante di modifica si passa all'articolo nel repository **sql-docs**. Oppure, se si sta modificando un articolo su SQL nella documentazione di Azure, si passa al repository **azure-docs**. 

1. Quindi, fare clic sull'icona a forma di matita in alto a destra nell'articolo in GitHub.

   ![Pulsante di modifica](./media/sql-server-docs-contribute/edit-button.png)

   > [!NOTE]
   > Per modificare un articolo è necessario accedere a GitHub. Se non si ha un account GitHub, vedere [Configurazione dell'account GitHub](https://docs.microsoft.com/contribute/get-started-setup-github). Dopo aver creato un nuovo account, è anche necessario verificare l'indirizzo di posta elettronica con GitHub prima di apportare modifiche.

1. Modificare l'articolo nel browser. Tutti gli articoli sono scritti in Markdown. Se occorre assistenza con il linguaggio Markdown, consultare le [informazioni di base su Markdown](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/). Un altro metodo di apprendimento è osservare in che modo viene eseguito il rendering del Markdown esistente negli articoli pubblicati.

1. Scorrere in basso fino alla parte inferiore della finestra di modifica, immettere un titolo per la modifica e fare clic sul pulsante **Propose file change** (Proponi modifica file).

   ![Proporre una richiesta pull](./media/sql-server-docs-contribute/propose-file-change.png)

1. Nella pagina successiva fare clic su **Create pull request** (Crea richiesta pull).

   ![Creare una richiesta pull](./media/sql-server-docs-contribute/create-pull-request.png)

1. Immettere un titolo e una descrizione per la richiesta pull. Quindi fare di nuovo clic su **Create pull request** (Crea richiesta pull).

   ![Creare una richiesta pull](./media/sql-server-docs-contribute/create-pull-request2.png)

A questo punto, per continuare con la procedura, seguire le indicazioni nei commenti della richiesta pull. Il processo di completamento e altri dettagli sono disponibili nella [guida per il collaboratore](https://docs.microsoft.com/contribute/light-workflow).

## <a id="tools"></a> Apportare modifiche a livello locale con gli strumenti

Un'altra opzione di modifica è creare un fork del repository **sql-docs** o **azure-docs** e clonarlo nel computer locale. È quindi possibile usare un editor di Markdown e un client Git per inviare le modifiche. Questo flusso di lavoro è ottimale per le modifiche più complesse o che interessano più file. È ideale inoltre per i collaboratori che inviano spesso contributi a docs.microsoft.com.

Per contribuire con questo metodo, vedere gli articoli seguenti:

- [Creare un account GitHub](https://docs.microsoft.com/contribute/get-started-setup-github)
- [Installare gli strumenti di creazione del contenuto](https://docs.microsoft.com/contribute/get-started-setup-tools)
- [Configurare un repository Git locale](https://docs.microsoft.com/contribute/get-started-setup-local)
- [Usare gli strumenti per collaborare](https://docs.microsoft.com/contribute/full-workflow)

Se si invia una richiesta pull con modifiche significative alla documentazione, verrà visualizzato un commento in GitHub che richiede di inviare un **contratto di licenza per contributi (CLA)** online. È necessario completare il modulo online affinché la richiesta pull possa essere accettata.

## <a name="recognition"></a>Riconoscimento

Se le modifiche vengono accettate, l'utente viene riconosciuto come collaboratore all'inizio dell'articolo.

![Riconoscimento del contributo al contenuto](./media/sql-server-docs-contribute/contribution-recognition.png)

## <a name="sql-docs-overview"></a>Panoramica di sql-docs

Questa sezione contiene informazioni aggiuntive sull'uso del repository **sql-docs**.

> [!IMPORTANT]
> Le informazioni di questa sezione sono specifiche per **sql-docs**. Se si modifica un articolo su SQL nella documentazione di Azure, vedere [il file Leggimi relativo al repository azure-docs su GitHub](https://github.com/MicrosoftDocs/azure-docs/blob/master/README.md).

Il repository [sql-docs](https://github.com/MicrosoftDocs/sql-docs) usa alcune cartelle standard per organizzare il contenuto.

| Cartella | Description |
|---|---|
| [docs](https://github.com/MicrosoftDocs/sql-docs/tree/live/docs) | Contiene tutto il contenuto pubblicato su SQL Server. Le diverse aree del contenuto sono organizzate logicamente in sottocartelle. |
| [docs/includes](https://github.com/MicrosoftDocs/sql-docs/tree/live/docs/includes) | Contiene i file di inclusione. Questi file sono blocchi di contenuto che si possono includere in uno o più argomenti diversi. |
| **./media** | Ogni cartella può avere una sottocartella **media** per le immagini degli articoli. La cartella **media** a sua volta contiene sottocartelle con lo stesso nome degli argomenti in cui appare l'immagine. Le immagini devono essere file PNG con tutte le lettere minuscole e senza spazi. |
| **TOC.MD** | Un file di sommario. Ogni sottocartella può usare un file TOC.MD. |

#### <a name="applies-to-includes"></a>Inclusioni applies-to

Ogni articolo su SQL Server contiene un file di inclusione **applies-to** dopo il titolo. Indica a quali aree o versioni di SQL Server si riferisce l'articolo.

Si consideri l'esempio di Markdown seguente che esegue il pull nel file di inclusione **appliesto-ss-asdb-asdw-pdw-md.md**.

```Markdown
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
```

Questo comando aggiunge il testo seguente nella parte superiore dell'articolo:

![Testo applies-to](./media/sql-server-docs-contribute/applies-to.png)

Per trovare l'inclusione applies-to corretta per l'articolo, usare i suggerimenti seguenti:

- Consultare un altro articolo che analizza la stessa funzionalità o un'attività correlata. Se si modifica quell'articolo, è possibile copiare il Markdown per il collegamento al file di inclusione applies-to (è possibile annullare la modifica senza inviarla).
- Cercare nella directory [docs/includes](https://github.com/MicrosoftDocs/sql-docs/tree/live/docs/includes) i file che contengono il testo "applies-to". È possibile usare il pulsante **Find** in GitHub per filtrare rapidamente. Fare clic sul file per vedere come viene visualizzato.
- Prestare attenzione alla convenzione di denominazione. Se il nome contiene delle x, in genere sono segnaposto che indicano la mancanza di supporto per un servizio. Ad esempio, **appliesto-xx-xxxx-asdw-xxx-md.md** indica che esiste solo il supporto per Azure SQL Data Warehouse, poiché nel nome appare solo **asdw**, mentre gli altri campi contengono solo x.
- Alcune inclusioni specificano un numero di versione, ad esempio **tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md**. Usare questi file di inclusione solo quando si sa cha la funzionalità è stata introdotta con una versione specifica di SQL Server. 

## <a name="contributor-resources"></a>Risorse per i collaboratori

- [Guida per il collaboratore per docs.microsoft.com](https://docs.microsoft.com/en-us/contribute/)
- [Guida di stile Microsoft](https://docs.microsoft.com/en-us/teamblog/style-guide)
- [Informazioni di base su Markdown](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/)

> [!TIP]
> Per inviare commenti e suggerimenti relativi al prodotto anziché alla documentazione, [inserire qui eventuali suggerimenti per il prodotto SQL Server](https://feedback.azure.com/forums/908035-sql-server).

## <a name="next-steps"></a>Passaggi successivi

Esplorare il [repository sql-docs](https://github.com/MicrosoftDocs/sql-docs) su GitHub.

Trovare un articolo, inviare una modifica e collaborare con la community di SQL Server. 

Grazie.


