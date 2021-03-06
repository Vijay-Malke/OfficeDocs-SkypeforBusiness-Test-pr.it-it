﻿---
title: Abilitazione o disabilitazione dell'eliminazione dei dati archiviati
TOCTitle: Abilitazione o disabilitazione dell'eliminazione dei dati archiviati
ms:assetid: 28cef09f-0970-4fc3-8315-f26689e3e187
ms:mtpsurl: https://technet.microsoft.com/it-it/library/Gg520968(v=OCS.15)
ms:contentKeyID: 49299996
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Abilitazione o disabilitazione dell'eliminazione dei dati archiviati

 

_**Ultima modifica dell'argomento:** 2013-02-23_

Nel Pannello di controllo di Lync Server 2013 le configurazioni di archiviazione vengono usate per abilitare e disabilitare l'eliminazione e per configurare la modalità di implementazione dell'eliminazione. Le configurazioni di archiviazione interessate includono:

  - Una configurazione globale creata per impostazione predefinita quando si distribuisce Lync Server 2013.

  - Configurazioni facoltative a livello di sito e di pool che è possibile creare e usare per specificare la modalità di implementazione dell'archiviazione per siti o pool specifici.

Le configurazioni di archiviazione vengono impostate inizialmente quando si distribuisce Archiviazione, ma è possibile modificarle, aggiungerle ed eliminarle dopo la distribuzione. Per informazioni dettagliate sul modo in cui le configurazioni di archiviazione vengono implementate, nonché sulle opzioni che è possibile specificare e sulla gerarchia delle configurazioni di archiviazione, vedere [Funzionamento dell'archiviazione in Lync Server 2013](lync-server-2013-how-archiving-works.md) nella documentazione relativa alla pianificazione, alla distribuzione e alle operazioni.


> [!NOTE]
> Per usare l'archiviazione per gli utenti disponibili su Lync Server 2013, è necessario configurare i criteri di archiviazione per specificare se abilitare l'archiviazione per le comunicazioni interne, per le comunicazioni esterne o per entrambe. Per impostazione predefinita, l'archiviazione non è abilitata né per le comunicazioni interne né per quelle esterne. Prima di abilitare Archiviazione nei criteri, è necessario specificare le configurazioni di archiviazione appropriate per la distribuzione corrente e, facoltativamente, per siti e pool specifici, come descritto in questa sezione. Per informazioni dettagliate sull'abilitazione di Archiviazione, vedere <A href="lync-server-2013-configuring-and-assigning-archiving-policies.md">Configurazione e assegnazione dei criteri di archiviazione</A> nella documentazione relativa alla distribuzione.<BR>Se, dopo aver distribuito Archiviazione, si desidera usare l'integrazione di Microsoft Exchange per archiviare i dati e i file archiviati sui server Exchange 2013 e tutti gli utenti sono disponibili sui server Exchange 2013, è necessario rimuovere la configurazione del database SQL Server dalla topologia. Per farlo, usare il Generatore di topologie. Per informazioni dettagliate, vedere <A href="lync-server-2013-changing-archiving-database-options.md">Modifica delle opzioni del database di archiviazione in Lync Server 2013</A> nella documentazione relativa alle operazioni.



## Per abilitare o disabilitare l'eliminazione per l'archiviazione

1.  Da un account utente assegnato al ruolo CsArchivingAdministrator o CsAdministrator, accedere a qualsiasi computer nella distribuzione interna.

2.  Aprire una finestra del browser e quindi immettere l'URL di amministrazione per aprire il Pannello di controllo di Lync Server. Per informazioni dettagliate sui diversi metodi disponibili per avviare il Pannello di controllo di Lync Server, vedere [Aprire gli strumenti di amministrazione di Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Nella barra di navigazione di sinistra fare clic su **Monitoraggio e archiviazione**, quindi scegliere **Configurazione archiviazione**.

4.  Fare clic sul nome della configurazione globale, di sito o di pool appropriata nell'elenco delle configurazioni di archiviazione, scegliere **Modifica**, **Mostra dettagli** ed eseguire le operazioni seguenti:
    
      - Per abilitare l'eliminazione, selezionare la casella di controllo **Abilita eliminazione dei dati di archiviazione** ed eseguire una delle operazioni seguenti:
        
          - Per eliminare tutti i record, fare clic su **Elimina dati di archiviazione esportati e archiviati dopo durata massima (giorni)** e quindi specificare il numero di giorni.
        
          - Per eliminare solo i dati che sono stati esportati, fare clic su **Elimina solo i dati di archiviazione esportati**.
    
      - Per disabilitare l'eliminazione, deselezionare la casella di controllo **Abilita eliminazione dei dati di archiviazione**.

5.  Fare clic su **Commit**.

## Abilitazione e disabilitazione dell'eliminazione dei dati di archiviazione mediante i cmdlet di Lync Server Management Shell

L'abilitazione e la disabilitazione dell'eliminazione automatica dei dati di archiviazione possono essere gestite anche mediante Windows PowerShell e il cmdlet **Set-CsArchivingConfiguration**. Quest'ultimo può essere eseguito da Lync Server 2013 Management Shell o da una sessione remota di Windows PowerShell. Per informazioni dettagliate sull'utilizzo di Windows PowerShell remoto per la connessione a Lync Server, vedere l'articolo "Avvio rapido: gestione di Microsoft Lync Server 2010 con PowerShell remoto" nel blog su Windows PowerShell per Lync Server all'indirizzo [http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Abilitazione dell'eliminazione di tutti i dati di archiviazione

  - Per abilitare l'eliminazione di tutti i dati di archiviazione, impostare la proprietà **EnablePurging** su true ($True). Ad esempio:
    
        Set-CsArchivingConfiguration -Identity "site:Redmond" -EnablePurging $True
    
    In seguito all'esecuzione di questo comando, ogni giorno Lync Server eliminerà tutti i record di archiviazione precedenti al valore specificato per la proprietà **KeepArchivingDataForDays**.

## Abilitazione dell'eliminazione solo per i dati di archiviazione esportati

  - Per limitare l'eliminazione ai record di archiviazione che sono stati esportati in un file di dati (mediante il cmdlet [Export-CsArchivingData](https://docs.microsoft.com/en-us/powershell/module/skype/Export-CsArchivingData)), è anche necessario impostare la proprietà PurgeExportedArchivesOnly su True ($True). Ad esempio:
    
        Set-CsArchivingConfiguration -Identity "site:Redmond" -EnablePurging $True -PurgeExportedArchivesOnly $True
    
    In seguito all'esecuzione di questo comando, Lync Server eliminerà solo i record di archiviazione che soddisfano questi due criteri: 1) sono precedenti al valore specificato per la proprietà **KeepArchivingDataForDays** e 2) sono stati esportati usando il cmdlet **Export-CsArchivingData**.

## Disabilitazione dell'eliminazione dei dati di archiviazione

  - Per disabilitare l'eliminazione automatica dei record di archiviazione, impostare la proprietà **EnablePurging** su False ($False). Ad esempio:
    
        Set-CsArchivingConfiguration -Identity "site:Redmond" -EnablePurging $False

Per ulteriori informazioni, incluse opzioni aggiuntive per l'eliminazione dei dati di archiviazione, vedere l'argomento della Guida relativo al cmdlet [Set-CsArchivingConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsArchivingConfiguration).

## Vedere anche

#### Concetti

[Funzionamento dell'archiviazione in Lync Server 2013](lync-server-2013-how-archiving-works.md)  

#### Ulteriori risorse

[Configurazione e assegnazione dei criteri di archiviazione](lync-server-2013-configuring-and-assigning-archiving-policies.md)  
[Gestione delle opzioni di configurazione dell'archiviazione per l'organizzazione, i siti e i pool in Lync Server 2013](lync-server-2013-managing-archiving-configuration-options-for-your-organization-sites-and-pools.md)

