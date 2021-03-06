﻿---
title: 'Lync Server 2013: Creare o modificare un gruppo di agenti'
TOCTitle: Creare o modificare un gruppo di agenti
ms:assetid: f1461fff-51c1-4f4b-9311-8cba02c333fc
ms:mtpsurl: https://technet.microsoft.com/it-it/library/JJ205370(v=OCS.15)
ms:contentKeyID: 49302439
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Creare o modificare un gruppo di agenti in Lync Server 2013

 

_**Ultima modifica dell'argomento:** 2014-02-07_

Utilizzare una delle procedure seguenti per creare o modificare un gruppo di agenti.


> [!NOTE]
> Un amministratore, ad esempio CsVoiceAdministrator, deve abilitare gli utenti all'utilizzo del VoIP aziendale e di Lync Server prima che gli utenti possano essere assegnati ai gruppi di agenti. Se si è tra i delegati alla gestione di un Response Group per un flusso di lavoro gestito, è possibile creare gruppi di agenti da utilizzare nei flussi di lavoro da gestire.



<table>
<thead>
<tr class="header">
<th><img src="images/Gg412908.important(OCS.15).gif" title="important" alt="important" />Importante:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Quando si assegnano utenti come agenti dei Response Group, informarli che, se la modalità Privacy è abilitata, devono cercare i contatti &quot;RGS Presence Watcher&quot; e aggiungerli all'elenco dei contatti. Gli agenti con la modalità Privacy abilitata ma senza &quot;RGS Presence Watcher&quot; nell'elenco dei contatti non possono infatti ricevere chiamate al Response Group. Questa operazione non riguarda gli agenti con la modalità Privacy disabilitata.</td>
</tr>
</tbody>
</table>


## Per utilizzare Pannello di controllo di Lync Server per creare o modificare un gruppo di agenti

1.  Accedere come membro del gruppo RTCUniversalServerAdmins oppure come membro di uno dei ruoli amministrativi predefiniti che supportano Response Group.
    

    > [!NOTE]
    > Se si è tra i delegati alla gestione di un Response Group per un flusso di lavoro gestito, è possibile creare gruppi da utilizzare nei flussi di lavoro da gestire.



2.  Aprire una finestra del browser e quindi immettere l'URL di amministrazione per aprire il Pannello di controllo di Lync Server. Per informazioni dettagliate sui diversi metodi disponibili per avviare il Pannello di controllo di Lync Server, vedere [Aprire gli strumenti di amministrazione di Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Sulla barra di navigazione sinistra fare clic su **Response Group** e quindi su **Gruppo** .

4.  Nella pagina **Gruppo** effettuare una delle operazioni seguenti:
    
      - Per creare un nuovo gruppo di agenti, fare clic su **Nuovo** . Nel campo di ricerca **Seleziona un servizio** digitare tutto o parte del nome del servizio **ApplicationServer** in cui si desidera aggiungere il gruppo. Nell'elenco di servizi visualizzato fare clic su quello desiderato e quindi premere **OK** .
    
      - Per modificare un gruppo di agenti esistente, digitare tutto o parte del nome del gruppo di agenti nel campo di ricerca. Nell'elenco dei risultati di ricerca fare clic sul gruppo desiderato, fare clic su **Modifica** e quindi su **Mostra dettagli** .

5.  Nel campo **Nome** digitare il nome da assegnare al gruppo di agenti.

6.  Nel campo **Descrizione** digitare una descrizione per il gruppo.

7.  Nel campo **Criteri di partecipazione** selezionare una delle opzioni indicate di seguito per impostare il comportamento di accesso per il gruppo:
    
      - Selezionare **Informale** per specificare che gli agenti inclusi nel gruppo non devono eseguire l'accesso o la disconnessione dal gruppo, in quanto l'accesso al gruppo viene eseguito automaticamente quando essi accedono a Lync Server 2013.
    
      - Selezionare **Formale** per specificare che gli agenti inclusi nel gruppo devono eseguire l'accesso e la disconnessione dal gruppo. Se si seleziona questa opzione, gli agenti scelgono una voce di menu di Lync per aprire Internet Explorer e visualizzare la console di una pagina Web per l'accesso e la disconnessione dal gruppo.

