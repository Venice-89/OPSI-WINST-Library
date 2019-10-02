# opsi-winst
You just have to build this Package on you OPSI-Server and deploy it to your clients.\\
Then all included Libraries will be available in your Script. \\
You find more Informations about OPSI-Libraries in the OPSI-Script Manual. \\

## Integrated Libraries: ##


## fhg_rebootcontrol ##
Wenn w�hrens eines scripts ein Neustart notwendig ist, das script danach aber "wissen" muss das der Rechner neugestartet wurde muss ein Flag in der 
Registry gestezt werden.
Diese Funktion übernimmt dies über einen Simplen Aufruf und erleichtert so die Lesbarkeit des OPSI-Scipts.

**Aufruf:**\
`rebootcontrol(<counter>,<mode>)`

**Counter:** \
    Kann die Zahl die als RebootCounter in die Registry eingetragen werden soll übernehmen oder den wert "auto" annehmen.\
    Nutzt man Auto, wird automatisch der aktuelle Wert aus der Registry gelesen (oder angelegt) und um 1 erhöht.\
    
    
**Modes:**\
Folgende Modi sind m��glich:\
    write => Schreibt den Wert aus "counter" in die Registry oder zählt hoch\
    read => Liest den aktuellen Wert aus der Registry aus und gibt den Wert zurück\
    delete => Löscht den registry Eintrag aus der Registry
    
    
## removeMSI ##
**Aufruf:**\
set $result$ = removeMSI("dummy")\
**NOTE:** $result$ must be from Type "StringList"

**config**\
Im %ScriptDir% muss eine Datei msi.conf liegen. Diese enthält das Mapping MSI:Description im folgenden Format:\
Beschreibung der Software:{meine-msi-id}\
Beispiel Paket: apple-itunes

**Retrurn StringList**\
You will get the following information back (in case of an error):

[0] = Description\
[1] = ExitCode\
[2] = Error Desciption (If known, otherwise UNKNOWN)\
-> isFatalError

In case of ExitCode 0, 1605, 1641 or 3010 you will only get the following Information back:

[0] = All Products uninstalled\
[1] = 0\
[2] = All Products uninstalled



