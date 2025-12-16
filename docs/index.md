## Chatmanagement

### Chat starten
1. **Neues Chatfenster** öffnen  
2. **Bestehende Datenbank** auswählen *oder* **neue Datenbank** anlegen  
3. **Chat starten**

### Woran sehe ich, welche Datenbank ich für einen vergangenen Chat verwendet habe?
In der linken Seitenleiste werden alle bisherigen Chatverläufe angezeigt. Die Chats sind nach der jeweils verwendeten Datenbank benannt.

### Wie kann ich einen Chat umbenennen?
1. In der linken Chatübersicht mit der Maus über den gewünschten Chat fahren  
2. Auf das **Stift-Symbol** klicken  
3. Neuen Namen eingeben

### Wie kann ich einen Chat löschen?
1. In der linken Chatübersicht mit der Maus über den zu löschenden Chat fahren  
2. Auf das **Mülleimer-Symbol** klicken  
3. Mit dem **Häkchen** bestätigen

### Wie kann ich alle Chats auf einmal löschen?
1. **Einstellungen** öffnen  
2. Unter **Chats verwalten**: **Alle Konversationen löschen** auswählen  
3. Löschen bestätigen

---

## Datenbankmanagement

### Neue Datenbank anlegen
1. **Neues Chatfenster** öffnen  
2. Unter **Neue Datenbank anlegen** den Namen der neuen Datenbank eingeben  
3. Auf **PDFs auswählen** klicken  
4. Gewünschte PDFs auswählen  

Nach der Auswahl werden die Namen der ausgewählten PDFs zur Überprüfung im Interface angezeigt.

### Was ist, wenn eine Datenbank versehentlich falsche PDFs enthält?
1. Falls falsche PDFs ausgewählt wurden, die Erstellung der Datenbank **zu Ende laufen lassen**  
2. Die neu erstellte Datenbank **löschen**  
3. Eine neue Datenbank mit den richtigen PDFs anlegen  

> **Hinweis:** Es kann vorkommen, dass der Name einer gelöschten Datenbank nicht sofort wieder verfügbar ist.

### Datenbank löschen
**Variante A**
1. **Neues Chatfenster** öffnen  
2. Die zu löschende Datenbank unter den bestehenden Datenbanken auswählen  
3. **Löschen** klicken  

**Variante B**
1. **Einstellungen** öffnen  
2. Datenbank auswählen  
3. **Datenbank löschen** klicken

### Warum kann ich nicht alle Datenbanken löschen?
Eine Datenbank (**Colitis Ulcerosa**) muss bestehen bleiben, da die Anwendung nicht ohne Datenbank verwendet werden kann.

### Kann ich noch Fragen in einem Chat stellen, wenn die Datenbank des Chats gelöscht wurde?
Nein. Der Chat wird deaktiviert, sobald die zugehörige Datenbank nicht mehr vorhanden ist.

---

## Systemmanagement

### Was passiert, wenn der PC neu gestartet wird?
Die Applikation startet automatisch. Falls es dabei Probleme gibt, kann sie manuell über die `docker-compose` Datei gestartet werden:
`mvz/MedDocGPT/rag_code/docker-compose`