8.  In **Tempo per avviso (secondi)** specificare il numero di secondi per l'invio di uno squillo a un agente prima che la chiamata venga inoltrata al successivo agente disponibile (il valore predefinito è 20 secondi).
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg412908.important(OCS.15).gif" title="important" alt="important" />Importante:</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>L'impostazione del tempo per l'invio di un avviso all'agente non può essere superiore a 180 secondi. Se il tempo per l'invio di un avviso all'agente supera i 180 secondi, l'applicazione client respinge la chiamata perché il timer delle transazioni SIP avrà raggiunto il massimo tempo di attesa consentito.</td>
    </tr>
    </tbody>
    </table>


9.  In **Metodo di routing** selezionare il metodo per il routing delle chiamate agli agenti del gruppo, nel modo seguente:
    
      - Per inoltrare una nuova chiamata prima all'agente che è stato inattivo per l'intervallo di tempo più lungo (con una presenza maggiore dello stato **Disponibile** o **Inattivo** in Lync Server), fare clic su **Inattività più lunga** .
    
      - Per inoltrare una nuova chiamata a tutti gli agenti disponibili contemporaneamente, fare clic su **Parallelo** . La chiamata verrà inviata al primo agente che la accetta.
    
      - Per inoltrare una nuova chiamata a ogni agente a turno, fare clic su **Round robin** .
    
      - Per inoltrare sempre una nuova chiamata agli agenti in base all'ordine con cui sono elencati nell'elenco **Agente** , fare clic su **Seriale** .
    
      - Per inoltrare una nuova chiamata a tutti gli agenti che hanno eseguito l'accesso a Lync Server 2013 e all' applicazione Response Group contemporaneamente, indipendentemente dalla loro presenza corrente, fare clic su **Attendant** . Gli utenti di Lync 2010 Attendant configurati come agenti possono visualizzare tutte le chiamate in attesa e rispondere a tali chiamate in qualsiasi ordine. La chiamata viene inviata al primo agente che la accetta e da quel momento gli altri utenti di Lync 2010 Attendant non la visualizzeranno più.

10. In **Agenti** specificare in che modo si desidera creare l'elenco degli agenti:
    
      - Per utilizzare un elenco personalizzato di agenti, fare clic su **Definisci un gruppo di agenti personalizzato** ed eseguire una delle operazioni seguenti:
        
          - Per aggiungere un utente al gruppo di agenti, fare clic su **Seleziona** , nel campo di ricerca **Seleziona agenti** digitare tutto o parte del nome dell'utente desiderato e quindi fare clic su **Trova** . Nell'elenco di agenti risultante fare clic sull'utente e quindi su **OK** .
        
          - Per rimuovere un utente dal gruppo di agenti, nell'elenco di agenti fare clic sull'utente desiderato e quindi su **Rimuovi** .
        
          - Per modificare l'ordine in cui vengono inoltrate le chiamate agli agenti nei gruppi con il routing round robin o seriale, nell'elenco degli agenti fare clic su un utente e quindi sulla freccia verso l'alto o verso il basso.
    
      - Per utilizzare una lista di distribuzione di Microsoft Exchange Server come gruppo di agenti, fare clic su **Usa una lista di distribuzione di posta elettronica esistente** e quindi in **Indirizzo lista di distribuzione** digitare l'indirizzo di posta elettronica della lista di distribuzione, ad esempio NetworkSupport@contoso.com.
        
        Se si utilizza una lista di distribuzione di posta elettronica, verranno applicate le restrizioni seguenti:
        
          - Non è possibile selezionare più liste di distribuzione per il gruppo di agenti. Ogni gruppo supporta una sola lista di distribuzione.
        
          - Se la lista di distribuzione contiene una o più liste di distribuzione, i membri delle liste di distribuzione annidate non verranno aggiunti all'elenco di agenti.
        
          - Se è selezionato il routing seriale o round robin, il server inoltra una chiamata in arrivo all'agente appropriato in base al metodo di routing e all'ordine con cui sono elencati gli agenti nella lista di distribuzione.
        
          - Se la lista di distribuzione contiene degli utenti per cui Lync Server 2010 è abilitato ma VoIP aziendale non è abilitato, tali utenti verranno aggiunti al gruppo di agenti come agenti non funzionali. Assicurarsi che VoIP aziendale sia abilitato per gli account utente di tutti i membri della lista di distribuzione.
        
        <table>
        <thead>
        <tr class="header">
        <th><img src="images/Gg412908.important(OCS.15).gif" title="important" alt="important" />Importante:</th>
        </tr>
        </thead>
        <tbody>
        <tr class="odd">
        <td>Se si utilizza una lista di distribuzione di posta elettronica, le appartenenze nascoste o gli elenchi nascosti potrebbero diventare visibili per l'amministratore o gli utenti di Response Group.</td>
        </tr>
        </tbody>
        </table>
        
        Per rendere visibili le appartenenze nascoste o gli elenchi nascosti, procedere nel modo seguente:
        
          - Se una lista di distribuzione è stata configurata in modo che l'appartenenza sia nascosta e che l'amministratore di Response Group assegni la lista di distribuzione all'elenco di agenti, gli utenti possono chiamare il gruppo per scoprirne i membri.
        
          - Se una lista di distribuzione è stata configurata in modo da essere nascosta nell'elenco di indirizzi globale di Exchange, l'amministratore di Response Group potrebbe essere in grado di visualizzare la lista di distribuzione e assegnarla all'elenco di agenti se il processo di Response Group dispone dei diritti e delle autorizzazioni utente appropriate, anche se l'amministratore non dispone di tali diritti e autorizzazioni.

11. Fare clic su **Commit** .

## Per utilizzare Windows PowerShell per creare o modificare un gruppo di agenti

1.  Accedere come membro del gruppo RTCUniversalServerAdmins oppure come membro di uno dei ruoli amministrativi predefiniti che supportano Response Group.

2.  Avviare Lync Server Management Shell: fare clic sul pulsante **Start**, scegliere **Tutti i programmi**, **Microsoft Lync Server 2013** e quindi **Lync Server Management Shell**.

3.  Utilizzare **New-CsRgsAgentGroup** per creare un nuovo gruppo di agenti. Utilizzare **Set-CsRgsAgentGroup** per modificare un gruppo di agenti esistente. Nella riga di comando digitare il comando seguente:
    
        New-CsRgsAgentGroup -Name "<agent group name>" -Parent $serviceId [-Description "<agent group description>"] -[AgentAlertTime <# seconds until call is routed to next agent>] [-ParticipationPolicy <Formal | Informal>] [-RoutingMethod <method for routing calls>] [-AgentsByUri("<first agent's SIP address>","<second agent's SIP address>")];
    
    Ad esempio:
    
        New-CsRgsAgentGroup -Name "Help Desk" -Parent "service:ApplicationServer:atl-cs-001.contoso.com"  -Description "Contoso Help Desk" -AgentAlertTime 20 -ParticipationPolicy Formal -RoutingMethod RoundRobin -AgentsByUri("sip:mindy@contoso.com","sip:bob@contoso.com")
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg412908.important(OCS.15).gif" title="important" alt="important" />Importante:</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>L'impostazione del tempo per l'invio di un avviso all'agente non può essere superiore a 180 secondi. Se il tempo per l'invio di un avviso all'agente supera i 180 secondi, l'applicazione client respinge la chiamata perché il timer delle transazioni SIP avrà raggiunto il tempo massimo di attesa consentito.</td>
    </tr>
    </tbody>
    </table>


4.  Verificare che il gruppo di agenti sia stato creato. Eseguire:
    
        Get-CsRgsAgentGroup -Name "Help Desk"

## Vedere anche

#### Attività

[Eliminare un gruppo di agenti](lync-server-2013-delete-an-agent-group.md)  

#### Ulteriori risorse

[Gestione di gruppi di agenti per Response Group](lync-server-2013-managing-response-group-agent-groups.md)  
[Get-CsService](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsService)  
[New-CsRgsAgentGroup](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsRgsAgentGroup)  
[Set-CsRgsAgentGroup](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsRgsAgentGroup)  
[Get-CsRgsAgentGroup](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsRgsAgentGroup)

